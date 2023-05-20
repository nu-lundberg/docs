---
layout: default
title: DI Azure Functions
description: förstå hur dependency injection fungerar i en azure function
parent: Koncept
nav_order: 2
---

# Dependency Injection Azure Functions

Azure Functions stödjer Dependency Injection (DI) genom integrering med .NET Core's inbyggda DI-funktioner. Det betyder att du kan använda DI för att hantera och injicera beroenden i dina Azure Functions. 

För att ge ett exempel, låt oss säga att du har en Azure Function som behöver interagera med en databas. Utan DI, skulle varje funktion behöva skapa sin egen anslutning till databasen, vilket kan bli rörigt och svårt att hantera. Men med DI, kan du konfigurera en databasanslutning en gång, och sedan injicera den i varje funktion som behöver den.

För att använda DI i Azure Functions, behöver du göra följande:

1. Installera nödvändiga paket - Du behöver `Microsoft.Azure.Functions.Extensions` och `Microsoft.NET.Sdk.Functions` paketen.

2. Skapa dina tjänster - Du skapar klasser för att utföra olika uppgifter (t.ex. interaktion med databasen).

3. Registrera dina tjänster - Du gör detta i en Startup-klass, där du berättar för .NET vilka tjänster du vill kunna injicera.

4. Injicera dina tjänster - Nu kan du lägga till parametrar till dina Functions, och .NET kommer att automatiskt ge dem de tjänster de behöver.

Ett enkelt exempel kan se ut så här:

```csharp
using Microsoft.Azure.Functions.Extensions.DependencyInjection;
using Microsoft.Extensions.DependencyInjection;
using System;

[assembly: FunctionsStartup(typeof(MyNamespace.Startup))]

namespace MyNamespace
{
    public class Startup : FunctionsStartup
    {
        public override void Configure(IFunctionsHostBuilder builder)
        {
            builder.Services.AddSingleton<IDatabaseService, DatabaseService>();
        }
    }
}

public interface IDatabaseService
{
    string GetData();
}

public class DatabaseService : IDatabaseService
{
    public string GetData()
    {
        return "Hello, World!";
    }
}

public class Function1
{
    private readonly IDatabaseService _dbService;

    public Function1(IDatabaseService dbService)
    {
        _dbService = dbService;
    }

    [FunctionName("Function1")]
    public string Run([HttpTrigger(AuthorizationLevel.Anonymous, "get", "post", Route = null)] HttpRequest req)
    {
        return _dbService.GetData();
    }
}
```

I detta exempel skapar vi en Startup-klass där vi registrerar våra tjänster. Vi skapar ett IDatabaseService-interface och en DatabaseService-klass som implementerar det. Vi registrerar sedan tjänsten med `builder.Services.AddSingleton<IDatabaseService, DatabaseService>();`

I vår Azure Function, injicerar vi sedan IDatabaseService och använder det för att hämta data. 

Fördelen med detta är att det gör vår kod mer modulär och testbar. Vi kan enkelt byta ut DatabaseService mot en mock-version när vi vill testa vår funktion, till exempel. Dessutom, om vi har många funktioner som alla behöver interagera med databasen, behöver vi bara konfigurera det en gång och sedan kan vi injicera det överallt där det behövs.
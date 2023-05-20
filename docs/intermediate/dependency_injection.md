---
layout: default
title: Dependency Injection
description: Förklaring på vad dependency injection är konceptuellt
parent: Koncept
nav_order: 1
---

# Dependency Injection

Dependency Injection (DI) är ett designmönster som används för att minska hård koppling mellan programvarukomponenter. Det gör systemet mer flexibelt, testbart och modulärt. 

För att förstå DI, låt oss tänka på en riktigt enkel situation - du bygger en bil. Din bil behöver ett motor för att fungera.

1. Utan Dependency Injection:

   Om du bygger en bil som alltid använder en specifik typ av motor, säg en dieselmotor, så har du "hårdkopplat" din bil till en specifik motor. Detta innebär att om du någonsin vill byta till en annan typ av motor (säg en elmotor), skulle du behöva ändra bilens konstruktion. Detta är inte flexibelt och gör det svårare att uppdatera din bil i framtiden. Detta är problemet som Dependency Injection försöker lösa.

2. Med Dependency Injection:

   Istället för att hårdkoppla din bil till en specifik motor, vad om du kunde bygga din bil så att motorn kunde bytas ut enkelt? Detta är grunden för Dependency Injection. I stället för att din bil skapar sin egen motor (en "beroende"), får den motorn "injicerad" i den. På det här sättet kan du enkelt byta motortyp utan att behöva ändra själva bilens konstruktion.

I kod skulle det se ut ungefär så här (i C#):

Utan DI:
```csharp
class Car
{
    private DieselEngine engine;
    
    public Car()
    {
        engine = new DieselEngine();
    }
}
```

Med DI:
```csharp
class Car
{
    private IEngine engine; // Notice that we're now using an interface
    
    public Car(IEngine engine) // The engine is now passed in ("injected") through the constructor
    {
        this.engine = engine;
    }
}
```

Nu, istället för att direkt skapa en DieselEngine inuti Car-klassen, tar Car emot någon klass som implementerar IEngine interfacet, vilket innebär att du kan skicka in vilken typ av motor du vill - DieselEngine, ElectricEngine, eller någon annan klass som implementerar IEngine. Detta gör din kod mycket mer flexibel och lätthanterlig.

Detta är en grundläggande förklaring av Dependency Injection. Det finns mer avancerade scenarier där man använder DI-ramverk (som Ninject, Unity eller ASP.NET Core's inbyggda DI system) för att hantera beroendena åt dig, men grunderna är detsamma.
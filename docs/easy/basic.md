---
layout: default
title: Introduktion till Mjukvaruutveckling
description: Baskunskaper i c#
parent: Grundläggande
---

#Starta här

**1. Variabler och datatyper:**

I C# (och de flesta andra språk) lagrar vi data i variabler. Varje variabel har en specifik datatyp, till exempel `int` för heltal, `double` för decimaltal, `char` för tecken och `string` för strängar av text.

```csharp
int myNumber = 5;          // En hel
double myDouble = 5.5;     // Ett decimaltal
char myChar = 'A';         // Ett tecken
string myString = "Hello"; // En textsträng
```

**2. Kontrollstrukturer:**

Kontrollstrukturer låter oss bestämma vilken kod som ska köras och när.

**If-Else:**

```csharp
if (myNumber > 0) {
    Console.WriteLine("Number is positive");
} else if (myNumber < 0) {
    Console.WriteLine("Number is negative");
} else {
    Console.WriteLine("Number is zero");
}
```

**Switch:**

```csharp
switch (myNumber) {
    case 1:
        Console.WriteLine("Number is one");
        break;
    case 2:
        Console.WriteLine("Number is two");
        break;
    default:
        Console.WriteLine("Number is not one or two");
        break;
}
```

**Loopar (for, while):**

```csharp
for (int i = 0; i < 10; i++) {
    Console.WriteLine(i);
}

int i = 0;
while (i < 10) {
    Console.WriteLine(i);
    i++;
}
```

**3. Funktioner och metoder:**

Funktioner är en grupp instruktioner som utför en specifik uppgift. I C#, kallas de ofta metoder.

```csharp
void SayHello() {
    Console.WriteLine("Hello, world!");
}

SayHello();  // Detta kommer att skriva ut "Hello, world!" till konsolen.
```

**4. Arrayer:**

En array är en samling av variabler av samma typ.

```csharp
int[] myArray = new int[5];  // Skapar en array med plats för fem heltal

myArray[0] = 1;  // Sätter det första elementet i arrayen till 1
myArray[1] = 2;  // Sätter det andra elementet i arrayen till 2
// Och så vidare...
```
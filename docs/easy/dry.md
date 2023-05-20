---
layout: default
title: Introduktion till DRY
description: Baskunskaper i c#
parent: Grundläggande
---
# DRY (Do Not Repeat Yourself)
## Introduktion till DRY

DRY, eller "Do Not Repeat Yourself", är en grundläggande princip inom programmering. Konceptet är enkelt - undvik att skriva samma kod flera gånger. Istället för att kopiera och klistra in samma kodblock var du än behöver samma funktionalitet, sträva efter att skapa en funktion eller metod som kan återanvändas flera gånger. 

Detta tillvägagångssätt gör din kod mer läsbar och lätt att underhålla. Dessutom minskar det risken för fel och inkonsekvenser i din kod.

## Användning av DRY-Principen

Tänk dig att du har skrivit samma kodbit på flera ställen i din kod och sedan upptäcker ett fel. Nu måste du hitta varje instans av den här koden och ändra den. Men om du hade en funktion som du återanvände, skulle du bara behöva göra ändringen på ett ställe.

Det är dock viktigt att notera att DRY-principen inte bör tolkas så strikt att varje upprepning av kod måste elimineras utan undantag. Ibland kan överanvändning av DRY skapa mer komplexa abstraktioner och faktiskt göra koden svårare att förstå. Kom ihåg att DRY är ett verktyg, inte en lag.

## Vikten av Läslig och Lättföljd Kod

När du skriver kod, skriver du den inte bara för datorn. Människor kommer också att läsa din kod - kanske du själv i framtiden, andra utvecklare i ditt team, och kanske till och med utvecklare som inte har börjat arbeta på projektet än. 

Om din kod är svår att läsa och följa kan det leda till misstag, missförstånd och generellt sett minskad produktivitet. Att skriva kod som är lätt att läsa handlar om mer än att bara undvika att kopiera och klistra in. Det handlar också om att:

- Använda tydliga och beskrivande namn på variabler och funktioner
- Strukturera din kod på ett logiskt och konsekvent sätt
- Använda kommentarer när det behövs för att förklara komplicerade bitar av kod.

## Slutsats

Både DRY-principen och strävan efter att skriva lättläst kod bidrar till att göra din kod mer underhållbar och ditt team mer produktivt. Det kan ta lite extra tid och tanke att följa dessa principer, men det lönar sig i det långa loppet.

# Felsökningsrapport

## Vad var felet?

Jag valde att undersöka felet med antal deltagare när man skapar
en bokning. För att testa detta startade jag programmet och valde
att skapa en ny bokning i menyn. Jag fyllde i uppgifterna och
skrev six..då kraschade applikationen. Jag förväntade mig att få ett
felmeddelande och kunna fortsätta använda programmet. Användaren
kan skriva fel men det ska inte göra att hela programmet stängs.

## Var fanns felet?

Felet fanns i BookingConsole.cs i metoden CreateBooking().
Där användes int.Parse för att omvandla det användaren skrev
till ett heltal.

Console.ReadLine() läser in text. Om användaren skriver "6"
kan int.Parse omvandla texten till talet 6. Men när jag skrev
"six" gick det inte. Då kastades ett FormatException som inte
hanterades och därför kraschade programmet.

Problemet var alltså att koden försökte omvandla inmatningen
utan att hantera att användaren kunde skriva något annat än
ett tal.

## Hur rättade jag felet?

Jag bytte ut int.Parse mot int.TryParse och använde en if sats.
TryParse försöker också omvandla text till ett heltal men
returnerar false om det inte går.

Jag använde ! framför TryParse. Det betyder att if satsen
körs när omvandlingen inte lyckas. Då visar Console.WriteLine
ett felmeddelande och return lämnar metoden. Efter det kommer
användaren tillbaka till menyn.

Om användaren skriver ett heltal sparas det i participants
genom out var participants. Talet används sedan i bokningen.
De andra kontrollerna till exempel rummets kapacitet, finns
fortfarande kvar.

## Hur kontrollerade jag ändringen?

Jag startade programmet igen och provade att skriva six
och fick ett felmeddelande och kom
tillbaka till menyn utan att programmet kraschar.


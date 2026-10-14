När jag försökte skapa en bokning kraschade applikationen om jag skrev
"six" som antal deltagare. Koden använde int.Parse som försökte
omvandla texten till ett heltal. Eftersom six inte kunde omvandlas
uppstod ett fel.

Jag ersatte int.Parse med int.TryParse och en if sats. TryParse
returnerar false om omvandlingen misslyckas. Då visar programmet ett
felmeddelande.

Efter ändringen provade jag att skriva six igen. Felmeddelandet
visade och applikationen fortsatte utan att krascha.

## Var felet fanns och förväntat beteende

Felet fanns i filen BookingConsole.cs  i metoden CreateBooking().
Raden med int.Parse läste användarens inmatning och försökte direkt
omvandla den till ett heltal. När jag skrev six kastades ett
FormatException.

Det förväntade beteendet var att programmet skulle visa ett 
felmeddelande och låta användaren försöka igen eller återgå till menyn.
Ingen bokning skulle skapas med ett ogiltigt deltagarantal. 
testade en giltig boking med fyra pers och de registerades utan problem


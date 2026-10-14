När jag försökte skapa en bokning kraschade applikationen om jag skrev
"six" som antal deltagare. Koden använde int.Parse, som försökte
omvandla texten till ett heltal. Eftersom "six" inte kunde omvandlas
uppstod ett undantag som inte hanterades.

Jag ersatte int.Parse med int.TryParse och en if sats. TryParse
returnerar false om omvandlingen misslyckas. Då visar programmet ett
felmeddelande med Console.WriteLine

Efter ändringen provade jag att skriva "six" igen. Felmeddelandet
visade och applikationen fortsatte utan att krascha.
# Förutsägelser (steg 8)

Skriv din gissning FÖRST. Skriv sedan raden i STEG 7 i `src/main.ts`, kör den och fyll i vad som hände. Skriv också vad TypeScript sa (ofta understryker den raden).

| Uttryck | Min gissning | Det som hände | Vad sa TypeScript? | Hade jag rätt? |
|---|---|---|---|---|
| `"5" + 3` | 53 | 53 | Inga klagomål | Yes! |
| `"5" - 3` | Kommer klaga på att vi vill subtrahera från en string? | 2 | Error: The left-hand side of an arithmetic operation must be of type 'any', 'number', 'bigint' or an enum type. | njaee... tänkte nog rätt när det kommer till typescript, men när det körs så är det i javascript och då får man lite andra resultat |
| `true + 1` | Nu måste det bli fel... addition mellan boolean och number borde ge ett error | 2 | Error: Operator '+' cannot be applied to types 'boolean' and 'number'. | Nej. Tänkte typescript igen... men när javascript körs så omvandlar den true till numeriska värdet 1, så får vi 1 + 1 = 2 |
| `0.1 + 0.2` | 0.3 | 0.30000000000000004 | Inga klagomål | Nej.|
| `"" === 0` | false? | false | Error: This comparison appears to be unintentional because the types 'string' and 'number' have no overlap. | Ja, äntligen!|
| `null == undefined` | False igen? Om inte javascript ser dessa som likgiltiga värden... | true | Inga klagomål | Nej |

## Min regel för det jag missade

Skriv en mening med egna ord för varje uttryck du hade fel på.

1. `"5" - 3`: Javascript har automatisk typkonvertering. Värden omvandlas ibland till lämpliga datatyper. Tänk på typkonvertering!

2. `true + 1`: Här omvandlas true (boolean) till 1 (number) så att den kan utföra beräkningen 1 + 1. Tänk på typkonvertering!

3. `0.1 + 0.2`: Decimaltal lagras i binärt format. Det kan ge små avrundningsfel när vi utför beräkningar.

4. `null == undefined`: Det är skillnad på == och ===. === jämför datatyp och värde utan att konvertera, men == tillåter typkonvertering. Enligt föreläsningen anser javascript `false`, `0`, `""`, `null`, `undefined` och `NaN` som falska värden. Allt annat är sant. Så i detta fall jämförs ett falskt värde med ett falskt värde och vi får då true.  
**Tillägg**: Jag hade inte helt rätt här... JavaScript har specialregler för `==` och enligt dessa gäller det att detta uttryck är `true`. Det har inget med `falsy` och `truthy` att göra. 

### Sammanfattat:
1. `==` och `===` är olika: `==` tillåter typkonvertering. `===` kräver samma datatyp och samma värde.
2. TypeScript och JavaScript är inte samma sak. TypeScript kan upptäcka fel som JavaScript inte nödvändigtvis hindrar vid körning. TypeScript kontrollerar koden **innan** den körs.
3. JavaScript har automatisk typkonvertering. JavaScript försöker ibland omvandla värden till lämpliga datatyper automatiskt!

## Tänk efter

Tre av raderna ger ett typfel i TypeScript, men JavaScript kör dem ändå. Vilka tre, och vad säger det om vad TypeScript kan och inte kan göra?

1. console.log("5" - 3);
2. console.log(true + 1);
3. console.log("" === 0);

### Vad säger det om TypeScript?
TypeScript hjälper oss att upptäcka fel och olämpliga kombinationer av datatyper **innan** programmet körs. Det är dock JavaScript som faktiskt kör koden, och kan automatiskt konvertera datatyper. Därför kan kod som TypeScript klagar på ändå ge ett resultat när den körs.
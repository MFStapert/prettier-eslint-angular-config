# ESLint

ESLint is de, de facto code formatter voor javascript projecten.
Waar het bij een formatter vrij duidelijk is wat het precies doet is dit bij een linter iets onduidelijker.
Een linter doet in feite statische code analyse en draait mee tijdens het ontwikkelen.
Er zit overlap tussen een linter en een formatter, ESLint kan ook bestanden formateren en omvat ook regels die meer te maken hebben met opmaak.

Voor ESLint zijn er weinig serieuze alternatieven, doorslaggevend voor mij is dat ESLint de enige ondersteunde linter is van het angular team.
Het is ook de enige linter die goed samenspeelt met NX, totdat het angular team naar een andere kijkt stel ik voor dat wij dat ook niet doen.
ESLint performance is wel extreem matig.

Meerwaarde van een linter is het eerder detecteren van fouten in je code en code afspraken afdwingen.
ESLint heeft een berg configuratie opties die, mits goed geconfigureerd, een hoop nakijkwerk kunnen schelen.

## Instalatie

Voor de setup in deze repo zijn de instructies in [deze repo](https://github.com/angular-eslint/angular-eslint) gevolgd waarna vervolgens alle eslint specifieke packages naar deze repo zijn verplaatst.
Packages specifiek voor angular builders zijn hierbuiten gelaten, dit resulteerde in de volgende packages:

- @angular-eslint/eslint-plugin
- @angular-eslint/eslint-plugin-template
- @angular-eslint/template-parser
- @typescript-eslint/eslint-plugin
- @typescript-eslint/parser
- eslint
- typescript

Met deze setup is het mogelijk om linting los van je apps in te richten, afhankelijk van hoe we onze repo's willen inrichten is dit wel of niet wenselijk.
Als we bijvoorbeeld kiezen voor een opzet met NX waar we alle dependencies willen centraliseren is dit een afrader.
Deze setup is alleen eenvoudiger met het los testen van de ESLint configuratie

## .eslintrc

Het enige bestand wat aangemaakt wordt bij instalatie, bevat alle config voor ESLint.
Enige aanpassingen hieraan zijn:

**ignorePatterns**

Toegevoegd, dit is projectspecifiek, goede inrichting hiervan is noodzakelijk want bijvoorbeeld je cache niet excluden resulteert in trage linting.

**extends:**

Zie [eslint-config-prettier](https://github.com/prettier/eslint-config-prettier) config die aangeraden wordt icm prettier om conflicten te voorkomen.

### Rules

**no-console**

Voorkomt dat je `console.log` in de app laat staan, voorkomt dat mensen per ongeluk debug statements laten staan, warnings en errors mogen wel.

**@angular-eslint/template/prefer-control-flow**

Voorkomt dat je per ongeluk oude syntax gebruikt

**@angular-eslint/template/prefer-ngsrc**

Dwingt gebruik van ngsrc af, dit voorkomt dat sommige mensen dit wel/niet gaan gebruiken.

**@angular-eslint/prefer-standalone**

Dwingt gebruik van standalone af, ik zie geen reden waarom we nog modules willen hebben in onze apps.
Mogelijke uitzondering hierop is misschien een UI library, dan kun je componenten groeperen in een module a la Material.

## Overwegingen

De ruleset die we tot onze beschiking hebben met deze plugins kun je hier vinden:

- [eslint default](https://eslint.org/docs/latest/rules/)
- [typescript plugin](https://typescript-eslint.io/rules)
- [angular plugin](https://github.com/angular-eslint/angular-eslint/tree/main/packages/eslint-plugin)
- [angular template plugin](https://github.com/angular-eslint/angular-eslint/tree/main/packages/eslint-plugin-template)

In totaal heb je een paar honderd regels tot je beschikking.
Mijn voorkeur heeft het om periodiek te kijken of er regels zijn die kunnen implementeren, ipv te voren alles dicht te timmeren.

Een paar regels die het overwegen waard zijn:

[@angular-eslint/prefer-on-push-component-change-detection](https://github.com/angular-eslint/angular-eslint/blob/main/packages/eslint-plugin/docs/rules/prefer-on-push-component-change-detection.md)

Dwingt af dat elk component ChangeDetectionStrategy.OnPush gebruikt, vraag is of we dit willen, maar als we dit willen is een makelijke toevoeging.

[@angular-eslint/use-lifecycle-interface](https://github.com/angular-eslint/angular-eslint/blob/main/packages/eslint-plugin/docs/rules/use-lifecycle-interface.md)

Dwingt af dat als je lifecycle methodes zoals OnInit gebruikt je ook de interface moet implementeren.
Je hoeft dit standaard niet te doen, dus je kan een interface weghalen en vergeten om de daadwerkelijke methode te verwijderen.

[i18n](https://github.com/angular-eslint/angular-eslint/blob/main/packages/eslint-plugin-template/docs/rules/i18n.md)

eslint kan ook i18n tags afdwingen mits geconfigureerd met angulars standaard i18n package.

[dot notation](https://typescript-eslint.io/rules/dot-notation/)

Voorkomt property access middels brackets `obj['prop']`, wat problemen kan opleveren met refactoring.

[explicit-member-accessibility](https://typescript-eslint.io/rules/explicit-member-accessibility/)

Dwingt gebruik van access modifiers af, als we dit consistent willen hebben kun je het niet vergeten met deze regel.

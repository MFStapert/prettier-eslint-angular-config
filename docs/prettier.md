# Prettier

Prettier is de, de facto code formatter voor javascript projecten.
Het is een tool die inmiddels al jaren meegaat en door het overgrote deel van de projecten gebruikt wordt (angular/react/svelte).
Prettier adverteert zichzelf als "opinionated" en biedt minimale configuratie opties aan, advies van prettier is om hier zo min mogelijk aan, aan te passen.
Sommige settings zoals een printWidth van 80 valt initieel slecht in de smaak bij ontwikkelaars maar biedt bijvoorbeeld een hoop voordeel bij multitab werken en nakijken.

Een andere formatter dan prettier gebruiken is een vrij exotische use case en is af te raden mits er een harde requirement aan zit.
Er is de laatste jaren wel wat beweging in de formatter space, vooral [biomejs](https://biomejs.dev/) lijkt een interessante ontwikkeling en belooft een hoop performance winst.
Echter is adoptie nog laag en performance van prettier "goed genoeg" in de meeste gevallen.

De reden dat je een code formatter wilt is zodat je een consistente stijl in je code base kan hanteren.
Door je bestanden standaard te formatten voor je commit garandeer je dat alle code die ingechekt wordt aan een standaard format voldoet.
Een check aan de CI kant garandeert dat er niet per ongeluk code wordt ingecheckt die niet geformat is (een amend slaat bijvoorbeeld pre-commit hooks over).
De grootste winst van een formatter is dat het veel discussie scheelt in MRs, het maakt het schrijven van code ook eenvoudiger omdat je nauwelijks meer bezig hoeft te zijn met formattering.

## Bestanden

### .editorconfig

Een `.editorconfig` op root niveau dwingt wat formatting af in je editor, maar je moet hier niet op leunen voor formatting.

Je wilt zo min mogelijk specifieke settings hierin en alle JS formatting aan prettier overlaten.

`insert_final_newline` en `charset` worden niet door prettier afgedwongen.

### .prettierignore

Ignore file, ondersteunt ook file extensies dus je kan b.v. je C# code negeren.

Je kan ook paden opgeven dus je kan b.v. een backend folder negeren

### .prettierrc

`"singleQuote": true,`

Single quotes `'` ipv `"`, resulteert in kortere regels

`"arrowParens": "avoid",`

Ik vindt niet dat je `(x) => {}` moet doen `ipv x => {}`

`"singleAttributePerLine": true`

Meest leesbare optie voor angular imo; zorgt dat elk attribuut op een losse regel komt te staan.

`"bracketSameLine": true,`
`"htmlWhitespaceSensitivity": "ignore",`

De combinatie van deze 2 properties zorgt dat je geen `>` op een newline krijgt.
Zie deze [post](https://trungvose.com/experience/prettier-prevent-html-closing-tag-new-line/)

## Scripts

`"format:prettier": "prettier . --write"`

Format alles, .prettierignore zou alles moeten afvangen wat niet geformat mag worden

`"check:prettier": "prettier . --check"`

Check alles, dit gebruik je in CI.

Interesante CLI flags:

`--cache`
`--log-level`

## Plugins

### [prettier-plugin-organize-imports](https://www.npmjs.com/package/prettier-plugin-organize-imports)

Sorteert imports en verwijderd ongebruikte imports, dit is een must IMO aangezien elke editor dit anders doet.

### [prettier-plugin-css-order](https://www.npmjs.com/package/prettier-plugin-css-order)

Sorteert CSS properties, optioneel.

### [prettier-plugin-organize-attributes](https://www.npmjs.com/package/prettier-plugin-organize-attributes)

Sorteert HTML attributen, optioneel.

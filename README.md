# Prettier-angular-config

Demo project for prettier config

Vraag is of we dit op root level willen

Zou fijn zijn voor configuratie en onderhoud

## Setup

`npm ci`
`npx husky init`

## Reasoning behind files

### .editorconfig

Wil je op zelfde niveau hebben omdat dit implicaties heeft voor prettier

Zo min mogelijk specifieke settings hierin en alle JS formatting aan prettier overlaten

### .prettierignore

Ignore file, ondersteund ook file extensies dus je kan b.v. je C# code negeren.

### .prettierrc

`"printWidth": 80,`

Default van prettier, vrij smal maar maakt nakijken en werken met meerdere tabs erg fijn.

`"tabWidth": 2,`

Nodig met width 80

`"useTabs": false,`

Nodig met width 80

`"semi": true,`

`;` op het einde van elke line

`"singleQuote": true,`

Enkele comma

`"quoteProps": "consistent",`

Mijn voorkeur om dit consistent te houden

`"trailingComma": "none",`

Mijn voorkeur om dit niet te doen

`"bracketSpacing": true,`

Default van prettier

`"bracketSameLine": true,`

Vermijd dat `<`op een newline komt

`"arrowParens": "avoid"`

`"singleAttributePerLine": true`

Mijn voorkeur

## Scripts

`"format:prettier": "prettier . --write"`

Format alles, .prettierignore zou alles moeten afvangen wat niet geformat mag worden

Vermijd npx met het aanroepen van workspace script.
Je kan hiermee een versie van een package aanroepen die anders is dan in je package.json file

`"check:prettier": "prettier . --check"`

Check alles, dit gebruik je in CI

Interesante CLI flags:

`--cache`
`--log-level`

## Packages

### husky + lint-staged

Wordt aangeraden voor precommit, er zijn andere opties

Git hooks kun je alleen opslaan in root niveau
Dus als je geen package.json op root wilt hebben moet je een niet JS optie kiezen

## Plugins

### eslint-config-prettier

Wordt aangeraden als je eslint gebruikt

### prettier-plugin-organize-imports

Goeie QoL plugin, zorgt dat

# Prettier-angular-config

Demo project for prettier + eslint config

Je moet git hooks op root level inrichten, in dit project is dit gedaan met husky, maar er zijn alternatieven.

Alternatieven die door prettier aangeraden worden:

- https://pre-commit.com/ (python)
- https://alirezanet.github.io/Husky.Net/ (dotnet)

## Setup

`npm ci`
`npx husky init`

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

## Packages

### husky + lint-staged

Wordt aangeraden voor precommit, er zijn andere opties

Git hooks kun je alleen opslaan in root niveau
Dus als je geen package.json op root wilt hebben moet je een niet JS optie kiezen

## Plugins

### [prettier-plugin-organize-imports](https://www.npmjs.com/package/prettier-plugin-organize-imports)

Sorteert imports en verwijderd ongebruikte imports, dit is een must IMO aangezien elke editor dit anders doet.

### [prettier-plugin-css-order](https://www.npmjs.com/package/prettier-plugin-css-order)

Sorteert CSS properties, optioneel.

### [prettier-plugin-organize-attributes](https://www.npmjs.com/package/prettier-plugin-organize-attributes)

Sorteert HTML attributen, optioneel.

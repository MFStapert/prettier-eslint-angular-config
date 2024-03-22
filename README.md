# Prettier-angular-config

Demo project to prettier configs

## Setup

`npm ci`
`npx husky init`

## Reasoning behind files

### .prettierignore

## Scripts

`"format:prettier": "prettier . --write"`

Avoid npx

Call prettier
`.` should target all ts/js
--write
--check for in CI
--cache is interesting
--log-level in CI?

use

## Packages

### eslint-config-prettier

Wordt aangeraden als je eslint gebruikt

### husky + lint-staged

Wordt aangeraden voor precommit

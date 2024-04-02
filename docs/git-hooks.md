# Git hooks

Je moet git hooks op root level inrichten, in dit project is dit gedaan met husky, maar er zijn alternatieven.

Alternatieven die door prettier aangeraden worden:

- https://pre-commit.com/ (python)
- https://alirezanet.github.io/Husky.Net/ (dotnet)

## lint-staged

Wordt aangeraden door prettier voor het alleen checken van bewerkte bestanden.
Met een andere tool voor pre-commit is deze tool mogelijk niet nodig.

## Gebruik

Met git hooks wil je niet dat er checks gedaan worden omdat dit ontwikkelaars hun proces kan blokeren.
Je kan bijvoorbeeld pas formatting willen draaien het moment dat je, je feature afhebt i.p.v. alle commits.
Ook tests draaien raadt ik af in pre-commit aangezien dit je proces erg traag maakt.
CI zou de omgeving moeten zijn waar daadwerkelijke checks gedaan worden.

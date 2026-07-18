# Deploy — manual

Este projeto ainda não tem pipeline de deploy automatizado. Documente
aqui, à mão, como o deploy é feito hoje (host, comando, quem faz) assim
que isso for definido.

## Fluxo de branch (mesmo dos outros modelos)

`feature/* → PR → develop → promoção → test → PR revisado → main`. A
promoção entre ambientes e o deploy em si são manuais até um modelo ser
escolhido.

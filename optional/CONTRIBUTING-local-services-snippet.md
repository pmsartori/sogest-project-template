
## Ambiente local

Este projeto usa Docker Compose para serviços locais (banco de dados).

```bash
docker compose up -d      # sobe o Postgres local
docker compose down       # derruba
docker compose down -v    # derruba e apaga os dados (reset completo)
```

Credenciais padrão (ambiente local, não são segredo): usuário `dev`, senha
`localdev`, banco `[SLUG_PROJETO]`, porta `5432`. Ajuste `docker-compose.yml`
se precisar de outro serviço (Redis, etc.) — há um comentário indicando
onde adicionar.

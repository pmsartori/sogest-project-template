# Deploy — SSH em servidor próprio

Pipeline de 3 ambientes, um host, um cluster Postgres (ou banco
equivalente), três bases:

```
feature/* ──PR──▶ develop ──promoção──▶ test ──gate (humano)──▶ main
                    DEV               TEST                     PROD
             deploy auto no push  deploy auto no push    disparo manual apenas
```

- **Edite `develop` apenas.** `test`/`main` são alvos de promoção.
- `develop → test`: fast-forward automático (workflow
  `deploy-test.yml`).
- `test → main`: exige PR revisado. Deploy de prod é **sempre disparo
  manual humano** (`gh workflow run "Deploy · prod" --ref main`).
- Configure os secrets do repositório antes do primeiro deploy:
  `SSH_HOST`, `SSH_USER`, `SSH_KEY`, `DEPLOY_PATH` — **este passo é
  manual**, o instalador não gera nem injeta credenciais.

| Env | Branch | Deploy |
|---|---|---|
| dev | `develop` | automático no push |
| test | `test` | automático na promoção |
| **prod** | `main` | **manual apenas** |

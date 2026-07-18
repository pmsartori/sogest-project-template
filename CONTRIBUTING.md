# Contribuindo & Fluxo de trabalho

Como trabalhamos no [PROJETO].

## Acesso

- **Código:** GitHub `pmsartori/[SLUG_PROJETO]` (privado ou público, ver
  README). Peça convite de colaborador ao dono do repositório.
- **Segredos:** nunca commitar credenciais reais. `.env*` é gitignored.

## Branching & pull requests

Trunk-based, branches curtas:

```
main            sempre deployável; protegida (PR + CI verde + 1 review)
develop         você trabalha aqui
feature/<nome>  sua branch de trabalho, a partir de develop
```

1. `git switch -c feature/descricao-curta`
2. Commits pequenos e focados. Escreva teste para todo comportamento
   novo/alterado.
3. Abra PR contra `develop`. CI precisa passar e 1 revisor aprovar.
4. Squash-merge pra `develop`. **Você só edita `develop`** — `test` e
   `main` são alvos de promoção, nunca push direto.

## Rastreamento de trabalho

- Trabalho é rastreado como **GitHub Issues**, organizado no **Project
  board** (Triage → Backlog → Ready → In Progress → In Review → Done).
- Pegue uma issue, self-assign, mova pra *In Progress*, referencie no PR
  (`Closes #NN`).

### Reivindicando trabalho — pra não pisar no pé de ninguém

1. **Self-assign** — `gh issue edit <n> --add-assignee @me`.
2. **Label `status:in-progress`** — `gh issue edit <n> --add-label status:in-progress`.
3. **Abra um PR _rascunho_ imediatamente**, antes do código existir —
   `gh pr create --draft --fill --base develop`.

**Ver quem trabalha em quê:** `gh issue list --label status:in-progress`
ou `gh issue list --assignee @me`.

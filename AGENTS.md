# [PROJETO] — regras do projeto (leia primeiro)

[DESCRICAO_UMA_LINHA]

Este arquivo é a memória de projeto que todo desenvolvedor e assistente de
IA deve ler antes de trabalhar aqui. Docs completos: [`README.md`](README.md),
[`CONTRIBUTING.md`](CONTRIBUTING.md).

## Rastreamento do projeto

Trabalho é organizado em **módulos** (`area:` labels) → **epics** (issues +
sub-issues) → **sprints** (milestones), num **board**
(Triage→Backlog→Ready→In Progress→In Review→Done). Guia completo:
[`docs/PROJECT.md`](docs/PROJECT.md).

- **Visão geral do projeto:** rode [`scripts/overview.sh`](scripts/overview.sh)
  (sprint atual, progresso dos epics, trabalho por módulo, inbox de triagem).
- **Minhas tarefas:** `gh issue list --assignee @me`. **Um módulo:**
  `gh issue list --label area:<modulo>`. **Esta sprint:**
  `gh issue list --milestone "Sprint N"`.
- **Pegar um ticket:** self-assign + label `status:in-progress` + PR
  rascunho (`Closes #n`) antes de codar. **Sugerir:** issue nova →
  template 💡 Sugestão (cai em Triage).

## Módulos deste projeto

[LISTA_MODULOS_COM_EPICS]

## Regras de ouro

1. **Edite `develop` apenas.** Branch a partir dele, PR de volta pra ele.
   `test` e `main` são alvos de promoção — nunca push direto.
2. **Produção é liberada explicitamente por um humano.** Nunca faça deploy
   automático pra prod nem por iniciativa própria.
3. **TypeScript/linguagem principal em modo estrito.** Arquivos focados.
4. Consulte [`docs/adr/`](docs/adr/README.md) antes de mudar um padrão já
   assentado — e adicione um ADR quando tomar uma decisão que um engenheiro
   futuro possa questionar ou desfazer.

## Ambientes

[TABELA_AMBIENTES]

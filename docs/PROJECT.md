# Como rodamos o projeto (módulos · epics · sprints · board)

Guia único de como o trabalho é organizado e rastreado em [PROJETO]. Humanos
e assistentes de IA devem ler isto para responder "qual o estado do
projeto?" e "como eu pego / sugiro / rastreio trabalho?".

## Ver a visão geral — duas formas

- **Peça ao seu assistente:** *"me dá a visão geral do projeto"* → ele roda
  [`scripts/overview.sh`](../scripts/overview.sh) e imprime a sprint atual,
  progresso dos epics, trabalho por módulo, e o inbox de triagem.
- **Web:**
  - **Board (visual):** https://github.com/users/pmsartori/projects/N
  - **Sprints (milestones):** https://github.com/pmsartori/[SLUG_PROJETO]/milestones
  - **Todas as issues:** https://github.com/pmsartori/[SLUG_PROJETO]/issues

## A estrutura

Quatro níveis, do mais amplo ao mais granular: **Módulo → Epic → Task →
Sub-task**.

```
Módulo (label area:)
 └─ Epic          issue, label `epic`, um por módulo
     └─ Task      sub-issue do epic — unidade que alguém pega para trabalhar
         └─ Sub-task   sub-issue da task — só quando uma task precisa ser dividida
```

Módulos deste projeto e seu epic — **um epic por módulo, sempre**:

[TABELA_MODULOS_EPICS]

| Conceito | Primitivo do GitHub | Como usar |
|---|---|---|
| **Módulo** | label `area:` | Toda issue recebe uma — ver tabela acima. |
| **Epic** | issue com label `epic` + **sub-issues** | Filhos formam a barra de progresso. Antes de criar um epic novo, cheque esta tabela primeiro. |
| **Task** | **sub-issue de um epic** | A unidade normal de trabalho. |
| **Sub-task** | **sub-issue de uma task** | Só quando a task precisa de checklist próprio. |
| **Sprint** | **Milestone** com data | Ex.: "Sprint 1". |
| **Status/dono** | **Project board** + **assignee** | Triage → Backlog → Ready → In Progress → In Review → Done. |

## Comandos do dia a dia

```bash
scripts/overview.sh                       # visão geral completa
gh issue list --milestone "Sprint 1"       # esta sprint + donos
gh issue list --assignee @me               # minhas tarefas
gh issue list --label area:<modulo>        # um módulo
gh issue list --label needs-triage         # inbox de sugestões
gh issue list --label status:in-progress   # o que está sendo feito agora
```

## Os fluxos

**Pegar trabalho:**
1. `gh issue edit <n> --add-assignee @me --add-label status:in-progress`
2. Branch `feat/<n>-slug`, abra PR **rascunho imediatamente** (`Closes #<n>`).
3. Mova o card pra **In Progress**.

**Sugerir uma feature:** issue nova → *💡 Sugestão de feature* (ou
`gh issue create --label needs-triage,suggestion`). Cai em **Triage**.

**Nova task ou sub-task:**
```bash
gh issue create --title "…" --label area:<modulo>
gh api repos/pmsartori/[SLUG_PROJETO]/issues/<pai>/sub_issues -F sub_issue_id=$(gh api repos/pmsartori/[SLUG_PROJETO]/issues/<nova> --jq '.id')
```

**Novo epic** — só se um módulo genuinamente ainda não tem um:
```bash
gh issue create --title "[EPIC] …" --label epic,area:<modulo>
```

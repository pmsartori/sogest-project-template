# Como construímos (o método)

O loop usado para todo trabalho não-trivial neste projeto.

```
  ideia ─▶ brainstorm ─▶ spec ─▶ plan ─▶ code+test ─▶ review/refine ─▶ merge
          (design)     (doc)   (tasks)  (subagents)   (olhos frescos)
```

| Estágio | Skill | Saída | Gate antes de avançar |
|---|---|---|---|
| **1. Brainstorm** | `superpowers:brainstorming` | Entendimento compartilhado + 2-3 abordagens com recomendação | Design apresentado e **aprovado pelo humano** |
| **2. Spec** | (brainstorming escreve) | `docs/superpowers/specs/YYYY-MM-DD-<topico>-design.md`, commitado | Humano revisou a spec escrita |
| **3. Plan** | `superpowers:writing-plans` | `docs/superpowers/plans/YYYY-MM-DD-<feature>.md` — tasks TDD pequenas | Auto-revisão do plano passa |
| **4. Code + test** | `superpowers:subagent-driven-development` | Commits, cada task test-first, revisada entre tasks | Todas as tasks verdes + reviews limpas |
| **5. Refine** | review da branch inteira | Correções do que a review encontrou | Review recomenda merge |

## Por que essa ordem

- Design antes de código evita o retrabalho mais caro (construir a coisa
  errada).
- Spec + plan escritos dão contexto completo a um agente ou dev novo, sem
  deriva — o mesmo motivo de manter [ADRs](adr/README.md) e o
  [glossário](glossary.md).

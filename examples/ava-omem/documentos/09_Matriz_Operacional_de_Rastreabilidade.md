---
document_id: DOC-09
title: Matriz Operacional de Rastreabilidade
status: canonical-example
version: 1.2.0
depends_on:
  - DOC-08
---

# 09 — Matriz Operacional de Rastreabilidade

> **Estado inicial:** nenhum código do produto foi implementado.  
> **Regra:** a matriz não inventa implementação, teste ou evidência.

Abreviações de origem usadas neste exemplo:

```text
D06   → Técnicas de Desenvolvimento
D07   → Engenharia e Arquitetura
TL    → Visão do Tech Lead
Infra → Infraestrutura e Plano de Fundação
```

| ID | Origem | Requisito | Implementação | Testes | Evidência | Status |
| --- | --- | --- | --- | --- | --- | --- |
| FND-001 | D07 | Estrutura arquitetural do monorepo | — | — | — | Planned |
| FND-002 | D06, TL | Stack, workspace e toolchain | — | — | — | Planned |
| FND-003 | D06, TL | Quality gates locais | — | — | — | Planned |
| FND-004 | D06, TL, Infra | Configurar CI | — | — | — | Planned |
| FND-005 | D07, TL, Infra | Banco/Auth staging | — | — | — | Planned |
| FND-006 | D06, D07, TL, Infra | Migrations e tenant baseline | — | — | — | Planned |
| FND-007 | TL, Infra | Web staging | — | — | — | Planned |
| FND-008 | D07, TL, Infra | API staging | — | — | — | Planned |
| FND-009 | D07, TL, Infra | E-mail transacional | — | — | — | Planned |
| FND-010 | D06, D07, TL, Infra | Smoke da Fundação | — | — | — | Planned |
| AUTH-001 | D02, D05 | Primeiro acesso por convite | — | — | — | Planned |
| TEN-001 | D02, D05 | Criar empresa | — | — | — | Planned |
| TEN-002 | D02, D03 | Módulos OMEM contratados | — | — | — | Planned |
| TEN-003 | D02, D05, D07 | Gestor restrito ao próprio tenant | — | — | — | Planned |
| CNT-001 | D02, D04 | Curso reutilizável | — | — | — | Planned |
| CNT-002 | D02, D04 | Módulos e aulas | — | — | — | Planned |
| CNT-003 | D02, D04 | Materiais | — | — | — | Planned |
| TRL-001 | D02, D03 | Criar trilha | — | — | — | Planned |
| TRL-002 | D02, D03, D05 | Sugerir trilha contextual | — | — | — | Planned |
| CLS-001 | D02, D05 | Criar turma | — | — | — | Planned |
| CLS-002 | D02, D05 | Matrícula + trilha | — | — | — | Planned |
| LRN-001 | Princípios, D04, D05 | Minha trilha | — | — | — | Planned |
| LRN-002 | D05, D07 | Concluir aula | — | — | — | Planned |
| ASM-001 | D02, D05 | Quiz | — | — | — | Planned |
| ASM-002 | D02, D05 | Tarefa prática | — | — | — | Planned |
| ASM-003 | D02, D05 | Validação manual | — | — | — | Planned |
| OBS-001 | D03, D05 | Acompanhamento da consultoria | — | — | — | Planned |
| OBS-002 | D02, D05 | Acompanhamento do gestor | — | — | — | Planned |
| CERT-001 | D02, D05 | Certificado | — | — | — | Planned |

## Como a matriz evolui

Exemplo depois da execução de `FND-001`:

```text
ID: FND-001
Implementation:
- apps/web/
- apps/api/
- packages/domain/
- packages/contracts/
- infra/
- tooling/

Tests/checks:
- repository tree review
- architecture conformance review

Evidence:
- commit <sha>
- diff <ref>

Status:
Validated
```

`pnpm-workspace.yaml`, Node, TypeScript, React/Vite e Fastify ainda não aparecem como evidência de `FND-001`; eles pertencem a `FND-002`, cuja origem inclui a Visão do Tech Lead.

Somente após todos os gates definidos para o item e a evidência necessária é que o status pode avançar para `Done`.

## Regras de consistência

- `Done` sem teste/evidência aplicável é divergência;
- código existente com matriz `Planned` precisa de reconciliação;
- stack instalada diferente da Visão do Tech Lead é divergência;
- provider implantado diferente da Infraestrutura aprovada é divergência;
- mudança de requisito deve atualizar backlog e matriz;
- evidência aponta para execução real, não para promessa;
- implementação não pode ser usada para reescrever silenciosamente a intenção original.
---
document_id: DOC-09
title: Matriz Operacional de Rastreabilidade
status: canonical-example
version: 1.0.0
depends_on:
  - DOC-08
---

# 09 — Matriz Operacional de Rastreabilidade

> **Estado inicial:** nenhum código do produto foi implementado.  
> **Regra:** a matriz não inventa implementação, teste ou evidência.

| ID | Origem | Requisito | Implementação | Testes | Evidência | Status |
| --- | --- | --- | --- | --- | --- | --- |
| FND-001 | D06, D07 | Inicializar monorepo | — | — | — | Planned |
| FND-002 | D06 | Fixar toolchain | — | — | — | Planned |
| FND-003 | D06 | Quality gates locais | — | — | — | Planned |
| FND-004 | D06, Infra | Configurar CI | — | — | — | Planned |
| FND-005 | Infra | Banco/Auth staging | — | — | — | Planned |
| FND-006 | D07, Infra | Migrations e tenant baseline | — | — | — | Planned |
| FND-007 | Infra | Web staging | — | — | — | Planned |
| FND-008 | Infra | API staging | — | — | — | Planned |
| FND-009 | Infra | E-mail transacional | — | — | — | Planned |
| FND-010 | D06, D07, Infra | Smoke da Fundação | — | — | — | Planned |
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

Exemplo depois da execução de uma fatia:

```text
ID: FND-001
Implementação:
- pnpm-workspace.yaml
- apps/web
- apps/api
- packages/domain
- packages/contracts

Testes:
- workspace install
- build smoke
- boundary check

Evidência:
- CI <run>
- commit <sha>

Status:
Validated
```

Somente após todos os gates definidos para o item e a evidência necessária é que o status pode avançar para `Done`.

## Regras de consistência

- `Done` sem teste/evidência aplicável é divergência;
- código existente com matriz `Planned` precisa de reconciliação;
- mudança de requisito deve atualizar backlog e matriz;
- evidência aponta para execução real, não para promessa;
- implementação não pode ser usada para reescrever silenciosamente a intenção original.
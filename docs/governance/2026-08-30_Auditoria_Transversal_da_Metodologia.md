# Auditoria Transversal da Metodologia

**Data:** 30 de agosto de 2026  
**Branch auditada:** `refactor/processo-v2-discovery`  
**Baseline inicial da auditoria:** `c4bf6db43ada7ad2d192afe1c6d9f166875e7be6`  
**Escopo:** README, documentos operacionais 00–12, documentos intermediários de Princípios UX/UI e Visão do Tech Lead, estrutura de exemplos e handoff para Codex.

## 1. Objetivo

Esta auditoria verifica se a metodologia reconstruída funciona como uma cadeia coerente de decisão e execução, sem exigir que ChatGPT, Codex ou uma pessoa nova no projeto adivinhem:

- a ordem das etapas;
- quem possui autoridade sobre cada tipo de decisão;
- quais documentos são fonte canônica;
- quando uma etapa pode avançar;
- quando uma mudança exige retorno;
- quando o Codex pode começar;
- como o agente deve parar;
- como backlog, rastreabilidade e evidência se conectam.

A auditoria não valida ainda a ergonomia completa do processo em projetos diferentes.

Essa validação será realizada por casos de uso ponta a ponta.

---

## 2. Veredito

```text
METHODOLOGY_AUDIT: PASS_WITH_CASE_VALIDATION_PENDING
DOCUMENT_CHAIN: COHERENT
ROLE_BOUNDARIES: COHERENT
CANONICAL_FORMAT: MARKDOWN
CODEX_HANDOFF: DEFINED
END_TO_END_CASE_VALIDATION: PENDING
STABLE_RELEASE_READY: NO
```

Estado recomendado após esta auditoria:

```text
READY_FOR_CASE_VALIDATION
```

A metodologia não deve ser tratada como versão estável antes de pelo menos os casos de uso planejados percorrerem o processo documento por documento e produzirem evidência sobre carga, lacunas, redundâncias e handoff.

---

## 3. Inventário auditado

A cadeia operacional atual é:

```text
00 Discovery
01 Pesquisa e Viabilidade
02 Briefing de Produto e Escopo
03 Visão de Product Owner
03A Princípios de UX/UI
04 Direção de UI e Design System
05 Especificação de UX
06 Técnicas de Desenvolvimento
07 Engenharia e Arquitetura
07A Visão do Tech Lead
08 DevOps e Infraestrutura
09 Plano de Fundação
10 Backlog Canônico, Rastreabilidade e Plano de Entrega
11 Matriz Operacional de Rastreabilidade
12 Reconciliação da Baseline e Handoff para Codex
EXEC CODEX_CANONICAL_START_V1
```

Os nomes `03A` e `07A` são posições lógicas definidas pelo `PROCESS_MANIFEST.md`; os arquivos históricos permanecem `Principios_de_UX_UI.md` e `Visao_do_Tech_Lead.md`.

---

## 4. Critérios auditados

### 4.1 Ordem e fechamento da cadeia

**Resultado: PASS após correção.**

Antes desta auditoria, o README ainda apresentava `Infraestrutura e Fundação` como um único bloco e não materializava com precisão o documento 12 nem a chave de início do Codex.

A sequência documental real já estava mais madura que a capa.

Correção aplicada:

- criação de `docs/processo/PROCESS_MANIFEST.md`;
- atualização do README com a ordem completa;
- separação explícita entre `08 DevOps e Infraestrutura` e `09 Plano de Fundação`;
- inclusão explícita de `12 Reconciliação e Handoff`;
- inclusão do gatilho `CODEX_CANONICAL_START_V1`.

### 4.2 Autoridade por camada

**Resultado: PASS.**

As responsabilidades estão suficientemente separadas:

| Camada | Autoridade principal |
| --- | --- |
| Discovery | intenção, contexto, hipóteses e perguntas |
| Pesquisa | evidência, viabilidade, riscos e recomendações |
| Briefing | produto, promessa, escopo e limites |
| Product Owner | outcomes, comportamentos, regras, histórias e aceite de produto |
| Princípios UX/UI | critérios transversais para decisões de experiência |
| Direção de UI | linguagem visual e sistema visual reutilizável |
| Especificação de UX | jornadas, fluxos, estados, validação e recuperação |
| Técnicas de Desenvolvimento | método de trabalho de software e controles de qualidade |
| Engenharia e Arquitetura | forças técnicas, atributos de qualidade, boundaries, dados e arquitetura |
| Tech Lead | tecnologias concretas, frameworks, bibliotecas, runtimes e toolchain |
| DevOps e Infraestrutura | providers, ambientes, pipelines, operação, secrets, observabilidade, recovery e custos |
| Plano de Fundação | ordem de bootstrap, FNDs, dependências e provas fundacionais |
| Backlog Canônico | ordem global de execução sem redefinir as fontes |
| Matriz Operacional | cobertura bidirecional entre intenção, execução, testes e evidência |
| Handoff | reconciliação final e autorização explícita para Codex |

Não foi identificado motivo para fundir novamente Tech Lead, Arquitetura e Infraestrutura.

A separação deve ser preservada durante os casos de uso para verificar se permanece prática em produtos menores.

### 4.3 Pesquisa versus decisão

**Resultado: PASS.**

A metodologia diferencia adequadamente:

```text
EVIDÊNCIA
INFERÊNCIA
RECOMENDAÇÃO
HIPÓTESE
DECISÃO HUMANA
PENDÊNCIA
```

Pesquisa pode investigar solução técnica ou direção de UX quando necessário para viabilidade, mas não deve transformar recomendação preliminar em stack ou contrato definitivo.

### 4.4 Produto versus implementação

**Resultado: PASS.**

Briefing e Product Owner possuem fronteiras explícitas contra seleção prematura de tecnologia.

A cadeia correta é:

```text
NECESSIDADE / COMPORTAMENTO
↓
REQUISITO DE EXPERIÊNCIA
↓
REQUISITO TÉCNICO
↓
ARQUITETURA
↓
TECH-REQ
↓
SELEÇÃO TECNOLÓGICA
```

### 4.5 UX/UI

**Resultado: PASS.**

A separação está coerente:

```text
PRINCÍPIOS
= como julgamos decisões

DIREÇÃO DE UI
= como o produto se expressa visualmente

UX
= como a pessoa realiza tarefas ponta a ponta
```

`Principios_de_UX_UI.md` possui natureza transversal e pode ser reconciliado quando evidência posterior revelar conflito real.

Isso não autoriza uma camada posterior a sobrescrever o documento silenciosamente.

### 4.6 Técnicas versus stack

**Resultado: PASS.**

`06_Tecnicas_de_Desenvolvimento.md` define controles como revisão, testes, segurança, CI conceitual e qualidade, mas não deve selecionar tecnologias concretas.

A seleção pertence à Visão do Tech Lead.

### 4.7 Engenharia/Arquitetura versus Tech Lead

**Resultado: PASS.**

A arquitetura mede o problema técnico e produz requisitos da stack.

O Tech Lead compara candidatos contra esses requisitos.

A metodologia evita o padrão:

```text
PREFERÊNCIA PESSOAL
↓
STACK
↓
ARQUITETURA TENTANDO SE ADAPTAR
```

E adota:

```text
PRODUTO + UX + RISCOS
↓
DRIVERS E ATRIBUTOS DE QUALIDADE
↓
ARQUITETURA
↓
TECH-REQs
↓
CANDIDATOS
↓
HARD CONSTRAINTS
↓
COMPARAÇÃO / POC
↓
TDR
```

### 4.8 Tech Lead versus DevOps/Infra

**Resultado: PASS.**

A fronteira está adequada.

Exemplo:

```text
PostgreSQL como engine
→ Tech Lead

onde PostgreSQL será executado, região, backup, plano e custo
→ DevOps / Infra
```

Decisões SaaS fortemente acopladas à aplicação podem ser `JOINT_TECH_LEAD_INFRA`.

### 4.9 DevOps/Infra versus Fundação

**Resultado: PASS.**

Infra define a topologia operacional.

Plano de Fundação transforma isso em sequência verificável.

```text
INFRA
= decisão operacional

FUNDAÇÃO
= bootstrap ordenado e provado
```

### 4.10 Plano de Fundação versus Backlog

**Resultado: PASS.**

`FND-xxx` permanece estável ao atravessar as duas camadas.

O Plano de Fundação define capacidade, dependência fundacional, runway, risco e evidência.

O Backlog integra FNDs ao portfólio completo de produto.

Não deve achatar vários FNDs em uma task genérica de setup.

### 4.11 `FND-GAT` versus `GAT`

**Resultado: PASS COM CONVENÇÃO.**

As famílias possuem escopos diferentes:

- `FND-GAT-xxx`: gate interno da preparação fundacional;
- `GAT-xxx`: gate global de produto, release, operação, jurídico, fornecedor ou outro bloqueio do backlog.

A distinção precisa ser mantida nos casos de uso para evitar colisão semântica.

### 4.12 Backlog versus Matriz

**Resultado: PASS.**

O Backlog é a tradução operacional da baseline.

A Matriz é a prova de ligação.

```text
BACKLOG
= o que executamos, em qual ordem, sob quais contratos

MATRIZ
= de onde veio, o que afeta, como provamos e qual evidência existe
```

O nome histórico do documento 10 ainda contém `Rastreabilidade`, mas a responsabilidade detalhada da matriz permanece no documento 11.

Não foi considerado bloqueante para os casos de uso.

### 4.13 Formato canônico da Matriz

**Resultado: PASS.**

A Matriz atual é Markdown.

Planilha XLSX do DayGym permanece apenas como evidência histórica da origem do método, não como formato canônico.

A metodologia atual declara explicitamente que Excel pode auxiliar análise, mas não substituir a matriz versionável em Git.

### 4.14 Handoff para Codex

**Resultado: PASS ESTRUTURAL; VALIDAÇÃO REAL PENDENTE.**

O documento 12 define:

```text
BASELINE_READINESS
HANDOFF_READINESS
BASELINE_FREEZE
EXECUTION_AUTHORIZATION
CONTINUATION_POLICY
CODEX_TRIGGER
```

O gatilho é:

```text
CODEX_CANONICAL_START_V1
```

A chave não funciona como autorização irrestrita.

O Codex deve resolver backlog, matriz, fontes, gates, testes, evidências e stop conditions antes de alterar o projeto.

Para reduzir dependência de prompt manual, foi criado:

```text
templates/AGENTS.md
```

como loader opcional para projetos que adotam um mecanismo de instrução persistente de agente.

### 4.15 ChatGPT versus Codex

**Resultado: PASS.**

A fronteira está adequada:

```text
CHATGPT
ajuda a descobrir, pesquisar, decidir, documentar e reconciliar

CODEX
consome a baseline aprovada e executa o trabalho autorizado
```

Codex não deve reconstruir produto a partir da conversa bruta.

### 4.16 Aprovação humana

**Resultado: PASS.**

As etapas mantêm a disciplina:

```text
PROPOSTA
↓
REVISÃO HUMANA
↓
AJUSTE
↓
APROVAÇÃO
↓
CANONIZAÇÃO
```

O documento 12 adiciona uma segunda distinção necessária:

```text
BASELINE TECNICAMENTE READY
≠
EXECUÇÃO HUMANA AUTORIZADA
```

### 4.17 Evolução e loops de retorno

**Resultado: CORRIGIDO.**

A versão anterior do README fazia a evolução voltar genericamente ao Discovery.

Isso era amplo demais.

A regra auditada agora é:

> **a mudança retorna à maior autoridade realmente afetada.**

Exemplos:

```text
novo problema
→ Discovery

mudança de escopo
→ Briefing

mudança de regra/outcome
→ PO

mudança de UX
→ UX/UI

mudança de arquitetura
→ Engenharia/Arquitetura

mudança de stack
→ Tech Lead

mudança de provider
→ Infra
```

Isso reduz retrabalho e preserva governança.

### 4.18 Greenfield e brownfield

**Resultado: PASS.**

A metodologia reconhece que código existente é evidência operacional, não fonte automática de verdade.

Projetos brownfield devem classificar o estado existente antes de preservar ou substituir comportamento.

### 4.19 Segurança, privacidade e dados reais

**Resultado: PASS.**

As camadas técnicas e o handoff repetem adequadamente que:

- secrets não pertencem a prompts/documentação;
- dados reais dependem de autorização;
- produção possui gates próprios;
- CI e agentes devem preferir credenciais de curta duração quando a solução aprovada permitir;
- backup sem restore testado não prova recuperação.

### 4.20 Evidência

**Resultado: PASS.**

A metodologia diferencia evidência esperada e real.

```text
EXPECTED
≠
VERIFIED
```

E também:

```text
MERGED
≠
DONE
```

### 4.21 Atualidade de fatos técnicos

**Resultado: PASS.**

Pesquisa, Tech Lead e Infra exigem reconfirmação atual para fatos que envelhecem.

Versão, preço, região, licença, limite, política, EOL e compatibilidade não devem ser canonizados apenas pela memória do modelo.

---

## 5. Inconsistências encontradas e tratamento

### AUD-001 — README atrás da arquitetura documental

**Severidade:** material  
**Estado:** corrigido

O fluxo da capa não refletia todos os documentos criados durante a reconstrução.

Correção: README atualizado e manifesto criado.

### AUD-002 — Evolução voltava sempre ao Discovery

**Severidade:** material  
**Estado:** corrigido

Correção: retorno agora ocorre pela autoridade afetada.

### AUD-003 — Ordem alfabética não representa `03A` e `07A`

**Severidade:** média  
**Estado:** mitigado

Os nomes históricos foram preservados para evitar renumeração ampla.

`PROCESS_MANIFEST.md` passa a ser a fonte de ordem.

Renomear fisicamente esses dois arquivos pode ser reconsiderado apenas em uma mudança de versão planejada, não como correção silenciosa.

### AUD-004 — Frontmatter inicial não é totalmente uniforme

**Severidade:** baixa  
**Estado:** aberto não bloqueante

Os primeiros documentos usam algumas formas humanas em `next_stage`, e `01_Pesquisa_e_Viabilidade.md` usa `consumes` escalar enquanto documentos posteriores usam lista.

Isso não altera o conteúdo normativo.

A ordem operacional agora é resolvida pelo `PROCESS_MANIFEST.md`.

Antes de uma versão estável, pode ser realizada uma normalização mecânica de frontmatter em commit isolado.

### AUD-005 — Exemplos antigos parecem atuais pela localização

**Severidade:** material  
**Estado:** mitigado

`examples/ava-omem/` pertence a uma iteração anterior, com numeração e responsabilidades diferentes.

Foi criado `examples/README.md` declarando explicitamente seu estado legado.

A substituição por novos casos atuais ocorrerá na fase de validação.

### AUD-006 — Handoff novo ainda não foi exercitado ponta a ponta

**Severidade:** material  
**Estado:** aberto por design

O protocolo está documentado, mas precisa ser testado em um projeto produzido pela cadeia atual.

Esse é um dos objetivos centrais dos próximos casos de uso.

### AUD-007 — Não existia loader reutilizável para mecanismo persistente de agente

**Severidade:** média  
**Estado:** corrigido

Foi criado `templates/AGENTS.md`.

Ele é loader, não fonte de produto nem cópia da metodologia.

---

## 6. Artefatos introduzidos pela auditoria

### `docs/processo/PROCESS_MANIFEST.md`

Índice operacional e ordem canônica.

### `templates/AGENTS.md`

Loader reutilizável para Codex/agente em projetos compatíveis.

### `examples/README.md`

Política para exemplos atuais e quarentena explícita dos exemplos legados.

### README atualizado

A capa agora representa a arquitetura documental real.

---

## 7. O que não foi alterado

A auditoria não:

- reescreveu as decisões de cada etapa;
- reintroduziu frameworks antigos de governança;
- mudou a stack de qualquer projeto;
- transformou exemplos legados em canônicos;
- autorizou release da metodologia;
- executou Codex sobre um caso atual;
- criou os novos casos de uso.

---

## 8. Critérios para considerar a metodologia pronta para release estável

Antes de marcar versão estável, recomenda-se provar pelo menos:

1. um caso B2B com requisitos operacionais e múltiplas regras de negócio;
2. um caso de menor complexidade, como site empresarial, para testar proporcionalidade do processo;
3. um caso consumer com múltiplos domínios e dados potencialmente sensíveis;
4. geração documento por documento, com revisão humana simulada entre etapas;
5. pesquisa real nas etapas em que a evidência externa for necessária;
6. chegada até o documento 12 sem contradições materiais;
7. acionamento do `CODEX_CANONICAL_START_V1` em pelo menos um caso implementável;
8. verificação de que o Codex consegue resolver o próximo item sem receber todo o contexto manualmente;
9. teste das stop conditions;
10. registro de ajustes na metodologia descobertos durante os casos.

---

## 9. Política para os próximos casos

Os casos de uso devem ser tratados como **experimentos da metodologia**, não como material publicitário.

Cada caso deve avançar um documento por vez.

Quando a etapa exigir retorno ao cliente ou owner, o cenário deve simular essa aprovação antes de canonizar.

Se um caso revelar que uma etapa possui informação demais, de menos ou na camada errada, a metodologia deve ser corrigida na fonte responsável e o caso retomado a partir da baseline reconciliada.

---

## 10. Estado de saída

```text
TRANSVERSAL_AUDIT: COMPLETE
PROCESS_MANIFEST: CREATED
README: RECONCILED
LEGACY_EXAMPLES: QUARANTINED_BY_POLICY
CODEX_AGENT_LOADER_TEMPLATE: CREATED
CASE_VALIDATION: READY_TO_START
METHODOLOGY_RELEASE: BLOCKED_UNTIL_CASE_EVIDENCE
```

## 11. Princípio de fechamento

> **A auditoria não procura provar que a metodologia está pronta porque possui muitos documentos. Ela procura provar que cada documento tem uma responsabilidade legítima, que as decisões atravessam as camadas sem perder autoridade e que a implementação pode começar sem obrigar o agente a inventar o que a documentação deveria ter decidido.**

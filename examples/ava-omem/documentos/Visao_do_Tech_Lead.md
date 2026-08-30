---
document_id: TECH-LEAD-VISION
title: Visão do Tech Lead
status: canonical-example
version: 1.1.0
depends_on:
  - DOC-06
  - DOC-07
reconciled_with:
  - Infraestrutura_e_Plano_de_Fundacao
governs:
  - languages
  - runtimes
  - frameworks
  - libraries
  - toolchain
  - technology-standards
---

# Visão do Tech Lead — AVA OMEM

> **Pesquisa de referência:** 2026-08-30.  
> **Regra:** versões, suporte e compatibilidade devem ser revalidados antes do FND e de upgrades materiais.

## 1. Objetivo

Materializar o Documento 06 e o Documento 07 em uma stack tecnológica explícita, pequena, coerente e adequada a uma equipe reduzida.

A sequência deste exemplo é:

```text
DOC-06
qualidade e disciplina de código
        +
DOC-07
forças + arquitetura + boundaries
        ↓
VISÃO DO TECH LEAD
linguagem + runtime + frameworks + libraries + tooling
        ↓
INFRAESTRUTURA
providers e ambientes compatíveis
```

Este documento não altera a arquitetura para acomodar uma tecnologia preferida.

## 2. Necessidades recebidas da arquitetura

```text
TL-NEED-001 — Web e API compartilham contratos tipados sem acoplar domínio a framework.
TL-NEED-002 — packages/domain permanece independente de UI, HTTP, banco e providers.
TL-NEED-003 — web e API possuem build/deploy independentes no mesmo monorepo.
TL-NEED-004 — boundaries externas possuem validação em runtime.
TL-NEED-005 — persistência principal é relacional, transacional e indexável.
TL-NEED-006 — unit, integration, E2E e boundary checks são automatizáveis.
TL-NEED-007 — equipe pequena exige baixa quantidade de modelos mentais/tooling sobreposto.
TL-NEED-008 — não existe requisito de SSR no Beta.
TL-NEED-009 — API HTTP deve ser stateless.
TL-NEED-010 — integrações com OMEM entram por adapters/ports.
```

## 3. Pesquisa tecnológica atual

Antes da decisão foram consultadas fontes oficiais/relevantes de manutenção.

### Node.js

Fonte oficial: https://nodejs.org/en/download

Em 2026-08-30, Node.js 24 está na linha LTS enquanto Node.js 26 está na linha Current.

**Decisão:** usar **Node.js 24 LTS** no backend e nas ferramentas que dependem de Node. Produção privilegia LTS; a linha Current não traz benefício necessário ao Beta.

### TypeScript

Fonte oficial: https://devblogs.microsoft.com/typescript/announcing-typescript-6-0/

TypeScript 6.0 foi lançado em 2026 e mantém o objetivo de type checking e tooling forte.

**Decisão:** **TypeScript 6.x**, com configuração strict e sem supressões usadas apenas para silenciar erros.

### React

Fonte oficial: https://react.dev/blog/2025/10/01/react-19-2

React 19.2 é uma linha estável disponível no período da pesquisa.

**Decisão:** **React 19.2.x** para a aplicação web.

### Vite

Fonte oficial: https://vite.dev/blog/announcing-vite8

Vite 8 foi lançado como versão estável em 2026.

**Decisão:** **Vite 8.x** como build/dev tooling da web.

### React Router

Fonte oficial: https://reactrouter.com/home/changelog

React Router 8 foi lançado em 2026.

**Decisão:** **React Router 8.x**, usado no modo necessário para uma SPA cliente. O projeto não ativa SSR/framework mode apenas porque a biblioteca oferece esse recurso.

### Fastify

Fonte oficial: https://fastify.dev/docs/v5.3.x/Guides/Migration-Guide-V5/

Fastify v5 suporta Node.js 20+ e permite validação explícita de schemas.

**Decisão:** **Fastify 5.x** para a API HTTP.

### Zod

Fonte de referência: https://github.com/colinhacks/zod

Zod 4 é a linha atual durante a pesquisa e fornece schema validation com inferência de tipos.

**Decisão:** **Zod 4.x** para contratos e validação de dados que atravessam boundaries externas.

### Vitest e Playwright

Fontes oficiais:

- https://vitest.dev/
- https://playwright.dev/docs/intro

Vitest possui integração natural com o ecossistema Vite; Playwright suporta Node 24 e atende jornadas E2E em navegadores reais.

**Decisão:** **Vitest 4.x** para unit/integration onde apropriado e **Playwright** para E2E/smoke de navegador, com versão compatível fixada no lockfile durante FND.

## 4. Stack canônica

| Responsabilidade | Decisão | Política |
| --- | --- | --- |
| Linguagem principal | TypeScript 6.x | strict |
| Runtime API/tooling | Node.js 24 LTS | patch travado no FND |
| Web UI | React 19.2.x | sem RSC/SSR no Beta |
| Build web | Vite 8.x | configuração mínima |
| Routing web | React Router 8.x | SPA/Data/Declarative conforme necessidade; sem server framework por hábito |
| API HTTP | Fastify 5.x | thin controllers + application/domain abaixo |
| Runtime validation | Zod 4.x | boundaries e contratos |
| Banco lógico | PostgreSQL | provider decidido em Infraestrutura |
| Driver SQL da API | `pg` | apenas adapters de infraestrutura |
| Server-state web | `@tanstack/react-query` | cache de dados remotos; não usar como state store genérico |
| Forms | `react-hook-form` quando formulários justificarem | estado simples continua local |
| Unit/integration runner | Vitest 4.x | testes próximos do comportamento |
| UI/component tests | Testing Library | testar comportamento acessível |
| E2E | Playwright | jornadas críticas e smoke |
| Package manager | pnpm | workspace nativo; versão fixada no FND |
| Workspace | pnpm workspaces | sem Turborepo/Nx inicialmente |
| Lint | ESLint + TypeScript ESLint | config compartilhada |
| Formatting | Prettier | sem regras concorrentes de estilo |
| Logging API | logger estruturado do Fastify/Pino | nunca logar secrets |

As versões patch exatas pertencem ao lockfile e à Fundação. Major/minor acima representam decisões de compatibilidade deste documento.

## 5. Organização tecnológica do monorepo

```text
/apps
  /web          React + Vite
  /api          Fastify
/packages
  /domain       TypeScript puro, sem framework/provider
  /contracts    Zod + tipos públicos compartilháveis
  /design-tokens
  /config       configs compartilhadas de tooling
/infra          manifests/scripts operacionais aprovados
/tooling        checks de boundaries e automações locais
/docs
```

Regras:

- `packages/domain` não importa React, Fastify, `pg` ou SDK de provider;
- `packages/contracts` pode expor schemas Zod e tipos inferidos destinados às boundaries;
- `apps/api` adapta HTTP para application/domain;
- acesso SQL fica atrás de repositories/adapters;
- `apps/web` consome API pública e nunca usa credencial administrativa;
- provider SDK entra somente na camada autorizada por este documento.

## 6. Dados e migrations

### Banco

**PostgreSQL** é escolhido como engine relacional porque satisfaz `TL-NEED-005` e possui ampla compatibilidade com serviços gerenciados.

### Acesso a dados

**Decisão inicial:** não adicionar ORM completo no Beta.

A API utiliza `pg` em adapters/repositories explícitos.

Motivos:

- mantém queries e transações visíveis;
- evita criar segundo modelo de domínio;
- reduz dependências e geração de código;
- permite substituir provider sem alterar regras de negócio.

Os resultados de queries relevantes devem ser mapeados/validados nas boundaries adequadas; tipos estáticos não substituem validação de dados externos.

### Migrations

O formato canônico é **SQL versionado no repositório**.

O executor concreto pode ser reconciliado após a escolha do provider, desde que:

- não altere o formato histórico silenciosamente;
- seja reproduzível em CI/staging;
- não faça drift fora do Git.

## 7. Estado e dados no frontend

### Server state

`@tanstack/react-query` é a solução canônica para cache, sincronização e invalidação de dados vindos da API.

### Estado local

Estado que pertence a uma tela/componente permanece em React local state ou primitives equivalentes.

### State manager global

**Não adicionar Redux, Zustand ou outro state manager global no Beta sem requisito comprovado.**

A combinação React local state + router + query cache cobre as necessidades atuais com menos modelos mentais.

### Formulários

`react-hook-form` pode ser usado em formulários administrativos com validação/estado suficiente para justificar a biblioteca. Formulários triviais não precisam de abstração adicional.

## 8. Contratos e validação

Zod é canônico para payloads externos relevantes.

```text
request externa
   ↓
Zod parse/validation
   ↓
application input tipado
   ↓
domain
```

Não duplicar schemas equivalentes em web e API quando o contrato puder ser compartilhado com segurança em `packages/contracts`.

Schemas de contrato não devem importar infraestrutura nem regras de UI.

## 9. Testes

### Vitest

Usar para:

- domínio;
- application services;
- utilities especializadas;
- contratos;
- componentes quando o teste em ambiente apropriado produzir valor.

### Testing Library

Usar para comportamento de componentes e superfícies, priorizando semântica/acessibilidade em vez de detalhes internos.

### Playwright

Usar para:

- convite/primeiro acesso;
- contexto de tenant;
- criação de empresa/turma;
- matrícula/trilha;
- conclusão/quiz;
- restrição do gestor;
- certificado;
- smoke de staging.

Teste E2E não substitui testes rápidos de domínio e integração.

## 10. Toolchain e qualidade

### pnpm

Escolhido pela capacidade nativa de workspaces e por reduzir a necessidade de tooling adicional para o monorepo pequeno.

### Sem orquestrador de monorepo inicialmente

**Turborepo/Nx não são adicionados no FND inicial.**

O projeto começa com scripts de workspace e CI simples. Reavaliar somente se tempos de build, cache ou grafo de tarefas criarem necessidade observável.

### Gates

A stack deve materializar comandos equivalentes a:

```text
format:check
lint
typecheck
test
build
check:boundaries
E2E/smoke quando aplicável
```

## 11. Bibliotecas que não são pré-aprovadas

Não existe aprovação genérica para instalar bibliotecas de:

- UI kits completos;
- state managers adicionais;
- ORMs adicionais;
- date libraries;
- charting;
- rich-text editors;
- realtime;
- queues;
- feature flags.

Quando uma funcionalidade real exigir uma delas, comparar alternativas e atualizar **este mesmo documento** se a escolha se tornar padrão do projeto.

## 12. Tecnologias rejeitadas neste estágio

### Next.js

**Não adotado no Beta.**

Não existe requisito atual de SSR, RSC ou backend acoplado ao framework web. A arquitetura já definiu API separada e deploy independente. React + Vite atende o escopo com menos superfície operacional.

Revisitar se requisitos reais de rendering/SEO alterarem essa premissa.

### NestJS

**Não adotado no Beta.**

A equipe é pequena e a arquitetura pede controllers finos, domínio independente e baixa complexidade acidental. Fastify atende HTTP com menos estrutura obrigatória.

Revisitar apenas se requisitos comprovados de módulos/decorators/ecossistema justificarem a camada adicional.

### ORM completo

**Não adotado inicialmente.**

SQL explícito em adapters é suficiente para o porte inicial e preserva controle de queries. Reavaliar se volume de modelagem repetitiva ou migrations tornar o custo manual maior que o benefício.

### Segundo state manager

**Não aprovado.**

Adicionar somente se estado global real não puder ser modelado adequadamente com as ferramentas canônicas.

## 13. Reconciliação após a decisão de Infraestrutura

A Infraestrutura deste exemplo aprovou Supabase para PostgreSQL/Auth/Storage, Cloudflare Pages para web, Cloud Run para API e Resend para e-mail.

Essa decisão não altera a arquitetura, mas autoriza integrações provider-specific localizadas:

```text
@supabase/supabase-js
→ permitido em adapters de Auth/Storage e integração cliente apenas com credencial pública apropriada
→ service role/secret somente no servidor

pg
→ conexão PostgreSQL da API pelo endpoint/pooler aprovado

resend SDK
→ permitido somente no adapter de Notifications
```

A UI e o domínio não passam a depender de Supabase ou Resend por causa dessa aprovação.

Se o provider mudar no futuro, o objetivo é trocar adapters e configuração, não reescrever regras de aprendizagem.

## 14. Saída para Fundação

```text
TL-STACK-001 — TypeScript 6.x aprovado.
TL-STACK-002 — Node.js 24 LTS aprovado.
TL-STACK-003 — React 19.2 + Vite 8 + React Router 8 aprovados para web.
TL-STACK-004 — Fastify 5 aprovado para API.
TL-LIB-001 — Zod 4 é validação/contrato canônico.
TL-LIB-002 — pg é driver SQL canônico da API.
TL-LIB-003 — TanStack Query é server-state canônico da web.
TL-LIB-004 — React Hook Form é solução aprovada para formulários que justificarem.
TL-TEST-001 — Vitest é runner unit/integration.
TL-TEST-002 — Testing Library é padrão de component behavior tests.
TL-TEST-003 — Playwright é E2E/smoke.
TL-TOOL-001 — pnpm workspaces é workspace/package management.
TL-TOOL-002 — ESLint + TypeScript ESLint + Prettier materializam lint/format.
TL-TOOL-003 — sem monorepo orchestrator no FND inicial.
```

## Critério de qualidade

Outro engenheiro ou agente deve conseguir iniciar o FND sem decidir novamente linguagem, runtime, frameworks principais, package manager, validação, acesso a dados, estratégia de state, testes ou tooling central.

Ao mesmo tempo, ele não recebe autorização para instalar dependências especializadas não previstas apenas porque “podem ser úteis”.
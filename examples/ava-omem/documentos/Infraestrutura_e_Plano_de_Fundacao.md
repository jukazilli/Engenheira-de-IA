---
title: Infraestrutura e Plano de Fundação
status: canonical-example
version: 1.1.0
depends_on:
  - DOC-06
  - DOC-07
  - TECH-LEAD-VISION
---

# Infraestrutura e Plano de Fundação — AVA OMEM

> **Pesquisa de referência:** 2026-08-30.  
> **Regra:** preços, free tiers, regiões, limites e compatibilidade devem ser revalidados antes de qualquer contratação ou FND real.

## 1. Respostas da entrevista

- produto pode evoluir para oferta comercial;
- começar com custo zero quando for seguro e coerente;
- staging em nuvem desde o início;
- menos de 500 usuários no Beta;
- dados pessoais básicos e dados de aprendizagem;
- preferência por serviços gerenciados;
- sem equipe DevOps dedicada;
- qualquer recurso pago exige aprovação humana explícita.

## 2. Stack recebida da Visão do Tech Lead

A infraestrutura não escolhe novamente a stack.

```text
Web        → React 19.2 + Vite 8 + React Router 8
API        → Node.js 24 LTS + Fastify 5
Contratos  → Zod 4
Banco      → PostgreSQL
DB driver  → pg em adapters
Tests      → Vitest + Testing Library + Playwright
Workspace  → pnpm workspaces
```

O objetivo desta etapa é escolher **providers e ambientes capazes de executar essa stack**.

## 3. Estratégia geral

```text
GitHub
   ↓
GitHub Actions
   ↓
Cloudflare Pages — web SPA
   +
Google Cloud Run — API Node/Fastify
   ↓
Supabase — PostgreSQL/Auth/Storage
   ↓
Resend — e-mail transacional
   ↓
staging validado
```

Essa composição foi escolhida para manter baixa complexidade operacional e boundaries compatíveis com o Documento 07.

## 4. Pesquisa atual de referência

### Supabase

Fonte oficial: https://supabase.com/pricing

Na pesquisa realizada em 2026-08-30, o plano Free informava, entre outros limites relevantes:

- 50.000 MAU;
- 500 MB de banco por projeto;
- 1 GB de file storage;
- limite de dois projetos ativos gratuitos;
- pausa de projeto gratuito após período de inatividade.

O plano Pro iniciava em US$ 25/mês na data pesquisada.

**Uso aprovado no exemplo:** PostgreSQL, Auth e Storage gerenciados.

**Região desejada:** São Paulo (`sa-east-1`) quando disponível para os recursos aplicáveis, para manter coerência geográfica com a operação brasileira.

**Atenção:** produção comercial, backups, retenção e disponibilidade precisam de nova avaliação antes do go-live.

### Cloudflare Pages

Fonte oficial: https://developers.cloudflare.com/pages/functions/pricing/

Na pesquisa de 2026-08-30, requests de assets estáticos em Pages eram gratuitas e sem limite de requests de asset estático; Pages Functions compartilhavam os limites/billing de Workers.

**Uso aprovado no exemplo:** hosting do build estático React/Vite.

O Beta não precisa de Pages Functions para sua API principal, evitando misturar runtime da web com a API separada definida pela arquitetura.

### Google Cloud Run

Fonte oficial: https://cloud.google.com/run/pricing

Na pesquisa de 2026-08-30, Cloud Run utilizava cobrança por uso após free tier. Para request-based billing, a documentação informava free tier mensal incluindo CPU, memória e 2 milhões de requests, com valores e disponibilidade dependentes da região. São Paulo (`southamerica-east1`) aparece entre as regiões disponíveis.

**Uso aprovado no exemplo:** API Node.js/Fastify em container gerenciado, região São Paulo quando compatível com todos os requisitos.

**Classificação:** `POTENCIALMENTE COBRÁVEL`.

Mesmo que o uso estimado caiba no free tier, criação/configuração que exija billing account deve passar pelo gate humano antes do FND.

### Resend

Fonte oficial: https://resend.com/pricing

Na pesquisa de 2026-08-30, o plano Free informava 3.000 e-mails/mês e limite de 100 por dia.

**Uso aprovado no exemplo:** convites, recuperação e notificações transacionais do Beta.

### GitHub Actions

Fonte oficial: https://docs.github.com/en/actions/concepts/billing-and-usage

Runners padrão podem ter tratamento diferente conforme visibilidade do repositório e plano da conta.

**Uso aprovado no exemplo:** CI e quality gates.

**Atenção:** o projeto real da consultoria pode ser privado; custo deve ser verificado na conta efetiva antes de assumir gratuidade.

## 5. Decisões de provider

### Repositório e CI

- GitHub;
- monorepo conforme Documento 07;
- GitHub Actions para CI;
- branch `main` protegida quando o plano/ambiente permitir;
- PR como caminho padrão de promoção depois da Fundação.

### Web

- Cloudflare Pages;
- deploy do build estático produzido por Vite;
- HTTPS;
- domínio técnico de staging;
- somente variáveis destinadas ao cliente podem entrar no bundle;
- nenhum secret administrativo na web.

### API

- Google Cloud Run;
- Node.js 24 LTS dentro do runtime/container aprovado;
- Fastify 5;
- serviço stateless;
- `min instances = 0` no estágio inicial salvo necessidade medida;
- health endpoint;
- secrets somente no ambiente do serviço;
- logs estruturados;
- região `southamerica-east1` como preferência aprovada para staging.

A escolha do provider acontece **antes do FND**. O FND valida e cria o recurso aprovado; ele não abre novamente uma disputa entre Workers, Cloud Run ou outros providers sem uma restrição nova.

### Banco/Auth/Storage

- Supabase;
- PostgreSQL como engine aprovada pelo Tech Lead;
- Auth gerenciado;
- Storage privado para materiais não públicos;
- migrations SQL versionadas no repo;
- Supabase CLI pode executar as migrations aprovadas na Fundação sem transformar o domínio em dependente do provider;
- `pg` na API para acesso relacional via conexão/pooler aprovado;
- `@supabase/supabase-js` somente nos adapters de Auth/Storage e, no cliente, apenas com credencial pública apropriada;
- service role ou segredo equivalente nunca entra no frontend.

### E-mail

- Resend;
- SDK do provider restrito ao adapter de Notifications;
- domínio de envio validado;
- secret somente no runtime seguro.

### Observabilidade

Para o FND:

- logs estruturados da API no Cloud Run;
- logs de deploy/execução do CI;
- captura de falhas críticas de web/API por mecanismo aprovado durante a Fundação;
- alertas mínimos para falha de deploy e erro crítico;
- nenhum payload sensível em logs.

Se uma ferramenta externa adicional de error tracking for necessária e puder gerar custo, ela exige nova decisão explícita; não é instalada silenciosamente.

## 6. Compatibilidade stack ↔ infraestrutura

| Decisão Tech Lead | Infra aprovada | Resultado |
| --- | --- | --- |
| React + Vite SPA | Cloudflare Pages | compatível com build estático |
| Node 24 + Fastify | Cloud Run | compatível com runtime/container Node |
| PostgreSQL | Supabase | engine compatível |
| pg | Supabase Postgres/pooler | compatível via adapter da API |
| Auth/Storage adapters | Supabase | SDK autorizado somente nas boundaries definidas |
| Playwright | CI + staging público controlado | compatível para smoke/E2E |

Se a validação real do FND contradisser alguma linha, o item fica `Blocked` e a decisão retorna para reconciliação. O Codex não troca framework ou provider silenciosamente.

## 7. Ambientes

### Local

Desenvolvimento e testes rápidos, usando serviços locais/emulados quando isso não cria comportamento diferente do contrato real.

### Staging

Obrigatório desde a Fundação, porque será usado pela consultoria e por usuários piloto.

- web: Cloudflare Pages staging;
- API: Cloud Run staging;
- banco/auth/storage: projeto Supabase de staging;
- e-mail: configuração de teste do Resend.

### Production

Não será criado automaticamente no primeiro setup.

Staging precisa produzir evidências antes de qualquer promoção. A criação de produção exige revisão de custo, backup/restore, disponibilidade, privacidade, domínio e observabilidade.

## 8. Segurança de credenciais

Nenhuma senha, service role key, private key, refresh token ou API secret deve ser enviada pelo chat.

Fluxo para setup humano-assistido:

```text
agente abre/prepara painel
        ↓
humano autentica diretamente
        ↓
MFA/CAPTCHA ficam com o humano
        ↓
agente continua na sessão autorizada
```

Preferência de automação:

```text
API/CLI/IaC
   ↓
OAuth/conector
   ↓
Playwright em sessão autorizada
   ↓
runbook manual seguro
```

## 9. Itens de Fundação derivados

Os IDs abaixo são mantidos consistentes com o Documento 08 deste exemplo.

```text
FND-001 — inicializar monorepo conforme DOC-07
FND-002 — fixar stack/toolchain conforme Visão do Tech Lead
FND-003 — configurar quality gates locais
FND-004 — configurar CI
FND-005 — criar banco/auth de staging
FND-006 — criar migrations baseline e autorização de tenant
FND-007 — publicar web em staging
FND-008 — publicar API em staging com secrets/logs mínimos
FND-009 — configurar e-mail transacional de teste
FND-010 — executar smoke test consolidado da Fundação
```

Secrets e observabilidade mínima são critérios transversais dos itens que criam os respectivos runtimes, não IDs concorrentes com significados diferentes.

## 10. Gate de custo

Antes de criar qualquer recurso:

```text
FREE / INCLUÍDO
POTENCIALMENTE COBRÁVEL
COBRÁVEL
DESCONHECIDO — REVALIDAR
```

Qualquer estado diferente de `FREE / INCLUÍDO` exige explicação e aprovação humana antes da ação.

No exemplo, Cloud Run deve ser tratado como `POTENCIALMENTE COBRÁVEL`, mesmo havendo free tier, porque billing/configuração e excedentes podem gerar cobrança.

## 11. Fundação pronta

A Fundação não está pronta apenas porque contas existem.

```text
repo conforme arquitetura
+
stack/toolchain conforme Tech Lead
+
CI executando
+
banco e migrations funcionando
+
auth/tenant baseline validado
+
web e API em staging nos providers aprovados
+
secrets fora do código e do chat
+
logs mínimos
+
smoke tests aprovados
+
rastreabilidade reconciliada
=
FND_READY
```

Qualquer troca de provider ou tecnologia durante a Fundação precisa voltar para a camada documental responsável antes de se tornar novo padrão.
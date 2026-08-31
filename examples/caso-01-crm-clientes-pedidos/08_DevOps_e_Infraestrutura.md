---
document_id: CASE-01-DOC-08
title: DevOps e Infraestrutura — CRM para gestão de clientes e pedidos
status: canonical
version: 1.0.0
case_id: CASE-01-CRM-CLIENTES-PEDIDOS
methodology_stage: devops-infraestrutura
infra_research_date: 2026-08-31
consumes:
  - 00_Discovery.md
  - 01_Pesquisa_e_Viabilidade.md
  - 02_Briefing_de_Produto_e_Escopo.md
  - 03_Visao_de_Product_Owner.md
  - Principios_de_UX_UI.md
  - 04_Direcao_de_UI_e_Design_System.md
  - 05_Especificacao_de_UX.md
  - 06_Tecnicas_de_Desenvolvimento.md
  - 07_Engenharia_e_Arquitetura.md
  - Visao_do_Tech_Lead.md
next_document: 09_Plano_de_Fundacao.md
infra_readiness: SUFFICIENT_WITH_OPEN_QUESTIONS
ready_for_foundation: true
ready_for_codex: false
---

# DevOps e Infraestrutura — CRM para gestão de clientes e pedidos

## 1. Propósito

Este documento transforma a arquitetura e a stack aprovadas do Caso 01 em uma direção operacional concreta de ambientes, cloud, identidade, rede, CI/CD, banco gerenciado, segredos, observabilidade, backup, recuperação, custos e operação.

A pergunta central é:

> **Onde e como a stack aprovada será executada e operada para que o CRM permaneça seguro, recuperável, observável, economicamente compatível com o business case e capaz de integrar-se ao TOTVS Protheus on-premises sem expor o ERP diretamente à Internet?**

Esta etapa não redefine produto, UX, arquitetura ou stack.

Ela também não executa provisionamento.

```text
DECISÃO OPERACIONAL
≠
PROVISIONAMENTO EXECUTADO

INFRA_READINESS
≠
READY_FOR_CODEX
```

---

## 2. Hipóteses e fatos do cenário

### 2.1. Evidência canônica anterior

- CRM custom permanece condicionado ao business case;
- Protheus é autoridade para cliente formal, pedido, faturamento, estoque, histórico transacional e informação financeira ERP;
- CRM é autoridade para prospect, histórico comercial, próxima ação, carteira, transferências e outros dados próprios;
- arquitetura inicial é monólito modular;
- stack proposta utiliza aplicação web responsiva, TypeScript/Node, React/Vite, NestJS e PostgreSQL;
- integração Protheus fica atrás de adapter/anti-corruption boundary;
- Protheus indisponível não deve derrubar o core comercial do CRM;
- banco canônico do CRM precisa suportar target arquitetural inicial de RPO <= 15 min e RTO <= 4 h para incidentes severos compatíveis com o mecanismo escolhido.

### 2.2. Premissas simuladas aceitas para este caso

Para manter o caso executável como simulação, foram fixadas explicitamente as seguintes informações de cliente:

```text
PROTHEUS_HOSTING:
ON_PREMISES

TCLOUD:
NO

CORPORATE_IDENTITY:
MICROSOFT_365 / MICROSOFT_ENTRA_ID
```

Essas informações são **dados simulados do cenário**, não fatos públicos sobre um cliente real.

A decisão humana no exercício foi manter Protheus on-premises para seguir a simulação.

Consequência:

```text
CRM CLOUD
        ↓
CONEXÃO HÍBRIDA PRIVADA
        ↓
REDE DO CLIENTE
        ↓
TOTVS PROTHEUS ON-PREMISES
```

---

## 3. INFRA-REQs

### INFRA-REQ-001 — Região brasileira

A infraestrutura primária deve operar em região compatível com o contexto brasileiro do produto e com baixa latência razoável para usuários e integração.

**Origem:** produto + arquitetura.

**Obrigatória:** sim.

---

### INFRA-REQ-002 — Executar stack web/API aprovada

A plataforma deve executar a aplicação web e a API da stack aprovada sem exigir mudança arquitetural.

**Origem:** Visão do Tech Lead.

---

### INFRA-REQ-003 — PostgreSQL gerenciado

A infraestrutura deve operar PostgreSQL na linha aprovada, com backup, PITR, encryption, observabilidade e restore compatíveis com os targets arquiteturais.

---

### INFRA-REQ-004 — Conectividade privada com Protheus

A API do CRM precisa alcançar os serviços Protheus homologados/produtivos pela rede corporativa sem expor banco ou serviços internos diretamente ao browser.

---

### INFRA-REQ-005 — Ambientes isolados

Staging e production não podem compartilhar banco, secrets, credenciais OIDC ou credenciais Protheus.

---

### INFRA-REQ-006 — Identidade corporativa

O produto deve integrar-se à identidade corporativa simulada baseada em Microsoft Entra ID, sem delegar a esse provider as regras de autorização por carteira do CRM.

---

### INFRA-REQ-007 — CI sem credencial cloud permanente

O pipeline deve preferir identidade federada/OIDC a secrets administrativos de longa duração.

---

### INFRA-REQ-008 — Segredos fora do repositório

Secrets de banco, Protheus, OAuth e outros providers não podem existir em código, bundle, documentação pública ou prompt.

---

### INFRA-REQ-009 — Build rastreável e promovível

A mesma origem/artefato validado deve poder ser promovida de staging para produção sem rebuild silencioso de código.

---

### INFRA-REQ-010 — Observabilidade minimizada

Infra deve receber métricas/logs/traces necessários à operação sem transformar telemetria em cópia de conteúdo comercial ou payload integral do ERP.

---

### INFRA-REQ-011 — Restore verificável

Backup habilitado não é suficiente; restore precisa ser provado em ambiente isolado.

---

### INFRA-REQ-012 — Custo inicial controlado

Infraestrutura precisa permanecer compatível com a hipótese econômica da solução e possuir budgets/alertas antes do rollout produtivo.

---

## 4. Hard constraints

Uma alternativa é rejeitada se:

- não suporta a stack aprovada;
- exige alteração de engine ou arquitetura apenas para caber no provider;
- não oferece caminho de backup/restore compatível com os targets;
- não permite integração privada/suficientemente protegida com a rede on-premises;
- impede identidade corporativa aprovada;
- força secrets administrativos permanentes no CI sem necessidade;
- torna custo inicial incompatível com o business case;
- não oferece região/topologia operacional adequada ao cenário.

---

## 5. Pesquisa e comparação de providers

Foram avaliadas conceitualmente Azure, Google Cloud e AWS como opções capazes de executar o workload.

Todas possuem serviços suficientes para web/API, PostgreSQL e conectividade híbrida.

No cenário simulado, Azure foi preferido por **coerência operacional**, não por superioridade universal:

```text
MICROSOFT ENTRA ID JÁ EXISTENTE
+
PROTHEUS ON-PREMISES
+
NECESSIDADE DE CONECTIVIDADE HÍBRIDA
+
SERVIÇOS GERENCIADOS EM REGIÃO BRASILEIRA
+
TIME / PRODUTO PEQUENO

→ AZURE
```

O fator on-premises aumenta o valor de uma topologia clara de VNet + VPN site-to-site.

Se o cenário fosse TCloud, essa vantagem precisaria ser reavaliada.

---

## 6. Provider e região aprovados

### IDR-001 — Microsoft Azure como cloud principal

**Status:** aceito para o cenário.

**Alternativas:** AWS, Google Cloud.

**Motivos:** coerência com Entra ID já existente no cenário, conectividade híbrida, serviços gerenciados suficientes e redução de dispersão operacional.

**Lock-in:** aceitável com mitigação.

O domínio e o banco permanecem baseados em tecnologias portáveis; Bicep e serviços operacionais Azure criam lock-in de infraestrutura conscientemente aceito.

### IDR-002 — Brazil South como região primária

**Status:** aceito.

A aplicação será single-region no primeiro horizonte.

```text
MULTI_REGION:
NO
```

---

## 7. Topologia operacional

```text
                         INTERNET
                            │
                            ▼
                   crm.empresa.com.br
                            │
                            ▼
                 AZURE CONTAINER APPS
                      WEB / SPA
                            │
                            ▼
                 AZURE CONTAINER APPS
                       API CRM
                    │            │
                    │            ▼
                    │       AZURE VNET
                    │            │
                    │            ▼
                    │       VPN GATEWAY
                    │            │
                    │         IPsec/IKE
                    │            │
                    │            ▼
                    │      REDE CORPORATIVA
                    │            │
                    │            ▼
                    │      TOTVS PROTHEUS
                    │       ON-PREMISES
                    │
                    ▼
        AZURE DATABASE FOR POSTGRESQL
             FLEXIBLE SERVER
```

Invariantes:

```text
BROWSER → PROTHEUS
PROIBIDO

CRM API → PROTHEUS ADAPTER → REDE PRIVADA
PERMITIDO

STAGING → PROTHEUS PRODUÇÃO
PROIBIDO
```

---

## 8. Ambientes

### INFRA-ENV-001 — Local

Finalidade:

- desenvolvimento;
- testes rápidos;
- fakes/simuladores Protheus;
- dados sintéticos.

Não exige acesso de produção.

### INFRA-ENV-002 — PR/CI

Finalidade:

- lint;
- typecheck;
- testes;
- contract checks;
- build;
- segurança.

Não precisa de infraestrutura permanente completa.

### INFRA-ENV-003 — Staging

Finalidade:

- homologação;
- POCs de integração;
- smoke/E2E;
- teste de migrations;
- teste de restore;
- validação com Protheus homologação.

Dados sintéticos/anonimizados por padrão.

### INFRA-ENV-004 — Production

Finalidade:

- operação real.

Possui:

- banco próprio;
- secrets próprios;
- identidade própria;
- credenciais Protheus produtivas próprias;
- observabilidade própria;
- políticas de backup e acesso mais restritivas.

---

## 9. Ownership e contas

A infraestrutura deve pertencer à organização/empresa do projeto, não a uma conta pessoal isolada.

Papéis mínimos:

```text
BUSINESS OWNER
TECHNICAL OWNER
CLOUD / BILLING OWNER
SECURITY / BREAK-GLASS OWNER
```

Controles:

- MFA para contas humanas privilegiadas;
- e-mails de função quando aplicável;
- inventário de subscriptions/resources;
- recuperação de conta;
- break-glass documentado;
- acesso de produção restrito.

---

## 10. Identidade de usuários

### IDR-004 — Microsoft Entra ID single-tenant

**Status:** aceito para a simulação.

Fluxo tecnológico herdado:

```text
OIDC / OAuth2
Authorization Code + PKCE
```

Separação obrigatória:

```text
ENTRA
= autenticação de identidade

CRM BACKEND
= autorização de negócio
```

App registrations de staging e production são distintas.

Entra não decide carteira, ownership ou acesso financeiro do CRM.

---

## 11. Identidade de workloads e CI

### IDR-008 — GitHub Actions com OIDC para Azure

O CI deve usar federação OIDC/workload identity.

Não armazenar credencial administrativa Azure permanente no repositório.

Identidades separadas:

```text
CI-STAGING
CI-PRODUCTION
```

A identidade de produção recebe apenas permissões necessárias para promoção e ações aprovadas.

Produção exige gate/aprovação antes de deploy.

---

## 12. Secrets

### IDR-007 — Azure Key Vault + Managed Identity

Secrets de runtime ficam em serviço apropriado.

A aplicação acessa secrets necessários por Managed Identity/RBAC quando aplicável.

Exemplos:

- credencial técnica Protheus;
- segredo OIDC quando realmente necessário;
- credenciais de integrações futuras.

Banco deve preferir mecanismos de credencial/identidade compatíveis com a stack e provider quando maduros; senha não deve ser propagada indiscriminadamente.

Proibido:

```text
.env COM PRODUÇÃO NO GIT
SECRET EM FRONTEND
SECRET EM PROMPT
SECRET EM SCREENSHOT
SECRET EM LOG
```

---

## 13. Networking

### IDR-006 — VNet + VPN Gateway site-to-site

A rede Azure do CRM conecta-se à rede corporativa do cliente por VPN site-to-site.

Destino operacional:

```text
STAGING
→ Protheus homologação

PRODUCTION
→ Protheus produção
```

A API do CRM não depende de acesso público direto ao Protheus.

### Gate de rede

Antes de produção, provar:

- rotas;
- DNS/nomes necessários;
- firewall;
- portas;
- autenticação;
- timeout;
- perda de túnel;
- recuperação;
- segregação staging/production.

Se a VPN não puder ser estabelecida por restrição real do cliente, reabrir `IDR-006`, sem alterar silenciosamente o boundary arquitetural.

---

## 14. DNS e TLS

Direção:

```text
PRODUCTION
crm.empresa.com.br

STAGING
crm-stg.empresa.com.br
```

O provider de DNS corporativo pode permanecer onde já existir.

Não há necessidade de mover a zona inteira para Azure.

TLS obrigatório.

Staging deve evitar indexação pública acidental.

---

## 15. Hosting da aplicação

### IDR-003 — Azure Container Apps para web e API

Dois workloads principais:

```text
WEB
React/Vite build servido como artefato web

API
NestJS / Node.js
```

Vantagens no cenário:

- modelo operacional único;
- revisão/rollout;
- integração com VNet;
- containers reproduzíveis;
- escala controlada;
- sem necessidade de Kubernetes.

Produção da API começa com capacidade mínima que evite cold start relevante ao trabalho comercial.

Staging pode utilizar scale-to-zero quando isso não prejudicar testes planejados.

---

## 16. Artefatos e registry

### Azure Container Registry

Web e API produzem artefatos OCI identificáveis por:

```text
source_commit
release/version
artifact_digest
```

Produção não depende exclusivamente de tag mutável como `latest`.

Rollback de aplicação referencia digest anteriormente verificado.

---

## 17. CI/CD

Fluxo aprovado:

```text
PULL REQUEST
        ↓
format
lint
typecheck
unit/component
contract
security
build
        ↓
MERGE MAIN
        ↓
build web + api
        ↓
scan / evidence
        ↓
publish ACR por digest
        ↓
STAGING
        ↓
migrations compatíveis
        ↓
smoke / E2E crítico
        ↓
approval
        ↓
PROMOVER MESMO DIGEST
        ↓
PRODUCTION
        ↓
smoke
        ↓
observação
```

Regra:

```text
STAGING BUILD
= PRODUCTION BUILD
```

Quando plataforma/configuração exigir diferenças, elas devem ocorrer por configuração de ambiente e secrets, não por fonte diferente.

---

## 18. Rollout e rollback

Container Apps permite revisões controladas.

Padrão inicial:

```text
STAGING
100% nova revisão

PRODUCTION
nova revisão
→ smoke
→ 100%
```

Mudança de risco elevado pode usar canary/traffic split.

Rollback de aplicação não significa rollback de banco.

Migration incompatível exige estratégia própria.

---

## 19. Migrations

Processo conceitual:

```text
EXPAND
↓
DEPLOY COMPATÍVEL
↓
MIGRATE / BACKFILL
↓
VALIDATE
↓
SWITCH
↓
CONTRACT POSTERIOR
```

Proibido no caminho normal:

```text
MIGRATION DESTRUTIVA
+
APP INCOMPATÍVEL
+
UM ÚNICO PASSO IRREVERSÍVEL
```

---

## 20. PostgreSQL hospedado

### IDR-005 — Azure Database for PostgreSQL Flexible Server

Configuração lógica:

```text
ENGINE:
PostgreSQL 18.x current supported minor

REGION:
Brazil South

STAGING:
instância separada

PRODUCTION:
instância separada
```

A produção começa sem HA zonal obrigatório.

Gatilho de revisão:

> indisponibilidade da instância passar a produzir impacto incompatível com o RTO e o business case justificar custo adicional.

---

## 21. Banco próprio do CRM

A infraestrutura materializa uma decisão arquitetural importante:

> **O banco do CRM existe para dados cuja autoridade pertence ao CRM.**

Ele não existe para transformar dados Protheus em segunda fonte de verdade.

Persistir no banco CRM, conforme modelo posterior:

- prospects;
- interações;
- próximas ações;
- carteira/ownership;
- transferências;
- auditabilidade do CRM;
- idempotência;
- estado técnico necessário do CRM.

Dados Protheus:

- cliente formal;
- pedidos;
- estoque;
- faturamento;
- financeiro;
- metadata/dicionário Protheus;

permanecem sob autoridade do ERP.

Snapshots/cache locais só existem quando justificados e sempre carregam semântica de origem/freshness.

---

## 22. Metadata Protheus

A infraestrutura não cria um “dicionário Protheus do CRM”.

A direção aprovada após as POCs simuladas é:

```text
PROTHEUS
metadata / dicionário do ambiente
        ↓
serviço/adapter suportado
        ↓
normalização do CRM
        ↓
contrato consumível por backend/UI
```

O CRM pode cachear metadata para performance/resiliência, mas a autoridade permanece no Protheus.

Exemplo validado na simulação:

```text
metadata diz maxLength = 8
→ UI previne 9
→ backend rejeita 9

metadata muda para 10
→ contrato é atualizado
→ CRM passa a aceitar 10
→ sem regra hardcoded maxLength=8 no produto
```

Regras complexas do Protheus não são automaticamente traduzidas para JavaScript; a validação final do domínio ERP continua sob autoridade do Protheus quando houver escrita futura.

---

## 23. Backup e PITR

Produção:

```text
RETENTION TARGET:
14 dias

PITR:
habilitado
```

Staging:

```text
RETENTION TARGET:
7 dias
```

Os valores finais devem ser validados contra o plano comercial escolhido antes de produção.

Target arquitetural:

```text
RPO:
<= 15 min para incidentes cobertos pelo mecanismo

RTO:
<= 4 h target inicial para incidente severo recuperável
```

---

## 24. Disaster recovery

Direção inicial:

```text
DR_LEVEL:
2

infra reconstruível
+
dados restauráveis

MULTI_REGION:
NO
```

Risco residual:

- desastre regional pode exceder os targets normais;
- estratégia multirregional não foi aprovada no P0 por custo/complexidade.

Esse risco é aceito no horizonte piloto, com gatilho de revisão conforme impacto real.

---

## 25. Restore test

Controle obrigatório:

```text
RESTORE TEST:
mensal

DESTINO:
ambiente isolado
```

Evidências esperadas:

- restore concluído;
- schema íntegro;
- migrations coerentes;
- acesso técnico validado;
- smoke de capacidades críticas;
- tempo de recuperação registrado;
- falhas documentadas.

```text
BACKUP SEM RESTORE PROVADO
=
CONTROLE NÃO VERIFICADO
```

---

## 26. Observabilidade

### IDR-010 — Azure Monitor / Application Insights

Instrumentação de código aprovada pelo Tech Lead utiliza OpenTelemetry onde adequado.

Infra recebe e opera sinais como:

- latência API;
- taxa de erro;
- falha/timeout Protheus;
- estado ERP indisponível/stale;
- falhas de autenticação;
- falhas de banco;
- retries;
- revisão/release em execução.

Separação:

```text
APPLICATION LOG
≠
AUDIT LOG
≠
PRODUCT ANALYTICS
```

Não registrar por padrão:

- observação comercial;
- corpo integral de interação;
- segredo;
- payload integral Protheus;
- dado financeiro completo.

---

## 27. Alertas iniciais

Alertas devem existir apenas quando possuem ação.

Sinais candidatos:

- API indisponível;
- taxa de erro material;
- PostgreSQL indisponível;
- falha de deploy;
- túnel VPN indisponível;
- aumento persistente de falhas Protheus;
- backup/restore failure;
- budget excedendo limiar;
- segredo/certificado próximo de expiração quando aplicável.

Todo alerta produtivo precisa de owner e runbook.

---

## 28. Infraestrutura como código

### IDR-009 — Bicep

Motivo:

- Azure é provider único aprovado;
- topologia não exige abstração multi-cloud;
- reduz tooling adicional;
- permite revisão/versionamento dos recursos Azure.

Princípio:

```text
INFRA SOURCE OF TRUTH
→ Git/Bicep
```

Mudança emergencial no portal precisa ser reconciliada com o código posteriormente.

---

## 29. Configuração

Separar:

```text
CONFIGURAÇÃO VERSIONADA
CONFIGURAÇÃO DE AMBIENTE
SECRET
FEATURE FLAG
KILL SWITCH
```

Exemplos de configuração não secreta:

- URL pública;
- identificador de ambiente;
- limites de paginação;
- flags aprovadas.

Exemplos de segredo:

- credencial Protheus;
- chave privada;
- client secret quando necessário.

---

## 30. Cache e broker

No P0:

```text
REDIS:
NO

DEDICATED_BROKER:
NO
```

A primeira necessidade de async durável poderá ser atendida por mecanismo coerente com a stack somente quando workload real aparecer.

Não provisionar serviço sem owner e necessidade atual.

---

## 31. Capacidade inicial

Base atual:

```text
USERS:
≈ 21

CUSTOMERS:
≈ 12k

BROKER:
none

CACHE SERVICE:
none
```

A API de produção começa com capacidade mínima suficiente e autoscaling limitado.

Staging pode utilizar capacidade reduzida.

Não dimensionar para milhões de usuários.

Ordem de evolução:

```text
MEDIR
↓
OTIMIZAR
↓
AUMENTAR CAPACIDADE
↓
ISOLAR GARGALO
↓
REABRIR ARQUITETURA
```

---

## 32. Custos e budgets

Os valores abaixo são **guardrails simulados do caso**, não cotação comercial Azure:

```text
SIMULATED_INFRA_TARGET:
<= R$ 1.500/mês

REVIEW_GATE:
> R$ 2.000/mês

TOTAL_OPERATIONAL_ASSUMPTION_DO_BUSINESS_CASE:
≈ R$ 3.000/mês
```

Antes de contratação real:

```text
ESTIMADO
↓
VALIDADO EM PRICING
↓
MEDIDO EM PILOTO
```

Budgets/alertas de referência:

```text
50%
80%
100%
120%
```

Autoscaling precisa possuir teto para evitar transformar bug em fatura.

---

## 33. Front Door / WAF

Status:

```text
DEFERRED_UNTIL_NEEDED
```

Não existe driver atual que justifique adicionar camada edge/WAF dedicada no P0.

Gatilhos:

- requisito corporativo;
- abuso real;
- necessidade de WAF avançado;
- CDN/edge routing material;
- proteção adicional demonstrada.

---

## 34. Segurança operacional

Controles mínimos:

- TLS;
- MFA para privilegiados;
- least privilege;
- OIDC para CI;
- Managed Identity quando aplicável;
- Key Vault;
- staging/prod isolados;
- banco produtivo sem acesso público irrestrito;
- VPN para Protheus;
- logs minimizados;
- auditabilidade de ações materiais;
- branch/environment protection;
- secret scanning;
- dependency/security checks previstos pelo documento 06;
- acesso de produção temporário/restrito quando possível.

---

## 35. Supply chain operacional

Pipeline deve posteriormente materializar:

- lockfile reproduzível;
- pin de actions quando material;
- dependency review;
- secret scan;
- SAST/security checks apropriados;
- image scan;
- SBOM/provenance quando proporcional;
- artefato por digest;
- workflow permissions mínimas.

---

## 36. Integração Protheus — operação

Para cada ambiente registrar:

- endpoint autorizado;
- rede/rota;
- credencial/identidade;
- timeout;
- retry de leitura;
- freshness;
- observabilidade;
- kill switch;
- owner.

A aplicação precisa conseguir desligar/degradar a integração sem derrubar o domínio comercial próprio.

A integração não pode utilizar acesso direto ao banco Protheus como atalho operacional normal.

---

## 37. Runbooks mínimos planejados

Antes de produção:

```text
RUNBOOK-01 deploy falhou
RUNBOOK-02 rollback de aplicação
RUNBOOK-03 migration falhou/presa
RUNBOOK-04 PostgreSQL indisponível
RUNBOOK-05 restore
RUNBOOK-06 segredo vazado
RUNBOOK-07 VPN/Protheus indisponível
RUNBOOK-08 autenticação Entra indisponível
RUNBOOK-09 budget/custo anômalo
RUNBOOK-10 DNS/TLS
```

Cada runbook precisa de:

- sintoma;
- impacto;
- diagnóstico;
- contenção;
- recuperação;
- validação da jornada;
- owner.

---

## 38. Política de acesso a produção

Produção não é ambiente de debugging rotineiro.

Definir e auditar:

- quem promove release;
- quem executa migrations;
- quem lê logs;
- quem acessa banco;
- quem rotaciona secrets;
- quem altera DNS;
- quem acessa billing;
- quem usa break-glass.

Acesso direto ao banco deve ser excepcional, justificado e auditável.

---

## 39. IDRs consolidados

```text
IDR-001 Azure como cloud principal
IDR-002 Brazil South como região principal
IDR-003 Azure Container Apps para web + API
IDR-004 Microsoft Entra ID single-tenant
IDR-005 Azure Database for PostgreSQL Flexible Server
IDR-006 VNet + VPN Gateway para Protheus on-premises
IDR-007 Azure Key Vault + Managed Identity
IDR-008 GitHub Actions OIDC + Azure Container Registry
IDR-009 Bicep para IaC
IDR-010 Azure Monitor / Application Insights
IDR-011 DR nível 2 + PITR + restore periódico
```

---

## 40. Pendências

### INFRA-PEND-001 — Equipamento/configuração VPN do cliente

**Owner:** TI do cliente.

**Momento:** Fundação antes de prova staging ↔ Protheus.

**Fallback:** reabrir topologia de integração sem expor diretamente o ERP.

### INFRA-PEND-002 — DNS corporativo

**Owner:** TI/infra do cliente.

**Momento:** antes de staging público/production.

### INFRA-PEND-003 — Pricing real

**Owner:** responsável técnico/financeiro.

**Momento:** antes de provisionar produção paga.

### INFRA-PEND-004 — Sizing final PostgreSQL/Container Apps

**Owner:** DevOps/Tech Lead.

**Momento:** Fundação/piloto.

### INFRA-PEND-005 — Contrato exato da API Protheus

**Owner:** TI Protheus + engenharia.

**Momento:** POC/integração de staging.

A pendência não autoriza suposição silenciosa.

---

## 41. Gates da etapa

| Gate | Estado |
| --- | --- |
| INFRA-01 Requisitos rastreáveis | PASS |
| INFRA-02 Providers comparados | PASS |
| INFRA-03 Ownership conceitual definido | PASS |
| INFRA-04 Ambientes definidos | PASS |
| INFRA-05 IAM/secrets definidos | PASS |
| INFRA-06 Network/DNS/TLS definidos com pendências nomeadas | PASS_WITH_OPEN_QUESTIONS |
| INFRA-07 CI/CD definido | PASS |
| INFRA-08 IaC/config definida | PASS |
| INFRA-09 Data services definidos | PASS |
| INFRA-10 Observabilidade definida | PASS |
| INFRA-11 DR/restore definidos | PASS |
| INFRA-12 Segurança operacional definida | PASS |
| INFRA-13 Custo possui guardrail e gate de pricing | PASS_WITH_OPEN_QUESTIONS |
| INFRA-14 Escala por sinal definida | PASS |
| INFRA-15 Runbooks planejados | PASS |
| INFRA-16 Handoff para Fundação possível | PASS |

---

## 42. Readiness

```text
INFRA_PROVIDER_RESEARCH:
COMPLETE_FOR_CASE

PRIMARY_CLOUD:
AZURE

PRIMARY_REGION:
BRAZIL_SOUTH

PROTHEUS_HOSTING:
ON_PREMISES — SIMULATED_CASE_DECISION

INFRA_READINESS:
SUFFICIENT_WITH_OPEN_QUESTIONS

READY_FOR_FOUNDATION:
YES

READY_FOR_CODEX:
NO
```

As perguntas abertas possuem owner e momento de resolução e não impedem o planejamento da Fundação.

---

## 43. Validação da metodologia

A etapa demonstrou corretamente a sequência:

```text
ADR
persistência relacional + boundary Protheus

↓

TDR
PostgreSQL + stack concreta

↓

IDR
Azure PostgreSQL + Container Apps + VPN + Entra + Key Vault
```

Também apareceu um aprendizado importante:

> **A hospedagem do ERP é um dado de Discovery/Pesquisa técnica que pode alterar materialmente a decisão de infraestrutura.**

No caso, foi assumido e depois explicitamente aceito pelo humano que o Protheus seria on-premises apenas para continuidade da simulação.

Se fosse TCloud, a comparação de conectividade e possivelmente de provider precisaria ser reaberta.

Isso reforça:

```text
CANONICAL
≠
IMUTÁVEL
```

Nova evidência real pode exigir reconciliação no documento dono da decisão.

---

## 44. Handoff para Plano de Fundação

O próximo documento deve transformar estas decisões em itens `FND-*` sem provisionar nada automaticamente.

O Plano de Fundação deve ordenar pelo menos:

- ownership e billing;
- governança do repositório;
- workspace/bootstrap da stack;
- identidade GitHub → Azure;
- staging;
- VNet/VPN;
- Key Vault;
- banco staging;
- Container Apps staging;
- observabilidade;
- metadata/API Protheus staging;
- backup/restore;
- production;
- DNS/TLS;
- budgets;
- promoção por digest;
- rollback;
- runbooks;
- gates de readiness.

```text
FOUNDATION_STATUS:
NOT_STARTED

PLANEJADO
≠
AUTORIZADO
≠
EXECUTADO
≠
VERIFICADO
```

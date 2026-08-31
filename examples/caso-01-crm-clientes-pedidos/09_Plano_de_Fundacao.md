---
document_id: CASE-01-DOC-09
title: Plano de Fundação — CRM para gestão de clientes e pedidos
status: canonical
version: 1.0.0
case_id: CASE-01-CRM-CLIENTES-PEDIDOS
methodology_stage: plano-fundacao
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
  - 08_DevOps_e_Infraestrutura.md
next_document: 10_Backlog_Canonico_Rastreabilidade_e_Plano_de_Entrega.md
foundation_readiness: SUFFICIENT
foundation_status: PLANNED
ready_for_codex: false
---

# Plano de Fundação — CRM para gestão de clientes e pedidos

## 1. Propósito

Este documento transforma a arquitetura, a stack e a infraestrutura aprovadas do Caso 01 em uma sequência ordenada, rastreável, reversível e verificável de preparação da base do projeto.

A pergunta central desta etapa é:

> **Qual é a menor sequência segura de ações necessárias para transformar as decisões aprovadas em uma fundação reproduzível, observável, recuperável e pronta para receber desenvolvimento funcional sem depender de conhecimento oral, contas improvisadas, segredos escondidos ou infraestrutura não provada?**

A fundação não implementa funcionalidades do CRM.

Ela cria e prova as capacidades mínimas para que o desenvolvimento funcional posterior possa acontecer com segurança.

```text
PLANEJADO
!=
AUTORIZADO
!=
EXECUTADO
!=
VERIFICADO
```

A canonização deste documento coloca todos os itens `FND-*` em `PLANNED`.

Ela não autoriza criação de recursos pagos, produção, DNS, segredos, VPN, credenciais, deploy público, carga de dados reais ou qualquer outra ação material.

---

## 2. Base recebida

A fundação herda, sem rediscutir silenciosamente:

- arquitetura inicial em monólito modular;
- aplicação web responsiva para desktop e mobile;
- TypeScript/Node, React/Vite e NestJS como direção tecnológica;
- PostgreSQL como engine relacional transacional;
- Azure como cloud da simulação;
- Brazil South como região principal da simulação;
- Azure Container Apps para web e API;
- Azure Database for PostgreSQL Flexible Server;
- Microsoft Entra ID como identity provider do cenário;
- Azure Key Vault + Managed Identity;
- GitHub Actions com OIDC para Azure;
- Azure Container Registry;
- Bicep como IaC;
- Azure Monitor/Application Insights como backend operacional de observabilidade;
- Protheus on-premises como premissa simulada aprovada para o Caso 01;
- VNet + VPN site-to-site como direção de conectividade privada com o ERP;
- Protheus como autoridade para cliente formal, pedido, faturamento, estoque, histórico transacional e informação financeira ERP;
- CRM como autoridade para prospect, histórico comercial, próxima ação, carteira, transferências e demais dados próprios;
- metadata de campos Protheus consumida do ambiente ERP, sem dicionário Protheus canônico duplicado no CRM;
- alvo arquitetural inicial de RPO <= 15 minutos e RTO <= 4 horas para os dados canônicos do CRM em incidentes compatíveis com o mecanismo escolhido;
- DR inicial nível 2, sem multi-região ativa;
- produção isolada de staging;
- build once / promote many;
- dados sintéticos por padrão fora de produção.

---

## 3. Princípio operacional da fundação

> **Fundação é o conjunto mínimo de capacidades que permite alterar, testar, entregar, observar e recuperar o sistema com segurança.**

Logo:

```text
REPOSITÓRIO CRIADO
!=
FUNDAÇÃO PRONTA
```

```text
DEPLOY FUNCIONOU UMA VEZ
!=
PIPELINE PROVADO
```

```text
BACKUP HABILITADO
!=
RECUPERAÇÃO PROVADA
```

Cada item de fundação precisa produzir uma evidência objetiva.

---

## 4. Status permitidos

Os itens `FND-*` poderão usar os seguintes estados durante execução futura:

```text
PLANNED
BLOCKED
READY
AUTHORIZED
IN_PROGRESS
IMPLEMENTED
VERIFIED
FAILED
ROLLED_BACK
SUPERSEDED
CANCELLED
```

Neste documento, todos começam em:

```text
PLANNED
```

---

## 5. Taxonomia usada

As categorias utilizadas são:

- `ORG` — ownership e contas;
- `CST` — billing, budgets e custo;
- `GIT` — repositório e governança;
- `WRK` — workspace e toolchain;
- `IAM` — identidade e acesso;
- `ENV` — ambientes;
- `SEC` — segredos e segurança;
- `NET` — rede;
- `DAT` — dados e migrations;
- `CICD` — build, CI e promoção;
- `OBS` — observabilidade;
- `EXT` — integrações externas;
- `BKP` — backup e restore;
- `REL` — release e rollback;
- `OPS` — operação e runbooks;
- `DOC` — documentação e handoff.

A categoria é metadado. O identificador estável continua sendo `FND-xxx`.

---

## 6. Inventário canônico de fundação

### FND-001 — Definir ownership organizacional

**Categoria:** ORG  
**Ambiente:** global  
**Status inicial:** PLANNED

**Objetivo:** garantir que ownership técnico, financeiro, operacional e de recuperação não dependa de uma única pessoa ou conhecimento oral.

**Origem:** Infra — contas, ownership e acesso.

**Dependências:** nenhuma.

**Resultado esperado:**

- owners humanos definidos;
- responsáveis por billing, GitHub, Azure, DNS, Entra ID, Protheus e produção definidos;
- contas de função identificadas quando aplicável;
- MFA e recuperação planejados;
- break-glass previsto quando necessário.

**Evidência:** matriz de ownership revisada e aprovada.

**Parar se:** não existir entidade responsável capaz de assumir ownership dos ativos críticos.

---

### FND-002 — Preparar billing, budget e alertas Azure

**Categoria:** CST  
**Ambiente:** global  
**Status inicial:** PLANNED

**Objetivo:** impedir criação de infraestrutura sem visibilidade financeira e owner.

**Dependências:** FND-001.

**Resultado esperado:**

- subscription/billing sob ownership correto;
- budget inicial configurado;
- alertas progressivos definidos;
- centro de custo ou responsável registrado.

**Evidência:** budget e alertas visíveis aos owners aprovados.

**Custo:** pode ativar cobrança; exige autorização humana explícita antes da execução real.

---

### FND-003 — Criar repositório operacional do CRM

**Categoria:** GIT  
**Ambiente:** global  
**Status inicial:** PLANNED

**Objetivo:** estabelecer uma fonte versionada e auditável para aplicação, contratos, IaC e documentação operacional.

**Dependências:** FND-001.

**Resultado esperado:** repositório sob ownership organizacional adequado.

**Evidência:** owners aprovados conseguem administrar o repositório; não existe dependência de conta pessoal isolada.

---

### FND-004 — Aplicar governança da branch principal

**Categoria:** GIT  
**Ambiente:** global  
**Status inicial:** PLANNED

**Dependências:** FND-003.

**Resultado esperado:**

- push direto bloqueado;
- force push bloqueado;
- PR obrigatório;
- checks obrigatórios suportados;
- revisão humana conforme política de risco;
- SHA revisado e conversas bloqueantes tratáveis.

**Evidência:** tentativa controlada de bypass falha.

---

### FND-005 — Inicializar toolchain e versões aprovadas

**Categoria:** WRK  
**Ambiente:** local/global  
**Status inicial:** PLANNED

**Dependências:** FND-003.

**Resultado esperado:**

- runtime e package manager aprovados fixados;
- versões diretas reconfirmadas no bootstrap;
- lockfile reproduzível;
- nenhuma instalação dependente de `latest` como política.

**Evidência:** instalação limpa em ambiente novo produz resultado reproduzível.

**Parar se:** versões atuais violarem compatibilidade canônica ou hard constraint.

---

### FND-006 — Criar skeleton compilável de web, API e packages

**Categoria:** WRK  
**Ambiente:** local  
**Status inicial:** PLANNED

**Dependências:** FND-005.

**Resultado esperado:**

```text
apps/
  web/
  api/
packages/
  ui/
  contracts/
  config/
```

ou estrutura equivalente aprovada no bootstrap, preservando boundaries.

Nenhuma feature de CRM é implementada aqui.

**Evidência:** web e API compilam, iniciam localmente e expõem apenas probes técnicos necessários.

---

### FND-007 — Provar CI mínimo em pull request

**Categoria:** CICD  
**Ambiente:** global  
**Status inicial:** PLANNED

**Dependências:** FND-004, FND-006.

**Resultado esperado:** pipeline executa, conforme aplicável:

- format;
- lint;
- typecheck;
- testes unitários mínimos;
- build;
- scans básicos previstos pela política.

**Evidência:** PR controlado passa e PR deliberadamente quebrado falha no gate correto.

---

### FND-008 — Provar identidade OIDC GitHub → Azure staging

**Categoria:** IAM  
**Ambiente:** staging  
**Status inicial:** PLANNED

**Dependências:** FND-002, FND-007.

**Resultado esperado:** GitHub Actions obtém identidade temporária para staging sem secret Azure administrativo permanente no repositório.

**Evidência:** workflow autentica por OIDC com escopo mínimo.

**Parar se:** a solução exigir credencial administrativa permanente quando existir alternativa federada aprovada.

---

### FND-009 — Criar ambiente Azure de staging

**Categoria:** ENV  
**Ambiente:** staging  
**Status inicial:** PLANNED

**Dependências:** FND-002, FND-008.

**Resultado esperado:** recursos de staging ficam isolados, identificáveis e submetidos ao budget aprovado.

**Dados:** sintéticos por padrão.

**Evidência:** inventário de recursos e tags/ownership conferidos.

---

### FND-010 — Configurar Key Vault e Managed Identity de staging

**Categoria:** SEC  
**Ambiente:** staging  
**Status inicial:** PLANNED

**Dependências:** FND-009.

**Resultado esperado:** workloads de staging acessam somente os secrets necessários por identidade gerenciada.

**Evidência:** acesso permitido funciona; secret não autorizado é negado.

---

### FND-011 — Criar e provar VNet de staging

**Categoria:** NET  
**Ambiente:** staging  
**Status inicial:** PLANNED

**Dependências:** FND-009.

**Resultado esperado:** topologia de rede necessária aos workloads e futura VPN existe sem exposição indevida do ERP.

**Evidência:** subnets/rotas/associações relevantes inventariadas e testadas.

---

### FND-012 — Provisionar PostgreSQL de staging

**Categoria:** DAT  
**Ambiente:** staging  
**Status inicial:** PLANNED

**Dependências:** FND-009, FND-011.

**Resultado esperado:** PostgreSQL staging disponível com acesso restrito e configuração compatível com migrations e observabilidade necessárias.

**Dados:** somente sintéticos/controlados.

**Evidência:** conexão segura + smoke transacional.

---

### FND-013 — Provar mecanismo de migrations

**Categoria:** DAT  
**Ambiente:** staging/local  
**Status inicial:** PLANNED

**Dependências:** FND-006, FND-012.

**Objetivo:** validar a decisão tecnológica de acesso a dados e migrations antes de modelagem funcional extensa.

**Resultado esperado:**

- migration inicial;
- evolução compatível;
- constraint;
- transação;
- rollback/forward-fix documentável;
- concorrência/idempotência tecnicamente representáveis.

**Evidência:** POC de persistência aprovada.

**Parar se:** a camada escolhida impedir requisito arquitetural relevante; reabrir TDR correspondente.

---

### FND-014 — Criar Container Apps de staging

**Categoria:** ENV  
**Ambiente:** staging  
**Status inicial:** PLANNED

**Dependências:** FND-009, FND-010, FND-011.

**Resultado esperado:** workloads técnicos de web e API executam com identities, rede e configuração de staging.

**Evidência:** health/build-info controlados respondem conforme esperado.

---

### FND-015 — Provar build OCI e publicação no ACR por digest

**Categoria:** CICD  
**Ambiente:** staging/global  
**Status inicial:** PLANNED

**Dependências:** FND-007, FND-009.

**Resultado esperado:** artefatos de web/API ficam associados ao source SHA e digest imutável.

**Evidência:** registry contém artefato rastreável ao commit de origem.

---

### FND-016 — Provar deploy controlado em staging

**Categoria:** CICD  
**Ambiente:** staging  
**Status inicial:** PLANNED

**Dependências:** FND-014, FND-015.

**Resultado esperado:** mesmo digest produzido no pipeline é executado em staging.

**Evidência:** release metadata mostra source SHA + digest + revisão implantada.

---

### FND-017 — Provar observabilidade mínima de staging

**Categoria:** OBS  
**Ambiente:** staging  
**Status inicial:** PLANNED

**Dependências:** FND-014, FND-016.

**Resultado esperado:** request técnico pode ser correlacionado por logs/métricas/traces sem transportar conteúdo comercial sensível.

**Evidência:** sinal técnico reproduzível visível no backend operacional.

---

### FND-018 — Estabelecer VPN Azure ↔ rede corporativa

**Categoria:** EXT/NET  
**Ambiente:** staging/hybrid  
**Status inicial:** PLANNED

**Dependências:** FND-011.

**Objetivo:** provar a premissa simulada de integração privada com Protheus on-premises.

**Resultado esperado:** túnel IPsec e rotas aprovadas permitem comunicação somente com alvos autorizados.

**Evidência:** conectividade controlada de staging até a rede de homologação.

**Parar se:** política/rede do cliente inviabilizar VPN; reabrir IDR de conectividade antes de improvisar exposição pública.

---

### FND-019 — Provar acesso exclusivo ao Protheus de homologação

**Categoria:** EXT  
**Ambiente:** staging  
**Status inicial:** PLANNED

**Dependências:** FND-018.

**Resultado esperado:** CRM staging alcança apenas o endpoint Protheus de homologação autorizado.

**Evidência:** chamada controlada bem-sucedida e prova de que credenciais/destinos de produção não são reutilizados.

---

### FND-020 — Provar contrato de metadata Protheus

**Categoria:** EXT  
**Ambiente:** staging/homologação  
**Status inicial:** PLANNED

**Dependências:** FND-019.

**Objetivo:** comprovar que o CRM consome metadados do ambiente Protheus sem manter um dicionário canônico duplicado.

**Resultado esperado:** adapter consegue obter e normalizar, quando aplicável:

- campo;
- tipo;
- tamanho;
- decimal;
- obrigatoriedade;
- picture/formato simples;
- opções simples;
- indicação de validação adicional.

**Evidência:** contrato sanitizado capturado e validado.

**Parar se:** única alternativa exigir leitura direta frágil de tabelas internas sem suporte; reabrir integração/TDR.

---

### FND-021 — Provar validação orientada por metadata

**Categoria:** EXT  
**Ambiente:** staging/homologação  
**Status inicial:** PLANNED

**Dependências:** FND-020.

**Cenário de prova:**

```text
metadata maxLength = 8
→ valor com 8 é aceito pela validação preventiva
→ valor com 9 é rejeitado

metadata controladamente alterado para maxLength = 10
→ CRM reconhece a mudança
→ valor com 10 passa sem alterar regra hardcoded do CRM
```

**Evidência:** teste reproduzível.

**Invariante:** Protheus continua sendo autoridade final sobre suas regras; metadata-driven validation não significa reimplementar toda lógica AdvPL no CRM.

---

### FND-022 — Provar contratos read-only de contexto ERP

**Categoria:** EXT  
**Ambiente:** staging/homologação  
**Status inicial:** PLANNED

**Dependências:** FND-019.

**Resultado esperado:** adapter normaliza pelo menos os contratos necessários do P0 para cliente formal e contexto de pedido; estoque/financeiro entram apenas na medida aprovada e testável.

**Evidência:** contract tests com payloads sanitizados/controlados.

**Invariante:** payload Protheus não vira entidade interna diretamente.

---

### FND-023 — Provar degradação diante de indisponibilidade do Protheus

**Categoria:** EXT/OPS  
**Ambiente:** staging  
**Status inicial:** PLANNED

**Dependências:** FND-016, FND-019.

**Resultado esperado:** quando Protheus fica indisponível:

- core CRM continua operacional;
- contexto ERP entra em estado indisponível/stale apropriado;
- nenhum dado antigo é apresentado como confirmação atual;
- observabilidade registra a falha sem payload sensível.

**Evidência:** teste de falha controlada.

---

### FND-024 — Provar backup/PITR de staging

**Categoria:** BKP  
**Ambiente:** staging  
**Status inicial:** PLANNED

**Dependências:** FND-012.

**Resultado esperado:** política de backup/PITR configurada conforme ambiente e inventariada.

**Evidência:** ponto de recuperação disponível.

**Observação:** existência de backup ainda não conclui o gate de recuperação.

---

### FND-025 — Executar restore isolado de prova

**Categoria:** BKP  
**Ambiente:** staging/isolado  
**Status inicial:** PLANNED

**Dependências:** FND-024.

**Resultado esperado:** banco restaurado em destino isolado e validado por smoke técnico.

**Evidência:** tempo medido, integridade básica, schema e conectividade verificados.

---

### FND-026 — Integrar Microsoft Entra ID em staging

**Categoria:** IAM  
**Ambiente:** staging  
**Status inicial:** PLANNED

**Dependências:** FND-014.

**Resultado esperado:** login, logout e sessão funcionam com tenant simulado/corporativo aprovado, sem transferir autorização de domínio para o IdP.

**Evidência:** fluxo OIDC/PKCE e sessão backend aprovados.

---

### FND-027 — Provar baseline de autorização server-side

**Categoria:** SEC  
**Ambiente:** staging  
**Status inicial:** PLANNED

**Dependências:** FND-026.

**Resultado esperado:** endpoint protegido nega acesso sem depender de botão oculto ou regra apenas no frontend.

**Evidência:** teste automatizado de autorização horizontal/role/resource.

---

### FND-028 — Provar rollback de aplicação por digest

**Categoria:** REL  
**Ambiente:** staging  
**Status inicial:** PLANNED

**Dependências:** FND-015, FND-016.

**Resultado esperado:** revisão anterior conhecida pode ser restaurada sem rebuild diferente.

**Evidência:** rollback controlado concluído e smoke verde.

---

### FND-029 — Provar política expand → migrate → validate → contract

**Categoria:** REL/DAT  
**Ambiente:** staging  
**Status inicial:** PLANNED

**Dependências:** FND-013, FND-028.

**Resultado esperado:** evolução de schema compatível com aplicação anterior/posterior é demonstrada sem passo destrutivo único e irreversível.

**Evidência:** migration de laboratório executada com compatibilidade e validação.

---

### FND-030 — Produzir runbooks mínimos de staging

**Categoria:** OPS  
**Ambiente:** staging  
**Status inicial:** PLANNED

**Dependências:** FND-017, FND-023, FND-025, FND-028.

**Runbooks mínimos:**

- deploy falhou;
- rollback;
- migration presa;
- PostgreSQL indisponível;
- Protheus indisponível;
- VPN indisponível;
- restore;
- segredo vazado;
- custo/quota anômala.

**Evidência:** cada runbook possui sintoma, impacto, verificação, contenção, validação e owner.

---

## 7. Gate de staging antes de produção

A criação da fundação produtiva é bloqueada até que o recorte de staging necessário esteja verificado e exista aprovação humana explícita.

```text
FND-001 → ... → FND-030
        ↓
STAGING FOUNDATION VERIFIED
        ↓
HUMAN APPROVAL
        ↓
FND-031+
```

Esse gate é obrigatório mesmo em futura execução automatizada.

---

### FND-031 — Criar ambiente isolado de production

**Categoria:** ENV  
**Ambiente:** production  
**Status inicial:** PLANNED

**Dependências:** gates de staging + autorização humana explícita.

**Resultado esperado:** produção possui recursos e ownership próprios, sem compartilhar banco, secrets ou credenciais sensíveis de staging.

**Evidência:** inventário produtivo separado.

**Ação sensível:** cria recursos pagos/reais; nunca autorizada apenas pela existência deste plano.

---

### FND-032 — Configurar OIDC e workload identity de production

**Categoria:** IAM  
**Ambiente:** production  
**Status inicial:** PLANNED

**Dependências:** FND-031.

**Resultado esperado:** identidade de CI/produção separada da de staging e com least privilege.

**Evidência:** token temporário e escopo mínimo comprovados.

---

### FND-033 — Configurar Key Vault e Managed Identity de production

**Categoria:** SEC  
**Ambiente:** production  
**Status inicial:** PLANNED

**Dependências:** FND-031, FND-032.

**Resultado esperado:** secrets de produção ficam isolados e acessíveis apenas pelas identidades autorizadas.

**Evidência:** acesso seletivo comprovado.

---

### FND-034 — Provar rede/VPN production → Protheus production

**Categoria:** NET/EXT  
**Ambiente:** production  
**Status inicial:** PLANNED

**Dependências:** FND-031 e prova correspondente em staging.

**Resultado esperado:** conectividade privada com Protheus produtivo, sem reutilizar credencial ou rota de homologação por conveniência.

**Evidência:** teste autorizado e auditável.

---

### FND-035 — Provisionar PostgreSQL de production

**Categoria:** DAT  
**Ambiente:** production  
**Status inicial:** PLANNED

**Dependências:** FND-031.

**Resultado esperado:** banco produtivo isolado com PITR/backup compatível com a política aprovada.

**Evidência:** configuração revisada, sem carga de dados comerciais antes de autorização específica.

---

### FND-036 — Criar workloads production

**Categoria:** ENV  
**Ambiente:** production  
**Status inicial:** PLANNED

**Dependências:** FND-031, FND-032, FND-033, FND-035.

**Resultado esperado:** web/API produtivos executam apenas probes técnicos e baseline necessária antes de features reais.

**Evidência:** health/build-info e identity operacional aprovados.

---

### FND-037 — Configurar observabilidade e budgets de production

**Categoria:** OBS/CST  
**Ambiente:** production  
**Status inicial:** PLANNED

**Dependências:** FND-036.

**Resultado esperado:** produção não recebe tráfego real sem sinais mínimos, owner e proteção financeira.

**Evidência:** logs/métricas/alertas/budget visíveis aos owners.

---

### FND-038 — Provar promoção do mesmo digest staging → production

**Categoria:** REL  
**Ambiente:** production  
**Status inicial:** PLANNED

**Dependências:** FND-015, FND-036.

**Resultado esperado:** produção executa o mesmo artefato previamente testado, variando apenas configuração/segredos permitidos.

**Evidência:** source SHA e artifact digest coincidem com o promovido.

---

### FND-039 — Provar rollback produtivo controlado

**Categoria:** REL  
**Ambiente:** production  
**Status inicial:** PLANNED

**Dependências:** FND-038.

**Resultado esperado:** revisão anterior pode ser restaurada antes de introduzir dados reais críticos.

**Evidência:** rollback + smoke técnico.

---

### FND-040 — Configurar DNS e TLS produtivos

**Categoria:** OPS/NET  
**Ambiente:** production  
**Status inicial:** PLANNED

**Dependências:** FND-036 + autorização humana para alteração de DNS.

**Resultado esperado:** domínio produtivo aprovado resolve para a aplicação com TLS válido.

**Evidência:** resolução, certificado e redirect/header básicos validados.

---

### FND-041 — Provar restore em cenário production-like

**Categoria:** BKP  
**Ambiente:** isolado/production-like  
**Status inicial:** PLANNED

**Dependências:** FND-035.

**Resultado esperado:** restaurar backup/PITR em ambiente isolado e medir RPO/RTO operacionalmente atingíveis.

**Evidência:** relatório de restore com tempos e limitações.

**Parar se:** targets arquiteturais não forem atingíveis; reabrir Infra/Arquitetura em vez de declarar sucesso.

---

### FND-042 — Consolidar documentação operacional da fundação

**Categoria:** DOC  
**Ambiente:** global  
**Status inicial:** PLANNED

**Dependências:** todos os gates materiais necessários à fundação.

**Resultado esperado:** nenhum procedimento crítico depende exclusivamente de conhecimento oral.

**Conteúdo mínimo:**

- ownership;
- acessos;
- comandos canônicos;
- ambientes;
- endpoints;
- políticas de secrets;
- release/rollback;
- backup/restore;
- observabilidade;
- VPN/Protheus;
- budgets;
- runbooks;
- pendências.

**Evidência:** documentação revisada por responsável diferente do autor quando possível.

---

## 8. Grafo de dependências resumido

```text
FND-001 Ownership
├── FND-002 Billing/Budget
│   └── FND-008 OIDC CI→Azure
│       └── FND-009 Staging
│           ├── FND-010 Key Vault
│           ├── FND-011 VNet
│           │   ├── FND-012 PostgreSQL
│           │   │   ├── FND-013 Migrations
│           │   │   ├── FND-024 Backup
│           │   │   │   └── FND-025 Restore
│           │   └── FND-018 VPN
│           │       └── FND-019 Protheus homologação
│           │           ├── FND-020 Metadata
│           │           │   └── FND-021 Metadata validation
│           │           ├── FND-022 Read contracts
│           │           └── FND-023 Degradação
│           └── FND-014 Container Apps
│               ├── FND-017 Observabilidade
│               └── FND-026 Entra ID
│                   └── FND-027 Authz baseline
└── FND-003 Repositório
    ├── FND-004 Proteção
    └── FND-005 Toolchain
        └── FND-006 Skeleton
            └── FND-007 CI
                └── FND-015 Build/ACR
                    └── FND-016 Deploy staging
                        └── FND-028 Rollback
                            └── FND-029 Migration lifecycle
```

Após os gates necessários de staging:

```text
HUMAN APPROVAL
↓
FND-031 Production
├── FND-032 OIDC prod
├── FND-033 Key Vault prod
├── FND-034 VPN prod
├── FND-035 PostgreSQL prod
│   └── FND-041 Restore production-like
└── FND-036 Workloads prod
    ├── FND-037 Observability/Budget
    ├── FND-038 Promotion
    │   └── FND-039 Rollback prod
    └── FND-040 DNS/TLS
```

---

## 9. Caminho crítico

O caminho crítico aproximado da fundação é:

```text
OWNERSHIP
→ REPOSITÓRIO
→ WORKSPACE
→ CI
→ BILLING/AZURE
→ OIDC CI→AZURE
→ STAGING
→ VNET
→ KEY VAULT
→ POSTGRESQL
→ CONTAINER APPS
→ BUILD/DEPLOY
→ VPN
→ PROTHEUS HOMOLOGAÇÃO
→ METADATA/READ CONTRACT
→ DEGRADAÇÃO
→ BACKUP/RESTORE
→ STAGING FOUNDATION VERIFIED
→ HUMAN GATE
→ PRODUCTION FOUNDATION
```

Itens de observabilidade, documentação e runbooks podem avançar em paralelo quando suas dependências mínimas estiverem satisfeitas.

---

## 10. Gate especial — Protheus

### FOUNDATION-GATE-PROTHEUS

A fundação não pode tratar a integração Protheus como pronta até provar:

```text
NETWORK
✓ Azure alcança homologação pela topologia aprovada

BOUNDARY
✓ browser não acessa Protheus diretamente
✓ integração passa pelo adapter aprovado

METADATA
✓ CRM obtém metadata necessária do ambiente Protheus

VALIDATION
✓ metadata simples consegue dirigir validação preventiva

READ CONTRACT
✓ contratos P0 são normalizáveis

FAILURE
✓ indisponibilidade do ERP não derruba o core CRM

AUTHORITY
✓ CRM não se torna segunda autoridade dos dados ERP
```

Falha material neste gate reabre a decisão responsável em `08`, `Visao_do_Tech_Lead.md` ou `07_Engenharia_e_Arquitetura.md`.

---

## 11. Gate especial — autoridade de dados

### FOUNDATION-GATE-DATA-AUTHORITY

O PostgreSQL próprio do CRM existe para o domínio cuja autoridade pertence ao CRM.

A fundação precisa preservar:

```text
CRM DATABASE
prospect
histórico comercial
próxima ação
portfolio ownership
transferência
auditabilidade CRM
estado técnico próprio
idempotência
outros dados explicitamente do CRM
```

Enquanto:

```text
PROTHEUS
cliente formal
pedido
faturamento
estoque
financeiro
metadata ERP
```

continua autoridade dos dados correspondentes.

Não é permitido usar a existência do PostgreSQL como justificativa automática para replicar SA1, SC5, SC6 ou outras tabelas como segunda verdade canônica.

Qualquer materialização/snapshot futuro precisa declarar:

- por que persiste;
- autoridade;
- freshness;
- retenção;
- reconstruibilidade;
- segurança;
- impacto de indisponibilidade.

---

## 12. Gate de custo

### FOUNDATION-GATE-COST

Antes de criar produção, executar projeção atualizada da infraestrutura aprovada.

Incluir no mínimo:

- Container Apps;
- PostgreSQL;
- VPN Gateway;
- ACR;
- Key Vault;
- observabilidade;
- backup;
- networking.

Guardrails simulados herdados:

```text
TARGET INFRA NORMAL
<= R$ 1.500/mês

REVIEW GATE
> R$ 2.000/mês
```

Se a estimativa real exceder materialmente a faixa aprovada, parar e reabrir a decisão correspondente. Não esconder o problema escolhendo sizing incompatível com os requisitos.

---

## 13. Dados permitidos durante a fundação

### Local / PR / staging

Permitido por padrão:

- dados sintéticos;
- fixtures controladas;
- payloads sanitizados;
- dados de homologação autorizados quando necessários à prova.

Não permitido por conveniência:

- dump integral de produção;
- histórico comercial real;
- credenciais produtivas;
- conteúdo financeiro real;
- segredos em prompts/logs/screenshots.

### Production

Dados reais somente após autorização específica e quando a fundação correspondente estiver verificada.

---

## 14. Fora do escopo da fundação

A fundação não implementa:

- carteira comercial funcional;
- timeline de cliente;
- próxima ação funcional;
- cadastro funcional de prospect;
- tela Hoje;
- gestão comercial;
- regras de atenção;
- experiência de pedido;
- dashboards de produto;
- rollout para os 18 vendedores.

Pode implementar apenas artefatos técnicos mínimos de prova como:

```text
/health
/build-info
probe de banco
probe de metadata
fake de integração
smokes técnicos
```

quando necessários para validar a base.

---

## 15. Condições globais de parada

Parar e pedir decisão humana/reconciliação quando:

- for necessário criar custo material não aprovado;
- produção precisar ser criada antes do gate de staging;
- VPN exigir exposição pública improvisada do Protheus;
- metadata não puder ser obtida de forma suportável;
- integração exigir acesso direto frágil a tabela interna do ERP;
- provider/stack não atender RPO/RTO aprovado;
- decisão tecnológica não passar POC obrigatória;
- autenticação exigir enfraquecer autorização do CRM;
- segredo precisar ser colocado em repositório/bundle;
- dado real precisar ser copiado para staging sem autorização;
- nova evidência contradizer ADR/TDR/IDR canônico;
- custo ultrapassar materialmente o guardrail sem revisão.

---

## 16. Definition of Foundation Ready

A fundação futura só poderá ser considerada `VERIFIED` quando existirem evidências suficientes de:

```text
REPO GOVERNADO
+
WORKSPACE REPRODUZÍVEL
+
CI PROVADO
+
OIDC SEM SECRET CLOUD PERMANENTE
+
STAGING FUNCIONAL
+
BANCO + MIGRATIONS
+
OBSERVABILIDADE
+
VPN PROTHEUS
+
METADATA CONTRACT
+
VALIDAÇÃO METADATA-DRIVEN
+
FAILURE MODE PROTHEUS PROVADO
+
BACKUP + RESTORE
+
ROLLBACK
+
PRODUCTION ISOLATION
+
BUDGETS
+
RUNBOOKS
+
DOCUMENTAÇÃO
```

`site abriu` ou `deploy retornou 200` não é evidência suficiente.

---

## 17. Relação com o Backlog Canônico

Todos os `FND-*` deste documento são candidatos obrigatórios ao inventário do Backlog Canônico.

O documento 10 deverá:

- preservar os IDs `FND-*`;
- reconciliar dependências com itens de produto;
- distinguir fundação necessária antes de feature da fundação que pode evoluir em paralelo;
- não transformar `PLANNED` em `AUTHORIZED`;
- criar a ordem global de execução;
- preservar gates humanos para ações sensíveis.

---

## 18. Validação da metodologia

A etapa 08 definiu decisões como:

```text
IDR-006
VNet + VPN Gateway
```

O Plano de Fundação transformou isso em sequência verificável:

```text
FND-011
provar VNet
↓
FND-018
provar VPN
↓
FND-019
provar homologação
↓
FND-023
provar degradação
```

Da mesma forma, a descoberta sobre metadata Protheus deixou de ser apenas recomendação arquitetural e passou a ter uma prova operacional explícita em `FND-020` e `FND-021`.

A fronteira metodológica permanece válida:

```text
08 DEVOPS / INFRA
qual infraestrutura foi escolhida

09 FUNDAÇÃO
em qual ordem criá-la e como prová-la

10 BACKLOG CANÔNICO
como integrar fundação + produto + entrega
```

Resultado:

```text
FOUNDATION_METHOD_VALIDATION: PASS

PROVISIONING_EXECUTED: NO
PRODUCT_FEATURE_IMPLEMENTED: NO

FND_INVENTORY: DEFINED
DEPENDENCY_GRAPH: DEFINED
CRITICAL_PATH: DEFINED
PROTHEUS_GATE: DEFINED
DATA_AUTHORITY_GATE: DEFINED
STAGING_TO_PRODUCTION_GATE: DEFINED
COST_GATE: DEFINED

FOUNDATION_READINESS: SUFFICIENT
FOUNDATION_STATUS: PLANNED
READY_FOR_CODEX: NO
```

---

## 19. Handoff

```text
FOUNDATION_EXECUTION: COMPLETE_AS_PLANNING
CLIENT_REVIEW: APPROVED_FOR_SIMULATION
FOUNDATION_STATUS: PLANNED
FOUNDATION_READINESS: SUFFICIENT
PROVISIONING_EXECUTED: NO
READY_FOR_CODEX: NO
NEXT_STAGE: 10 — Backlog Canônico, Rastreabilidade e Plano de Entrega
```

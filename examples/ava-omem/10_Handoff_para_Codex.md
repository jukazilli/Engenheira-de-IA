# Handoff para o Codex — AVA OMEM

> **Objetivo:** mostrar a passagem do projeto documentado no ChatGPT para o ambiente de execução.

## Pré-condições

Antes de abrir o Codex:

- todos os documentos do exemplo foram aprovados;
- o repositório do projeto real já contém os `.md` canônicos;
- o repositório foi clonado ou atualizado na máquina local;
- o Codex está aberto na raiz do projeto;
- a Visão do Tech Lead foi aprovada e reconciliada com a Infraestrutura;
- ainda não existe permissão para escolher stack/provider alternativo, criar recurso pago ou manipular credenciais humanas sem gate.

## Primeiro comando no Codex

```text
Consuma integralmente a documentação canônica deste projeto antes de alterar qualquer arquivo.

Leia os documentos na ordem e precedência definidas pelo processo, com atenção especial a:

- 06_Tecnicas_de_Desenvolvimento.md
- 07_Engenharia_e_Arquitetura.md
- Visao_do_Tech_Lead.md
- Infraestrutura_e_Plano_de_Fundacao.md
- 08_Backlog_Canonico_Rastreabilidade_e_Plano_de_Entrega.md
- 09_Matriz_Operacional_de_Rastreabilidade.md

Leia também todos os documentos anteriores e qualquer documentação derivada existente.

Não implemente nada ainda.

Primeiro responda somente com:

DOCUMENTS_CONSUMED
DOCUMENT_CONSISTENCY
TECH_STACK_STATUS
CURRENT_FOUNDATION_STATUS
BACKLOG_STATUS
NEXT_EXECUTABLE_ITEM
BLOCKERS
PROPOSED_FIRST_SLICE

Não marque item como entregue sem evidência. Não escolha silenciosamente stack, biblioteca ou infraestrutura diferente da aprovada. Não peça senhas, tokens, chaves privadas ou secrets pelo chat.
```

## Resposta simulada do Codex

```text
DOCUMENTS_CONSUMED: complete
DOCUMENT_CONSISTENCY: consistent for initial execution
TECH_STACK_STATUS: canonical; compatible with approved infrastructure
CURRENT_FOUNDATION_STATUS: not_started
BACKLOG_STATUS: canonical; first milestone M0
NEXT_EXECUTABLE_ITEM: FND-001
BLOCKERS: none for repository skeleton
PROPOSED_FIRST_SLICE: FND-001 — create the architecture-approved repository skeleton only
```

## Autorização humana

### Usuário

Consuma o backlog para iniciarmos o desenvolvimento da aplicação. Comece pelo `FND-001` e siga somente pelos itens FND elegíveis. Faça commits pequenos, execute os gates definidos e mantenha a matriz consistente.

## Execução esperada — FND-001

O Codex deve:

```text
reler FND-001
   ↓
consultar Documento 07
   ↓
inspecionar repo atual
   ↓
criar somente o esqueleto estrutural previsto pela arquitetura
   ↓
não instalar stack/toolchain ainda
   ↓
revisar boundaries e árvore
   ↓
auto-revisar diff
   ↓
atualizar rastreabilidade
   ↓
registrar evidência
```

A Visão do Tech Lead já existe, mas a materialização de Node, pnpm, TypeScript, React/Vite e Fastify acontece no **FND-002**, conforme o backlog. Isso evita misturar a decisão estrutural do repositório com a instalação da stack.

Ele não deve avançar para `FND-005`, por exemplo, apenas porque consegue abrir o painel do provider. Dependências do backlog continuam governando a execução.

Também não pode substituir pnpm, React/Vite, Fastify ou outra decisão canônica apenas porque conhece uma alternativa.

## Exemplo de evidência após FND-001

```text
FND-001
Implementation:
- apps/web/
- apps/api/
- packages/domain/
- packages/contracts/
- infra/
- tooling/

Checks:
- repository tree review
- architecture conformance review

Evidence:
- commit <sha>
- diff <ref>

Status: Validated / Done conforme gates do item
```

`pnpm-workspace.yaml` e builds ainda não pertencem a essa evidência. Eles entram em `FND-002`.

## Execução esperada — FND-002

Depois que `FND-001` estiver validado, o próximo item materializa a Visão do Tech Lead:

```text
FND-002
   ↓
consultar D06 + Visão do Tech Lead
   ↓
fixar Node 24 LTS + pnpm
   ↓
configurar workspace
   ↓
TypeScript strict
   ↓
React/Vite web + Fastify API
   ↓
lockfile
   ↓
clean install + build mínimo
   ↓
evidência
```

Somente a partir daí os quality gates concretos de `FND-003` podem ser configurados sobre uma toolchain reproduzível.

## Exemplo de interação quando surge autenticação externa

### Codex

```text
FND-005 está elegível, mas exige autenticação no provider aprovado.
A criação do recurso pode ser gratuita dentro do plano pesquisado, porém preciso confirmar o estado atual da conta antes de prosseguir.

HUMAN_GATE_REQUIRED: provider_login
ACTION_FOR_HUMAN:
1. abra a página de login que deixei preparada;
2. autentique-se diretamente no provider;
3. conclua MFA/CAPTCHA se solicitado;
4. não envie senha, token ou recovery code no chat;
5. avise apenas quando a sessão estiver autenticada.
```

### Usuário

Sessão autenticada. Pode continuar.

### Codex

O agente continua somente na sessão autorizada e não copia credenciais para a conversa.

## Exemplo de gate de custo

Neste exemplo, a criação do runtime Cloud Run deve ser tratada como potencialmente cobrável mesmo que exista free tier.

```text
HUMAN_GATE_REQUIRED: billable_resource
RESOURCE: Cloud Run staging API
PURPOSE: runtime da API Fastify
CURRENT_COST_CLASSIFICATION: POTENTIALLY_BILLABLE
KNOWN_PRICE: conforme pesquisa atual da documentação oficial
ALTERNATIVES: não trocar provider silenciosamente; qualquer alternativa exige reconciliação
ACTION_REQUIRED: explicit approval before creation
```

Sem aprovação, o item fica `Blocked`; não é contornado por escolha silenciosa de outro serviço.

## Quando a Fundação termina

O Codex executa `foundation-readiness` ou check equivalente e deve retornar algo semelhante:

```text
FOUNDATION_STATUS: FND_READY

repo_structure: validated
tech_stack: validated
approved_dependencies: validated
locked_toolchain: validated
quality_gates: validated
ci: validated
database_migrations: validated
auth_tenant_baseline: validated
web_staging: validated
api_staging: validated
providers_match_infrastructure_plan: validated
secrets_handling: validated
observability_minimum: validated
smoke_tests: validated

NEXT_ELIGIBLE_MILESTONE: M1 — Identity / Tenancy
```

Se qualquer parte essencial estiver incompleta, o resultado deve ser `FND_PARTIAL` ou `FND_BLOCKED` com gaps concretos.

## Exemplo de divergência tecnológica

Suponha que durante `FND-002` o agente prefira instalar outro framework de API.

O comportamento correto é:

```text
Visão do Tech Lead: Fastify 5
        ↓
Codex identifica preferência/alternativa
        ↓
NÃO instala silenciosamente
        ↓
existe restrição nova que torna Fastify inviável?
        ├─ não → manter decisão canônica
        └─ sim → bloquear item e devolver decisão ao fluxo documental
```

A implementação não possui precedência sobre a decisão tecnológica aprovada.

## Execução funcional

Depois da Fundação:

### Usuário

```text
Continue consumindo o backlog na ordem de dependências. Execute a próxima menor fatia elegível, começando por AUTH-001. Antes de codificar, releia os documentos de origem, aplique integralmente as Técnicas de Desenvolvimento e respeite a Visão do Tech Lead.
```

O ciclo passa a ser:

```text
item do backlog
   ↓
documentos de origem
   ↓
D06 + arquitetura + stack quando aplicáveis
   ↓
código existente e padrões locais
   ↓
reuso antes de criação
   ↓
implementação pequena
   ↓
testes
   ↓
gates
   ↓
staging quando aplicável
   ↓
evidência
   ↓
matriz atualizada
```

## Correção de bug recorrente durante o projeto

Suponha que, meses depois, uma falha de isolamento de tenant reapareça em endpoints diferentes.

O comportamento esperado não é apenas corrigir novamente.

```text
incidente
   ↓
correção + teste de regressão
   ↓
IA reconhece classe recorrente
   ↓
Issue com causa/detecção/prevenção
   ↓
discover-to-skill avalia reutilização
   ↓
novo check/skill se justificado
   ↓
document-consistency reconcilia projeto
```

Assim, o processo transforma uma ocorrência real em conhecimento executável quando há valor de reutilização.

## Encerramento do exemplo

Este estudo de caso termina quando o projeto cruza a fronteira:

```text
ChatGPT
→ Discovery e documentação aprovada

Git
→ fonte canônica versionada

Codex
→ Fundação + implementação + evidência
```

A mensagem curta “consuma o backlog” só é segura porque, antes dela, o projeto já possui um sistema explícito de decisões, constraints, stack, critérios de aceite e rastreabilidade.
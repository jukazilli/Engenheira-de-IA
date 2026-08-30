# Handoff para o Codex — AVA OMEM

> **Objetivo:** mostrar a passagem do projeto documentado no ChatGPT para o ambiente de execução.

## Pré-condições

Antes de abrir o Codex:

- todos os documentos do exemplo foram aprovados;
- o repositório do projeto real já contém os `.md` canônicos;
- o repositório foi clonado ou atualizado na máquina local;
- o Codex está aberto na raiz do projeto;
- ainda não existe permissão para escolher provedores pagos ou manipular credenciais humanas sem gate.

## Primeiro comando no Codex

```text
Consuma integralmente a documentação canônica deste projeto antes de alterar qualquer arquivo.

Leia os documentos na ordem e precedência definidas pelo processo, com atenção especial a:

- 06_Tecnicas_de_Desenvolvimento.md
- 07_Engenharia_e_Arquitetura.md
- Infraestrutura_e_Plano_de_Fundacao.md
- 08_Backlog_Canonico_Rastreabilidade_e_Plano_de_Entrega.md
- 09_Matriz_Operacional_de_Rastreabilidade.md

Leia também todos os documentos anteriores e qualquer documentação derivada existente.

Não implemente nada ainda.

Primeiro responda somente com:

DOCUMENTS_CONSUMED
DOCUMENT_CONSISTENCY
CURRENT_FOUNDATION_STATUS
BACKLOG_STATUS
NEXT_EXECUTABLE_ITEM
BLOCKERS
PROPOSED_FIRST_SLICE

Não marque item como entregue sem evidência. Não escolha silenciosamente infraestrutura diferente da aprovada. Não peça senhas, tokens, chaves privadas ou secrets pelo chat.
```

## Resposta simulada do Codex

```text
DOCUMENTS_CONSUMED: complete
DOCUMENT_CONSISTENCY: consistent for initial execution
CURRENT_FOUNDATION_STATUS: not_started
BACKLOG_STATUS: canonical; first milestone M0
NEXT_EXECUTABLE_ITEM: FND-001
BLOCKERS: none for local repository initialization
PROPOSED_FIRST_SLICE: FND-001 — initialize monorepo structure and verify workspace/build boundaries
```

## Autorização humana

### Usuário

Consuma o backlog para iniciarmos o desenvolvimento da aplicação. Comece pelo `FND-001` e siga somente pelos itens FND elegíveis. Faça commits pequenos, execute os gates definidos e mantenha a matriz consistente.

## Execução esperada — FND-001

O Codex deve:

```text
reler FND-001
   ↓
consultar D06 e D07
   ↓
inspecionar repo atual
   ↓
criar a menor estrutura necessária
   ↓
configurar workspace mínimo
   ↓
executar instalação/build/checks aplicáveis
   ↓
auto-revisar diff
   ↓
atualizar rastreabilidade
   ↓
registrar evidência
```

Ele não deve avançar para `FND-005`, por exemplo, apenas porque consegue abrir o painel do provider. Dependências do backlog continuam governando a execução.

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

Se o provider exigir upgrade:

```text
HUMAN_GATE_REQUIRED: billable_resource
RESOURCE: <nome>
PURPOSE: staging database / runtime / e-mail etc.
CURRENT_COST_CLASSIFICATION: POTENTIALLY_BILLABLE
KNOWN_PRICE: <valor pesquisado, se atual e confirmado>
ALTERNATIVES: <opções>
ACTION_REQUIRED: explicit approval before creation
```

Sem aprovação, o item fica `Blocked`; não é contornado por escolha silenciosa de outro serviço.

## Atualização da matriz durante a Fundação

Depois de validar `FND-001`, uma linha pode evoluir de:

```text
FND-001 | implementação — | testes — | evidência — | Planned
```

para algo como:

```text
FND-001
Implementation:
- pnpm-workspace.yaml
- apps/web
- apps/api
- packages/domain
- packages/contracts

Tests:
- clean install
- workspace build smoke
- boundary check

Evidence:
- commit <sha>
- CI <run, quando disponível>

Status: Validated / Done conforme gates do projeto
```

A atualização deve refletir o que aconteceu, não o que o agente pretende fazer.

## Quando a Fundação termina

O Codex executa `foundation-readiness` ou check equivalente e deve retornar algo semelhante:

```text
FOUNDATION_STATUS: FND_READY

repo_structure: validated
locked_toolchain: validated
quality_gates: validated
ci: validated
database_migrations: validated
auth_tenant_baseline: validated
web_staging: validated
api_staging: validated
secrets_handling: validated
observability_minimum: validated
smoke_tests: validated

NEXT_ELIGIBLE_MILESTONE: M1 — Identity / Tenancy
```

Se qualquer parte essencial estiver incompleta, o resultado deve ser `FND_PARTIAL` ou `FND_BLOCKED` com gaps concretos.

## Execução funcional

Depois da Fundação:

### Usuário

```text
Continue consumindo o backlog na ordem de dependências. Execute a próxima menor fatia elegível, começando por AUTH-001. Antes de codificar, releia os documentos de origem e aplique integralmente as Técnicas de Desenvolvimento.
```

O ciclo passa a ser:

```text
item do backlog
   ↓
documentos de origem
   ↓
código existente e padrões locais
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

A mensagem curta “consuma o backlog” só é segura porque, antes dela, o projeto já possui um sistema explícito de decisões, constraints, critérios de aceite e rastreabilidade.
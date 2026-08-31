---
document_id: CASE-01-DOC-07
title: Engenharia e Arquitetura — CRM para gestão de clientes e pedidos
status: canonical
version: 1.0.0
case_id: CASE-01-CRM-CLIENTES-PEDIDOS
methodology_stage: engenharia-arquitetura
consumes:
  - 00_Discovery.md
  - 01_Pesquisa_e_Viabilidade.md
  - 02_Briefing_de_Produto_e_Escopo.md
  - 03_Visao_de_Product_Owner.md
  - Principios_de_UX_UI.md
  - 04_Direcao_de_UI_e_Design_System.md
  - 05_Especificacao_de_UX.md
  - 06_Tecnicas_de_Desenvolvimento.md
next_document: Visao_do_Tech_Lead.md
architecture_readiness: SUFFICIENT_WITH_OPEN_QUESTIONS
ready_for_codex: false
---

# Engenharia e Arquitetura — CRM para gestão de clientes e pedidos

## 1. Propósito

Este documento transforma a baseline canônica do Caso 01 em uma arquitetura de software capaz de preservar os contratos de produto, UX e qualidade já aprovados, sem escolher prematuramente linguagem, runtime, framework, engine concreta de banco, cloud, provedor ou ferramenta de CI/CD.

A pergunta central é:

> **O que tecnicamente precisa ser verdade para que o CRM preserve o trabalho comercial, integre-se ao TOTVS Protheus sem criar uma segunda verdade, aplique autorização por carteira, mantenha histórico e auditabilidade e permaneça simples o suficiente para sustentar o business case?**

A arquitetura deve ser a menor estrutura suficiente para cumprir os drivers reais do produto.

```text
PRODUTO / UX
        ↓
MENSURAÇÃO TÉCNICA
        ↓
DRIVERS E QUALIDADES
        ↓
DOMÍNIOS E BOUNDARIES
        ↓
AUTORIDADE DE DADOS
        ↓
INTEGRAÇÕES E INVARIANTES
        ↓
REQUISITOS PARA STACK
        ↓
VISÃO DO TECH LEAD
```

A existência deste documento não autoriza implementação pelo Codex.

---

## 2. Base consumida

A arquitetura consome integralmente:

- `00_Discovery.md`;
- `01_Pesquisa_e_Viabilidade.md`;
- `02_Briefing_de_Produto_e_Escopo.md`;
- `03_Visao_de_Product_Owner.md`;
- `Principios_de_UX_UI.md`;
- `04_Direcao_de_UI_e_Design_System.md`;
- `05_Especificacao_de_UX.md`;
- `06_Tecnicas_de_Desenvolvimento.md`.

Contratos dominantes herdados:

- TOTVS Protheus permanece autoridade para dados e operações ERP definidos como canônicos;
- o CRM é uma camada comercial e não um segundo ERP;
- o vendedor pode descobrir a existência de cliente de outra carteira sem receber automaticamente acesso ao histórico comercial dessa carteira;
- gerente e diretor possuem visão ampliada conforme responsabilidade e escopo;
- histórico comercial pertence à empresa e sobrevive à troca ou saída de vendedor;
- informação financeira é proporcional ao papel;
- dados do Protheus precisam carregar estado de confiança quando atualidade afeta decisão;
- indisponibilidade do Protheus não deve derrubar o trabalho comercial próprio do CRM;
- repetição de intenção não pode duplicar efeito material;
- falhas recuperáveis não devem apagar trabalho válido;
- TCO e complexidade operacional precisam permanecer compatíveis com o business case;
- offline completo não está aprovado para o P0.

---

## 3. Mensuração técnica

A arquitetura foi derivada a partir do porte real conhecido do cenário, e não de uma escala futura especulativa.

| Dimensão | Estado de conhecimento | Valor / leitura atual | Impacto arquitetural |
| --- | --- | --- | --- |
| usuários comerciais iniciais | CONFIRMADO | 18 vendedores, 2 gerentes, 1 diretor | não justifica distribuição por escala |
| clientes existentes | CONFIRMADO | aproximadamente 12 mil | volume pequeno/moderado para o horizonte atual |
| filiais | CONFIRMADO | 2 | identidade ERP e escopo organizacional precisam ser inequívocos |
| desktop + mobile | CONFIRMADO | ambos no P0 | stack futura precisa atender os dois contextos |
| ERP | CONFIRMADO | TOTVS Protheus | integração externa material |
| integrações REST já existentes no cliente | CONFIRMADO NO CENÁRIO | sim | reduz risco de viabilidade, não define mecanismo final |
| customizações Protheus | CONFIRMADO | existem | inventário obrigatório antes da integração real |
| release exato Protheus | PENDENTE | ainda não levantado | gate técnico antes de contrato definitivo |
| volume diário de interações | PENDENTE | não medido | não justifica escala preventiva |
| volume/frequência de pedidos | PENDENTE | não medido | influencia atualização e eventual materialização de contexto ERP |
| rede móvel instável | HIPÓTESE FORTE | contexto de campo | exige preservação de rascunho e recuperação |
| offline completo | DESCARTADO NO P0 | não | evita arquitetura local-first completa |
| TCO reduzido | CONFIRMADO | business case é sensível a custo | complexidade operacional é driver arquitetural |
| retenção LGPD | PENDENTE | política ainda não definida | não inventar prazo de retenção |
| identity provider corporativo | PENDENTE | não definido | Tech Lead/Infra deverão avaliar opções |

### 3.1. Leitura principal

O risco técnico dominante do sistema não é escala de milhões de usuários.

```text
ESCALA
não domina o desenho atual

INTEGRAÇÃO
AUTORIZAÇÃO
INTEGRIDADE
AUDITORIA
RESILIÊNCIA
SIMPLICIDADE

são os drivers dominantes
```

Portanto, a arquitetura não deve introduzir distribuição preventiva apenas para parecer preparada para crescimento hipotético.

---

## 4. Drivers arquiteturais

### ARCH-DRV-001 — Autoridades distintas CRM × Protheus

**Origem:** BR-001, BR-003, UX-JRN-004.

O CRM possui dados próprios e também representa dados cuja autoridade permanece no Protheus.

**Prioridade:** crítica.

**Impacto:** exige autoridade de dados explícita e isolamento da integração.

---

### ARCH-DRV-002 — Protheus pode degradar sem derrubar o core

**Origem:** UX-STA-006, UX-GATE-003.

Indisponibilidade do ERP não deve impedir histórico, próxima ação, prospect, carteira e registro comercial.

**Prioridade:** crítica.

**Impacto:** core CRM não pode depender sincronamente do Protheus para todo comando comercial.

---

### ARCH-DRV-003 — Autorização contextual por carteira

**Origem:** BR-004, BR-005, BR-007, UX-GATE-005.

Papel isolado não responde se determinado usuário pode ver determinado cliente/histórico.

**Prioridade:** crítica.

**Impacto:** autorização precisa considerar sujeito, recurso, ação, ownership e escopo organizacional.

---

### ARCH-DRV-004 — Histórico corporativo durável

**Origem:** BR-006, US-017.

Trocar o vendedor responsável não pode apagar, reatribuir silenciosamente ou reiniciar o histórico comercial.

**Prioridade:** crítica.

---

### ARCH-DRV-005 — Idempotência de comandos materiais

**Origem:** UX de repetição + DEV-IDEMP-01..04.

Retry, double tap e reconexão não podem produzir segundo efeito lógico.

**Prioridade:** alta.

---

### ARCH-DRV-006 — Concorrência de ownership

**Origem:** US-013 e política de concorrência do documento 06.

Duas transferências concorrentes não podem resultar em `last-write-wins` acidental.

**Prioridade:** alta.

---

### ARCH-DRV-007 — Freshness de dados ERP

**Origem:** BR-012, UX-STA-003..006.

Dados do ERP podem estar atuais, atualizando, potencialmente desatualizados ou indisponíveis.

**Prioridade:** alta.

---

### ARCH-DRV-008 — Custo e simplicidade

**Origem:** Pesquisa e Briefing.

A solução custom só permanece racional se o TCO não destruir o business case.

**Prioridade:** alta.

---

### ARCH-DRV-009 — Dados pessoais, comerciais e financeiros

**Origem:** Pesquisa LGPD, BR-013 e UX/UI.

O sistema processa dados de contatos, histórico comercial e informações financeiras restritas.

**Prioridade:** alta.

---

### ARCH-DRV-010 — Rede móvel imperfeita sem offline completo

**Origem:** UX-JRN-002 e política de conectividade.

Rascunho e trabalho válido não podem desaparecer por oscilação comum de rede.

**Prioridade:** alta.

---

### ARCH-DRV-011 — Contratos Protheus são voláteis em relação ao domínio

**Origem:** pesquisa técnica e customizações do cliente.

O domínio do CRM não pode conhecer diretamente payloads, tabelas ou detalhes específicos do ERP.

**Prioridade:** alta.

---

### ARCH-DRV-012 — Evolução reversível

**Origem:** business case e Técnicas de Desenvolvimento.

O sistema deve permitir rollout incremental, compatibilidade e retirada de decisões quando a hipótese de valor falhar.

**Prioridade:** média/alta.

---

## 5. Cenários de atributos de qualidade

### QA-001 — Autorização horizontal

**Atributo:** segurança.

**Estímulo:** vendedor tenta acessar histórico de cliente pertencente a outra carteira por rota/API direta.

**Resposta:** acesso detalhado é negado de forma autoritativa no backend; descoberta mínima permitida permanece separada.

**Medida:** teste automatizado de autorização deve falhar se a regra for removida.

**Prioridade:** crítica.

---

### QA-002 — Indisponibilidade Protheus

**Atributo:** resiliência/disponibilidade.

**Estímulo:** Protheus fica indisponível durante operação comercial.

**Resposta:** comandos e leituras canônicas do CRM continuam disponíveis; contexto ERP degrada de forma explícita.

**Medida:** teste de integração/falha confirma que o core comercial continua operável.

**Prioridade:** crítica.

---

### QA-003 — Comando repetido

**Atributo:** confiabilidade/integridade.

**Estímulo:** mesma intenção de registrar interação é recebida mais de uma vez.

**Resposta:** apenas um efeito lógico é criado.

**Medida:** teste de repetição/retry.

**Prioridade:** alta.

---

### QA-004 — Transferência concorrente

**Atributo:** consistência.

**Estímulo:** dois atores tentam transferir o mesmo cliente a partir do mesmo estado base.

**Resposta:** uma operação é aceita e a concorrente recebe conflito explícito; nenhuma sobrescrita silenciosa ocorre.

**Medida:** teste concorrente/reprodutível.

**Prioridade:** alta.

---

### QA-005 — Auditabilidade de ownership

**Atributo:** auditabilidade.

**Estímulo:** responsabilidade por cliente é transferida.

**Resposta:** ator, momento, alvo e resultado ficam rastreáveis.

**Medida:** consulta de trilha de auditoria controlada.

**Prioridade:** alta.

---

### QA-006 — Dado ERP potencialmente desatualizado

**Atributo:** confiança/consistência.

**Estímulo:** sistema possui última representação conhecida mas não consegue confirmar atualização atual.

**Resposta:** dado não é apresentado como confirmado atual; origem/momento/estado são preservados.

**Medida:** teste de estado `STALE`/equivalente.

**Prioridade:** alta.

---

### QA-007 — Perda de rede durante edição

**Atributo:** recuperabilidade.

**Estímulo:** vendedor perde conectividade após digitar conteúdo válido.

**Resposta:** rascunho não desaparece apenas pela falha de rede.

**Medida:** teste de interrupção/reentrada.

**Prioridade:** alta.

---

### QA-008 — Breaking change externo

**Atributo:** compatibilidade/operabilidade.

**Estímulo:** contrato esperado do Protheus muda de forma incompatível.

**Resposta:** incompatibilidade é detectável por contratos/integração antes de produzir corrupção silenciosa.

**Prioridade:** alta.

---

### QA-009 — Diagnóstico sem vazamento

**Atributo:** observabilidade/privacidade.

**Estímulo:** ocorre falha técnica envolvendo cliente, histórico ou ERP.

**Resposta:** logs e métricas permitem diagnóstico sem copiar texto comercial, segredos ou payload integral desnecessário.

**Prioridade:** alta.

---

### QA-010 — Responsividade no porte atual

**Atributo:** desempenho.

**Estímulo:** utilização concorrente compatível com a população inicial e operações previstas.

**Resposta:** fluxos interativos permanecem adequados ao trabalho cotidiano.

**Medida:** metas numéricas devem ser calibradas por benchmark da stack escolhida e piloto; não há escala suficiente para justificar números artificiais nesta etapa.

**Prioridade:** média/alta.

---

## 6. Não objetivos arquiteturais

No horizonte atual não são objetivos:

- microserviços preventivos;
- multi-região ativa-ativa;
- event sourcing global;
- offline-first completo;
- sistema global de eventos criado sem consumidores reais;
- abstração de todo vendor imaginável;
- replicação completa do Protheus;
- consistência forte em todo dado independentemente do significado;
- cache em toda consulta por padrão;
- reconstruir transações financeiras/fiscais dentro do CRM.

Toda complexidade adicional precisa apontar para um driver real.

---

## 7. Forma arquitetural

### ADR-001 — Monólito modular no horizonte inicial

**Status:** aceito.

**Contexto:** aproximadamente 21 usuários comerciais, cerca de 12 mil clientes, uma única equipe/produto, necessidade de transações internas e TCO sensível.

**Decisão:** iniciar com um **monólito modular**, com boundaries internos explícitos e integração externa isolada.

**Alternativas consideradas:** microserviços, arquitetura distribuída por domínio, funções independentes por entidade.

**Consequências positivas:**

- menor custo operacional;
- menor complexidade de deploy;
- transações internas mais simples;
- evolução mais rápida no piloto;
- melhor aderência ao business case.

**Consequências negativas:**

- exige disciplina modular real para não degenerar em monólito acoplado;
- workloads futuros muito diferentes podem exigir extração.

**Gatilho de revisão:** escala independente persistente, boundary regulatório, runtime incompatível, necessidade real de isolamento de falha ou ownership organizacional independente.

---

## 8. Arquitetura lógica

```text
┌──────────────────────────────┐
│         EXPERIÊNCIA          │
│      desktop + mobile        │
└──────────────┬───────────────┘
               │
               ▼
┌──────────────────────────────┐
│      CAMADA DE APLICAÇÃO     │
│ casos de uso + autorização   │
└──────────────┬───────────────┘
               │
       ┌───────┼────────┐
       ▼       ▼        ▼
┌──────────┐ ┌────────┐ ┌─────────────┐
│ Accounts │ │Portfolio│ │Relationship │
└──────────┘ └────────┘ └─────────────┘
       │         │          │
       └─────────┼──────────┘
                 ▼
        ┌─────────────────┐
        │ Dados canônicos │
        │      do CRM     │
        └─────────────────┘

                 │
                 ▼
┌──────────────────────────────┐
│      PORTA DE CONTEXTO ERP   │
│   contrato interno estável   │
└──────────────┬───────────────┘
               │
               ▼
┌──────────────────────────────┐
│ ADAPTER / ANTI-CORRUPTION    │
│          PROTHEUS            │
└──────────────┬───────────────┘
               │
               ▼
        TOTVS PROTHEUS
```

O cliente não acessa o Protheus diretamente.

Credenciais, endpoints, payloads e particularidades do ERP permanecem atrás da fronteira de integração.

---

## 9. Domínios e boundaries

### ARCH-DOM-001 — Identity & Access

**Responsabilidade:** identidade, sessão, papéis, escopo e decisão autoritativa de acesso.

**Invariantes:**

- autorização não depende apenas da UI;
- revogação precisa ser respeitada;
- papel isolado não substitui ownership/contexto.

---

### ARCH-DOM-002 — Commercial Accounts

**Responsabilidade:** prospect, representação comercial do cliente e vínculo com identidade do Protheus.

**Conceitos:** Prospect, CommercialCustomer, ERPReference.

**Invariantes:**

- prospect pode existir sem cliente Protheus;
- cliente formal vinculado precisa apontar inequivocamente para a referência ERP correta;
- possível duplicidade precisa ser detectável no fluxo.

---

### ARCH-DOM-003 — Portfolio Ownership

**Responsabilidade:** responsável comercial atual e transferências.

**Invariantes:**

- transferência não apaga histórico;
- alteração de ownership é auditável;
- concorrência não pode ser resolvida por sobrescrita silenciosa.

---

### ARCH-DOM-004 — Relationship

**Responsabilidade:** interações, histórico comercial e próximas ações.

**Invariantes:**

- autoria e momento são preservados;
- histórico corporativo não é propriedade pessoal do vendedor;
- comandos repetidos não duplicam efeito.

---

### ARCH-DOM-005 — Attention

**Responsabilidade:** sinais derivados que ajudam a identificar clientes que merecem atenção.

**Observação:** é domínio derivado; a regra concreta ainda será calibrada com evidência e não deve fixar arbitrariamente 60 dias.

---

### ARCH-DOM-006 — ERP Context

**Responsabilidade:** fornecer ao CRM uma representação interna de capacidades/dados necessários do Protheus.

**Não é responsável por:** reproduzir módulos completos do ERP.

---

### ARCH-DOM-007 — Management

**Responsabilidade:** consultas e projeções gerenciais derivadas dos domínios canônicos e do escopo autorizado.

**Regra:** projeções não viram fonte de verdade.

---

### ARCH-DOM-008 — Audit

**Responsabilidade:** trilha de ações materiais e privilegiadas.

**Regra:** audit log é distinto de log técnico e de histórico comercial.

---

## 10. Direção de dependência

O princípio é:

```text
EXPERIÊNCIA
        ↓
CASOS DE USO
        ↓
DOMÍNIO

ADAPTADORES
        → implementam portas

PROTHEUS / INFRAESTRUTURA
        → permanecem na borda
```

Regras críticas não podem depender de estruturas de tela ou do payload bruto do Protheus.

Contratos externos nunca viram entidade interna diretamente apenas por conveniência.

---

## 11. Autoridade e semântica dos dados

| Dado/capacidade | Autoridade canônica |
| --- | --- |
| prospect ainda não formalizado | CRM |
| histórico comercial | CRM |
| próxima ação | CRM |
| responsável da carteira | CRM |
| transferência de carteira | CRM |
| cadastro formal do cliente ERP | Protheus |
| código/loja e identidade ERP | Protheus |
| pedido | Protheus |
| faturamento | Protheus |
| histórico transacional de compra | Protheus |
| estoque | Protheus |
| situação financeira ERP | Protheus |
| sinal “precisa de atenção” | derivado pelo CRM |
| dashboard e indicadores | projeções |

Regra estrutural:

```text
REPRESENTAÇÃO LOCAL DE DADO ERP
≠
AUTORIDADE DO DADO ERP
```

---

## 12. Identidade externa do cliente

O cenário confirma `código + loja` como parte da identificação do cliente no Protheus, mas ainda existem duas filiais e estrutura organizacional a confirmar.

A arquitetura, portanto, exige uma referência externa inequívoca conceitualmente equivalente a:

```text
ERPReference
- sistema
- empresa/grupo, quando aplicável
- filial, quando aplicável
- código
- loja
```

A composição definitiva depende do inventário real do Protheus e não deve ser inventada nesta etapa.

### ARCH-DATA-001

A chave interna do CRM não deve depender apenas de `codigo` do ERP.

---

## 13. Persistência canônica

### ADR-002 — Persistência relacional transacional

**Status:** aceito.

**Decisão:** os dados canônicos do CRM precisam de persistência relacional transacional.

**Drivers:** carteira, cliente/prospect, interações, próximas ações, autorização, auditoria e concorrência possuem relações e invariantes que se beneficiam de constraints e transações.

A arquitetura não escolhe engine concreta.

A Visão do Tech Lead decidirá entre produtos capazes de cumprir este requisito.

---

## 14. Event sourcing

### ADR-003 — Não adotar event sourcing global no horizonte atual

**Status:** aceito.

Histórico e auditoria não constituem, sozinhos, motivo suficiente para transformar todo o CRM em event sourced.

O sistema utilizará estado canônico transacional e trilhas específicas para histórico/auditoria conforme necessidade.

**Gatilho de revisão:** surgir requisito real de reconstrução temporal integral, versionamento complexo ou outro driver forte.

---

## 15. Integração Protheus

### ADR-004 — Isolar Protheus por porta e camada anticorrupção

**Status:** aceito.

O domínio consome capacidades internas estáveis; o adapter traduz contratos externos.

Benefícios:

- evita vazamento de tabelas/campos do ERP para todo o CRM;
- permite contract tests;
- reduz blast radius de customizações e upgrades;
- permite mocks/fakes controlados em testes;
- impede que a UI precise conhecer transporte ou credencial.

---

### ADR-005 — Integração P0 predominantemente read-only em relação ao ERP

**Status:** aceito.

No P0, o CRM pode consultar contexto necessário de:

- cliente formal;
- histórico de pedidos/compra;
- situação relevante de pedido;
- faturamento relevante;
- estoque necessário à atividade comercial;
- informação financeira permitida ao papel.

Não está autorizado no P0 atual:

- criar cliente no Protheus;
- criar pedido no Protheus;
- alterar estoque;
- alterar financeiro;
- executar faturamento.

Qualquer escrita futura no ERP reabre produto, segurança, idempotência e arquitetura.

---

## 16. Degradação do Protheus

### ADR-006 — Core CRM não depende da disponibilidade síncrona do Protheus

**Status:** aceito.

Se o ERP estiver indisponível:

```text
HISTÓRICO CRM
PRÓXIMA AÇÃO
PROSPECT
CARTEIRA
REGISTRO COMERCIAL

continuam operáveis
```

Enquanto:

```text
PEDIDO
ESTOQUE
FATURAMENTO
FINANCEIRO

podem degradar explicitamente
```

O Protheus é dependência crítica de contexto, não dependência síncrona obrigatória de todo comando comercial.

---

## 17. Freshness e snapshots ERP

### ADR-007 — Representações ERP carregam estado de confiança

**Status:** aceito.

A arquitetura precisa representar semanticamente estados equivalentes a:

```text
CURRENT
REFRESHING
STALE
UNAVAILABLE
```

Quando houver última representação conhecida, ela só pode ser utilizada se o domínio permitir e deve preservar momento/origem.

Regras de risco:

- pedido antigo pode ser mostrado como última informação conhecida, com timestamp;
- estoque antigo não pode parecer disponibilidade confirmada;
- situação financeira desatualizada não pode funcionar como autorização implícita de venda.

---

## 18. Offline e conectividade

O produto não exige offline completo.

Política por domínio:

| Domínio/tarefa | Continuidade degradada | Escrita local canônica? | Observação |
| --- | --- | --- | --- |
| rascunho de interação | sim | não | rascunho temporário precisa sobreviver à falha comum |
| dados CRM já carregados | possível conforme segurança | não | representação local não substitui backend canônico |
| confirmação de nova interação | depende do backend | não no desenho atual | UX só declara sucesso quando o estado verdadeiro permitir |
| consulta Protheus | pode ficar indisponível | não | fallback depende de freshness |
| pedido/estoque/financeiro | última posição apenas quando permitida | não | nunca afirmar atualidade sem confirmação |
| gestão complexa | pode degradar | não | não é tarefa crítica offline |

A arquitetura não é `local-first` no P0.

---

## 19. Idempotência

### ARCH-INV-001 — Repetição de intenção não duplica efeito

Comandos materiais precisam suportar identidade de intenção ou mecanismo equivalente.

Aplicável no P0 a:

- `RecordInteraction`;
- `CreateProspect`;
- `TransferOwnership`.

Aplicável obrigatoriamente a qualquer futura escrita no Protheus.

Contrato conceitual:

```text
MESMA INTENÇÃO REPETIDA
→ MESMO RESULTADO LÓGICO
→ SEM SEGUNDO EFEITO MATERIAL
```

O Tech Lead definirá a primitiva concreta.

---

## 20. Concorrência de carteira

### ADR-008 — Transferência usa precondição/versão explícita

**Status:** aceito.

Uma transferência deve ser baseada em estado/versão conhecida do ownership.

Exemplo conceitual:

```text
customer ownership
responsável = Maria
version = 17
```

Duas transferências baseadas na mesma versão não podem ambas ser aceitas silenciosamente.

A segunda precisa receber conflito e revisar o estado atual.

`last-write-wins` não é política aceita para ownership.

---

## 21. Autorização

### ADR-009 — Autorização server-side contextual

**Status:** aceito.

RBAC isolado é insuficiente.

A decisão autoritativa precisa considerar:

```text
SUJEITO
PAPEL
AÇÃO
RECURSO
OWNERSHIP
ESCOPO ORGANIZACIONAL
ESTADO DE REVOGAÇÃO
```

Exemplo:

```text
SELLER + OWN CUSTOMER + READ_HISTORY
→ permitido

SELLER + OTHER CUSTOMER + DISCOVER
→ mínimo permitido

SELLER + OTHER CUSTOMER + READ_HISTORY
→ negado

MANAGER + CUSTOMER IN MANAGEMENT SCOPE
→ acesso ampliado conforme regra
```

A UI nunca é a única barreira.

---

## 22. Threat model inicial

Ativos principais:

- carteira comercial;
- histórico e observações;
- dados pessoais de contatos;
- contexto financeiro permitido;
- credenciais/segredos de integração;
- referências Protheus;
- trilha de auditoria.

Ameaças prioritárias:

- acesso horizontal entre carteiras/IDOR;
- elevação indevida de papel;
- acesso financeiro indevido;
- revogação sem efeito;
- replay de comandos;
- duplicidade por retry;
- payload externo malformado ou inesperado;
- vazamento em logs/analytics;
- segredo de integração exposto;
- importação que mistura empresas/clientes;
- contexto de filial incorreto;
- alteração indevida de histórico/auditoria.

Controles arquiteturais obrigatórios, sem escolher ferramenta concreta:

- autorização autoritativa no backend;
- validação de entradas externas;
- minimização de dados entre boundaries;
- adapter para Protheus;
- idempotência;
- controle de concorrência em ownership;
- auditoria material;
- segredo restrito à fronteira de integração;
- telemetria allowlisted quando risco justificar.

---

## 23. Auditabilidade

### ADR-010 — Audit log separado de log técnico e histórico comercial

**Status:** aceito.

Ações materiais que podem exigir trilha:

- transferência de carteira;
- alteração de permissão;
- alteração relevante de vínculo ERP;
- ação administrativa sensível.

Campos conceituais mínimos:

```text
ator
momento
ação
alvo
resultado
contexto seguro
```

Estado anterior/posterior pode ser exigido conforme ação.

Audit log não substitui timeline comercial.

---

## 24. Trabalho assíncrono

Não há driver para arquitetura global orientada a eventos.

Workloads que podem exigir execução assíncrona:

- importação inicial;
- atualização/materialização de contexto ERP;
- reconciliação;
- cálculo de sinais de atenção;
- exportações futuras.

Para qualquer workload assíncrono material, a arquitetura exige definir:

- gatilho;
- durabilidade;
- idempotência;
- ordem quando relevante;
- retry;
- falha terminal;
- observabilidade;
- cancelamento quando aplicável.

A tecnologia de fila/job será escolhida posteriormente.

---

## 25. Cache e projeções

Cache não é requisito por padrão.

Pode existir representação reconstruível de dados ERP para:

- resiliência;
- redução de dependência síncrona;
- UX de freshness.

Antes de introduzir qualquer cache, a solução precisa declarar:

- fonte canônica;
- tolerância a desatualização;
- invalidação;
- efeito sobre autorização;
- reconstrução;
- risco de stale data.

Cache de autorização não pode permitir acesso após revogação além do contrato aprovado.

---

## 26. Observabilidade arquitetural

Sinais necessários:

- logs estruturados;
- métricas de integração/falha;
- audit logs;
- eventos semânticos de produto;
- correlation IDs quando úteis;
- release/version ID;
- indicadores de dependência Protheus;
- sinais de autorização negada/anômala sem expor dados indevidos;
- sinais de jobs/reconciliação quando existirem.

Dados proibidos em telemetria comum sem finalidade específica:

- texto livre comercial;
- observações de cliente;
- payload bruto do Protheus;
- tokens e credenciais;
- dados financeiros completos;
- headers de autorização;
- documentos pessoais completos.

---

## 27. RTO e RPO iniciais

Para os dados canônicos do CRM, a revisão simulada aprovou como **targets iniciais**:

```text
RTO inicial: até 4 horas
RPO inicial de desastre: até 15 minutos
```

Esses números são targets do cenário e precisam ser confrontados com custo na etapa de DevOps/Infraestrutura.

Uma gravação confirmada durante operação normal deve possuir durabilidade compatível com o estado informado ao usuário; o RPO acima trata desastre de armazenamento, não erro operacional cotidiano.

Dados ERP reconstruíveis possuem política diferente porque a autoridade permanece no Protheus.

---

## 28. Ambientes como requisito

A arquitetura exige isolamento conceitual entre pelo menos:

```text
LOCAL / DESENVOLVIMENTO
STAGING / VALIDAÇÃO
PRODUÇÃO
```

Preview/PR pode ser adicionado pela materialização posterior se o custo/benefício justificar.

Regras:

- produção utiliza dados reais somente no ambiente apropriado;
- desenvolvimento/testes usam dados sintéticos ou sanitizados;
- segredos não são compartilhados entre ambientes sem necessidade explícita;
- integração Protheus precisa de sandbox/ambiente controlado quando possível;
- promoção deve preservar rastreabilidade do artefato.

O provider não é decidido nesta etapa.

---

## 29. Backup e recuperação

Ativos com necessidade de recuperação:

| Ativo | Criticidade | Natureza |
| --- | --- | --- |
| dados canônicos CRM | alta | não reconstruíveis integralmente a partir do ERP |
| histórico comercial | alta | parte do valor central do produto |
| ownership | alta | regra operacional atual |
| configuração de autorização | alta | segurança |
| snapshots ERP | média | reconstruíveis da fonte externa |
| telemetria técnica | menor que dado canônico | não deve ser tratada como backup do produto |

DevOps/Infra escolherá backup, restore, PITR, replicação e testes necessários para atingir os targets aprovados.

---

## 30. Migração/importação inicial

Os aproximadamente 12 mil clientes e controles legados exigem abordagem incremental.

Contrato arquitetural:

```text
AMOSTRA SANITIZADA
↓
MAPEAMENTO
↓
VALIDAÇÃO
↓
DRY-RUN / AMOSTRA
↓
IMPORTAÇÃO CONTROLADA
↓
RECONCILIAÇÃO
↓
EVIDÊNCIA
```

A importação não pode fazer do CRM uma autoridade para campos cuja autoridade pertence ao Protheus.

Dados duplicados e qualidade da base continuam sendo gate.

---

## 31. Gatilhos de escala e extração

A arquitetura deve ser revisada se surgir evidência de:

- workload ERP degradando persistentemente o core interativo;
- necessidade material de isolamento de falha;
- isolamento regulatório;
- runtime especializado realmente incompatível;
- ownership organizacional independente e estável;
- escala muito diferente de um workload específico;
- necessidade frequente de deploy independente;
- custo mensurável de manter determinado boundary no monólito.

Sem esses gatilhos, extrair serviço não é autorizado.

---

## 32. Portabilidade

Não será criada abstração universal de providers sem cenário real de troca.

Entretanto, são pontos de lock-in que merecem disciplina:

- dados canônicos precisam ser exportáveis;
- domínio não deve depender diretamente do contrato Protheus;
- segredos não devem contaminar código/aplicação;
- toolchain futura deve preservar testes e contratos independentes o suficiente para migração razoável.

Portabilidade não significa custo zero de troca.

---

## 33. ADRs canônicas desta etapa

| ADR | Decisão |
| --- | --- |
| ADR-001 | iniciar com monólito modular |
| ADR-002 | persistência relacional transacional para dados canônicos CRM |
| ADR-003 | não adotar event sourcing global no horizonte atual |
| ADR-004 | isolar Protheus por porta/adaptador/anticorruption layer |
| ADR-005 | manter integração P0 predominantemente read-only em relação ao ERP |
| ADR-006 | core CRM não depende da disponibilidade síncrona do Protheus |
| ADR-007 | representações ERP carregam freshness/estado de confiança |
| ADR-008 | transferência de carteira usa precondição/versão explícita |
| ADR-009 | autorização é server-side e contextual, não apenas RBAC |
| ADR-010 | audit log é separado de log técnico e histórico comercial |

IDs não devem ser reutilizados para decisões futuras diferentes.

---

## 34. Requisitos para seleção tecnológica

### TECH-REQ-001 — Desktop + mobile

A solução deve sustentar experiência adequada em desktop e mobile sem obrigar composição idêntica.

**Obrigatório:** sim.

---

### TECH-REQ-002 — Modularidade testável

Backend e domínio precisam permitir regras testáveis independentemente de UI e adapters externos.

**Obrigatório:** sim.

---

### TECH-REQ-003 — Persistência relacional transacional

A engine concreta deve suportar transações, constraints, índices e migrations maduras.

**Obrigatório:** sim.

---

### TECH-REQ-004 — Autorização contextual

A stack precisa permitir decisões server-side por papel, ação, recurso, ownership e escopo.

**Obrigatório:** sim.

---

### TECH-REQ-005 — Idempotência e concorrência

A plataforma precisa oferecer primitivas suficientes para comandos idempotentes e controle de concorrência/versionamento.

**Obrigatório:** sim.

---

### TECH-REQ-006 — Integrações externas robustas

Precisa permitir timeout, retry controlado, validação de contrato, autenticação segura e adapter isolado.

**Obrigatório:** sim.

---

### TECH-REQ-007 — Trabalho assíncrono durável quando necessário

O ecossistema precisa possuir caminho confiável para jobs/retries sem obrigar adoção antecipada de infraestrutura complexa.

**Obrigatório:** capacidade, não necessariamente uso inicial amplo.

---

### TECH-REQ-008 — Freshness e snapshots reconstruíveis

Modelagem deve permitir origem, timestamp e estado de confiança de representações ERP.

**Obrigatório:** sim.

---

### TECH-REQ-009 — Estratégia completa de testes

Ecossistema precisa suportar testes de domínio, UI, contrato, integração e E2E com boa automação.

**Obrigatório:** sim.

---

### TECH-REQ-010 — Acessibilidade verificável

A stack de interface precisa permitir semântica, teclado, foco, leitor de tela, zoom/reflow e testes adequados.

**Obrigatório:** sim.

---

### TECH-REQ-011 — Observabilidade e auditoria

A plataforma deve permitir logs estruturados, métricas, correlation e auditabilidade sem obrigar exposição de payload sensível.

**Obrigatório:** sim.

---

### TECH-REQ-012 — Compatibilidade progressiva

Migrations e contratos devem permitir expandir/conviver/migrar/retirar com rollback razoável.

**Obrigatório:** sim.

---

### TECH-REQ-013 — TCO compatível

A stack e sua operação precisam ser justificáveis para o business case do cenário.

**Obrigatório:** sim.

---

### TECH-REQ-014 — Recuperabilidade

A materialização operacional precisa conseguir atingir targets iniciais de RTO/RPO aprovados a custo aceitável.

**Obrigatório:** sim.

---

### TECH-REQ-015 — Segredo Protheus fora do cliente

Nenhuma credencial de integração com ERP pode precisar ser exposta a browser/app cliente.

**Obrigatório:** sim.

---

### TECH-REQ-016 — Suporte empresarial e manutenção

Linguagens, runtimes e principais frameworks precisam possuir suporte/maturidade compatíveis com vida útil empresarial, política de atualização e disponibilidade de manutenção.

**Obrigatório:** sim.

---

## 35. Pendências abertas

| Pendente | Owner futuro | Quando precisa ser resolvido | Impacto |
| --- | --- | --- | --- |
| release exato Protheus | TI cliente | antes do PoC/contrato real | alto |
| endpoints/APIs/customizações existentes | TI cliente + Tech Lead | durante Tech Lead/PoC | alto |
| composição definitiva da ERPReference | TI + Arquitetura | antes da integração real | alto |
| volume/frequência de pedidos e estoque | cliente + Tech Lead | antes de decidir refresh/materialização | médio/alto |
| política de retenção LGPD | cliente/responsável jurídico | antes de dados reais/produção | alto |
| identity provider corporativo | cliente + Tech Lead | seleção tecnológica | médio/alto |
| qualidade da base de 12 mil clientes | cliente + projeto | antes de migração | alto |
| owner operacional da solução | cliente/consultoria | antes da produção | alto |
| custo de atingir RTO/RPO | DevOps/Infra | etapa 08 | médio/alto |

Essas pendências não impedem a seleção tecnológica inicial desde que sejam tratadas como gates e não como fatos inventados.

---

## 36. Gates arquiteturais

| Gate | Evidência do caso |
| --- | --- |
| ARCH-01 Drivers | ARCH-DRV-001..012 rastreáveis à baseline |
| ARCH-02 Qualidade | QA-001..010 definidos |
| ARCH-03 Domínio | ARCH-DOM-001..008 e dependências definidos |
| ARCH-04 Dados | autoridade CRM × Protheus e ERPReference definidas conceitualmente |
| ARCH-05 Contratos | comandos materiais, idempotência, concorrência e adapter definidos semanticamente |
| ARCH-06 Offline | offline completo descartado; rascunho/continuidade delimitados |
| ARCH-07 Integrações | Protheus isolado, read-only P0 e degradação definidos |
| ARCH-08 Segurança | trust boundaries e autorização contextual definidos |
| ARCH-09 Confiabilidade | degradação + targets iniciais RTO/RPO definidos |
| ARCH-10 Evolução | gatilhos de extração/escala definidos |
| ARCH-11 ADRs | ADR-001..010 registrados |
| ARCH-12 Tech Handoff | TECH-REQ-001..016 prontos |

---

## 37. Revisão simulada

A revisão envolveu os papéis do cenário.

### TI

Confirmou como princípio que a integração não deve contornar regras do Protheus e aprovou a fronteira isolada para o ERP. Reforçou a necessidade de inventário do release, customizações e APIs antes do contrato definitivo.

### Gerente comercial

Considerou autorização por carteira e controle de concorrência de transferência requisitos críticos. Também reforçou que dado financeiro antigo não pode aparecer como liberação atual.

### Vendedor

Confirmou que queda do Protheus não deve impedir o registro de ligação, histórico ou próxima ação.

### Diretor

Aprovou explicitamente evitar microserviços, multi-região e complexidade preventiva antes de existir evidência, pois isso protege o business case.

A revisão não alterou o escopo P0.

---

## 38. Validação da metodologia

A etapa conseguiu transformar contratos anteriores em propriedades estruturais sem selecionar tecnologia concreta.

Exemplo:

```text
UX
“Protheus pode ficar indisponível
sem apagar o trabalho comercial”

↓

TÉCNICAS
“falha é caminho normal
e precisa ser testada”

↓

ARQUITETURA
core CRM não depende sincronamente do ERP
+
Protheus vive atrás de adapter
+
dados externos possuem freshness
+
fallback não inventa verdade
```

Outro:

```text
UX
“double tap não pode duplicar interação”

↓

TÉCNICAS
“repetição precisa ser provada”

↓

ARQUITETURA
comandos materiais exigem semântica idempotente
```

Nenhuma escolha concreta foi canonizada para:

- linguagem;
- framework;
- engine de banco;
- cloud;
- provider de auth;
- CI/CD;
- produto de fila;
- biblioteca de testes;
- transporte definitivo Protheus.

Resultado:

```text
ARCH_METHOD_VALIDATION: PASS

STACK_SELECTED: NO
DATABASE_ENGINE_SELECTED: NO
CLOUD_SELECTED: NO
CI_VENDOR_SELECTED: NO
PROTHEUS_TRANSPORT_SELECTED: NO

ARCHITECTURAL_STYLE: DEFINED
DOMAIN_BOUNDARIES: DEFINED
DATA_AUTHORITIES: DEFINED
DEPENDENCY_DIRECTION: DEFINED
ERP_BOUNDARY: DEFINED
AUTHORIZATION_MODEL: DEFINED
IDEMPOTENCY_REQUIREMENT: DEFINED
CONCURRENCY_POLICY: DEFINED
DATA_FRESHNESS_POLICY: DEFINED
OFFLINE_SCOPE: DEFINED
AUDIT_REQUIREMENTS: DEFINED
RECOVERY_TARGETS: INITIAL_TARGETS_DEFINED
SCALING_TRIGGERS: DEFINED
ADRS: CANONICAL
TECH_REQUIREMENTS: READY
```

---

## 39. Readiness e handoff

```text
ARCHITECTURE_READINESS: SUFFICIENT_WITH_OPEN_QUESTIONS
READY_FOR_CODEX: NO
NEXT_CANONICAL_ARTIFACT: Visao_do_Tech_Lead.md
```

`SUFFICIENT_WITH_OPEN_QUESTIONS` é apropriado porque as pendências possuem owner/momento de resolução e não impedem que o Tech Lead compare tecnologias candidatas.

O Tech Lead deve consumir especialmente:

- `ARCH-DRV-001..012`;
- `QA-001..010`;
- `ADR-001..010`;
- `TECH-REQ-001..016`;
- pendências de Protheus, identidade e migração.

A próxima etapa deverá selecionar tecnologias concretas somente quando conseguir mostrar quais requisitos arquiteturais cada escolha satisfaz.

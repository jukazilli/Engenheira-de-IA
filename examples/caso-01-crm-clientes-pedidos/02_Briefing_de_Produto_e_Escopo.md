---
document_id: CASE-01-DOC-02
title: Briefing de Produto e Escopo — CRM para gestão de clientes e pedidos
status: canonical
version: 1.0.0
case_id: CASE-01-CRM-CLIENTES-PEDIDOS
methodology_stage: briefing-produto-escopo
consumes:
  - 00_Discovery.md
  - 01_Pesquisa_e_Viabilidade.md
next_document: 03_Visao_de_Product_Owner.md
briefing_readiness: SUFFICIENT
---

# Briefing de Produto e Escopo — CRM para gestão de clientes e pedidos

## 1. Definição do produto

O produto é um **CRM comercial enxuto para vendedores e gestores da empresa**, destinado a centralizar carteira, prospects, relacionamento, retornos e contexto comercial dos clientes, integrando-se ao TOTVS Protheus para reduzir fragmentação operacional sem substituir as responsabilidades transacionais do ERP.

A definição canônica deste horizonte é:

> **Uma camada operacional comercial que concentra quem atender, o que já aconteceu e o que fazer a seguir, trazendo ao contexto do cliente as informações necessárias do Protheus sem transformar o CRM em um segundo ERP.**

A identidade do produto não é “software próprio” por si só.

A Pesquisa e Viabilidade concluiu que um CRM sob medida é justificável de forma condicional para este cliente, mas a decisão permanece subordinada ao business case, à integração real com o Protheus e ao controle de escopo e TCO.

---

## 2. Problema central

A operação comercial atual depende de informações distribuídas entre:

- TOTVS Protheus;
- planilhas;
- WhatsApp;
- controles individuais;
- memória dos vendedores;
- conhecimentos não formalizados sobre carteira e histórico.

Isso produz cinco efeitos principais:

1. o histórico comercial não pertence de forma confiável à empresa;
2. o vendedor precisa reconstruir contexto em múltiplos lugares;
3. follow-ups e oportunidades podem depender excessivamente de memória e controles pessoais;
4. a gestão não possui visão consolidada e confiável da atividade comercial;
5. desligamentos de vendedores podem causar perda de conhecimento e alto esforço de reconstrução de carteira.

O problema não é a inexistência de um CRM genérico.

O problema é a **fragmentação da operação comercial e a duplicidade entre o trabalho de relacionamento e o contexto transacional do Protheus**.

---

## 3. Tese consolidada

Quando o vendedor precisa conduzir relacionamento, follow-up e contexto comercial utilizando múltiplas ferramentas, aumenta o esforço operacional para descobrir o que aconteceu, decidir o que fazer e responder ao cliente.

Essa fragmentação reduz continuidade, visibilidade e capacidade de gestão e cria dependência de controles individuais.

A tese aprovada para este horizonte é:

```text
CENTRALIZAR O TRABALHO COMERCIAL
+
TRAZER CONTEXTO NECESSÁRIO DO PROTHEUS
+
PRESERVAR AUTORIDADE DO ERP
+
REDUZIR DUPLA OPERAÇÃO

→

MENOS FRAGMENTAÇÃO
MAIS CONTINUIDADE
MAIS VISIBILIDADE
MENOR ESFORÇO OPERACIONAL
```

A tese perde validade se o CRM se tornar uma segunda operação paralela ao Protheus.

---

## 4. Público do horizonte atual

### 4.1. Vendedor

Público operacional primário.

Precisa:

- trabalhar sua carteira;
- localizar clientes e prospects;
- compreender rapidamente o contexto comercial;
- registrar interações;
- saber qual é a próxima ação;
- consultar informações relevantes de compras e pedidos;
- identificar a existência de cliente de outra carteira sem receber acesso irrestrito ao histórico alheio;
- operar também em contexto móvel.

### 4.2. Gerente comercial

Público de gestão operacional.

Precisa:

- acompanhar carteiras sob sua responsabilidade;
- entender atividade da equipe;
- localizar clientes que precisam de atenção;
- consultar histórico comercial;
- acompanhar retornos;
- transferir carteira quando necessário;
- utilizar informação registrada para orientar a equipe.

### 4.3. Diretor comercial

Stakeholder decisor e consumidor de visão consolidada.

Precisa:

- compreender saúde da operação comercial;
- reduzir dependência de controles paralelos;
- preservar conhecimento comercial da empresa;
- acompanhar resultados e riscos do projeto;
- assegurar que o business case continue válido.

### 4.4. TI / responsáveis pelo Protheus

Stakeholders técnicos e operacionais, não público primário do CRM.

Participam da governança de:

- integração;
- customizações existentes;
- contratos de dados;
- acesso ao ambiente;
- suporte e continuidade operacional.

---

## 5. Jobs to be Done

### 5.1. Vendedor

| Elemento | Definição |
| --- | --- |
| Quando | estou trabalhando um cliente ou prospect |
| Quero | encontrar rapidamente o contexto, registrar o que fiz e saber qual é a próxima ação |
| Para | conduzir relacionamento e venda com continuidade |
| Sem | reconstruir informação em múltiplos lugares ou depender da memória |

### 5.2. Gerente

| Elemento | Definição |
| --- | --- |
| Quando | preciso acompanhar a equipe comercial |
| Quero | saber quais clientes estão sendo trabalhados, quais precisam de atenção e o que aconteceu |
| Para | orientar a equipe e tomar decisões com informação objetiva |
| Sem | depender apenas de relatos, planilhas e cobranças manuais |

---

## 6. Promessa de valor

> **Dar ao comercial um único contexto de trabalho para saber quem atender, o que já aconteceu e o que fazer a seguir, mantendo o Protheus como autoridade das operações ERP.**

Essa promessa funciona como filtro de escopo.

Uma capacidade que não contribui de forma relevante para essa promessa precisa justificar por que pertence ao horizonte atual.

---

## 7. Posicionamento

Para a equipe comercial da empresa, que hoje trabalha entre Protheus, planilhas, WhatsApp e controles individuais, o produto é uma camada de CRM operacional integrada ao ERP que organiza carteira, contexto e próxima ação.

Ele não pretende competir com o Protheus como ERP nem reproduzir uma suíte genérica de CRM com módulos que a empresa não necessita.

Sua diferenciação pretendida é:

```text
ADERÊNCIA AO PROCESSO REAL
+
INTEGRAÇÃO COM PROTHEUS
+
EXPERIÊNCIA COMERCIAL ENXUTA
+
REDUÇÃO DE DUPLA OPERAÇÃO
```

---

## 8. Princípios de produto

### P-PROD-01 — Comercial antes de suíte

O produto deve resolver profundamente o trabalho comercial necessário antes de ampliar quantidade de módulos.

### P-PROD-02 — Uma informação, uma autoridade

Quando uma informação pertence canonicamente ao Protheus, o CRM não deve criar uma segunda verdade silenciosa.

### P-PROD-03 — Registrar deve custar menos do que esquecer

Se manter o CRM atualizado gerar esforço percebido maior que o benefício, o produto tende a repetir a falha da tentativa anterior do cliente com CRM sem integração suficiente.

### P-PROD-04 — Contexto antes de relatório

O valor primário nasce no trabalho diário do vendedor. Relatórios e dashboards apoiam o core; não o substituem.

### P-PROD-05 — Histórico pertence à empresa

O histórico comercial corporativo deve permanecer disponível mesmo quando um vendedor deixa a organização.

### P-PROD-06 — Build precisa continuar justificável

Se custo, TCO, complexidade ou integração invalidarem o business case, a decisão de desenvolver sob medida deve ser reaberta.

### P-PROD-07 — Informação sensível é proporcional ao papel

A necessidade de trazer informação financeira ou operacional ao contexto comercial não significa acesso irrestrito. O produto deve preservar o princípio de menor exposição necessária ao trabalho de cada perfil.

---

## 9. Loop principal

O loop principal do vendedor é:

```text
ENTRAR
↓
VER O QUE PRECISA DE ATENÇÃO
↓
ABRIR CLIENTE OU PROSPECT
↓
COMPREENDER CONTEXTO
↓
EXECUTAR CONTATO OU AÇÃO
↓
REGISTRAR RESULTADO
↓
DEFINIR PRÓXIMA AÇÃO
↓
ACOMPANHAR
↓
RETORNAR NO MOMENTO CERTO
```

Um loop de apoio relevante é:

```text
ABRIR CLIENTE
↓
CONSULTAR CONTEXTO DE PEDIDO / COMPRA
↓
RESPONDER OU DECIDIR A PRÓXIMA AÇÃO
```

O segundo loop não deve transformar o produto em interface paralela completa do ERP.

---

## 10. Hierarquia de valor

| Ordem | Camada | Regra |
| --- | --- | --- |
| 1 | Trabalho comercial diário | Core do produto; deve dominar prioridade e experiência |
| 2 | Contexto do cliente | Permite boa decisão e continuidade |
| 3 | Próxima ação / follow-up | Impede perda de continuidade |
| 4 | Integração Protheus | Remove fragmentação e dupla operação |
| 5 | Visão gerencial | Permite acompanhamento e decisão |
| 6 | Analytics avançado | Só após core demonstrar valor |
| 7 | Automação avançada | Evolução condicionada a dados e adoção |

---

## 11. Escopo P0 — horizonte atual

P0 é o contrato de produto deste horizonte. Não representa ordem de implementação nem autorização de código.

### P0.1. Identidade e acesso

O produto precisa distinguir, no mínimo, responsabilidades de:

- vendedor;
- gerente comercial;
- diretor comercial;
- administração necessária do sistema.

O mecanismo de autenticação e autorização será definido posteriormente.

### P0.2. Clientes e prospects

O produto precisa permitir:

- localizar cliente;
- localizar prospect;
- criar prospect;
- reconhecer cliente existente;
- diferenciar prospect de cliente formal;
- vincular cliente efetivo ao registro canônico do Protheus;
- visualizar contexto comercial necessário.

### P0.3. Carteira comercial

O produto precisa permitir:

- conhecer o responsável por determinado cliente;
- vendedor trabalhar sua própria carteira;
- gerente e diretor possuírem visão ampliada compatível com suas responsabilidades;
- evitar cadastro duplicado;
- descoberta controlada de cliente pertencente a outra carteira;
- transferência controlada de responsabilidade.

A regra detalhada de permissões pertence às etapas posteriores.

### P0.4. Histórico comercial

O produto precisa registrar eventos comerciais relevantes, como:

- contato;
- ligação;
- visita;
- interação via WhatsApp;
- observação comercial;
- proposta ou negociação;
- outros eventos aprovados posteriormente.

O histórico deve permitir identificar, quando aplicável:

- autor;
- momento;
- tipo de interação;
- contexto registrado.

### P0.5. Próxima ação e retorno

O vendedor precisa conseguir registrar uma próxima ação para data futura e reencontrá-la no fluxo de trabalho sem depender exclusivamente de memória ou agenda paralela.

O P0 não inclui uma agenda corporativa completa.

### P0.6. Clientes que precisam de atenção

O produto deve sinalizar clientes potencialmente negligenciados ou que merecem ação comercial.

O Briefing não canoniza um número fixo de dias.

A regra poderá considerar, posteriormente, ausência de compra, ausência de contato, frequência histórica ou outro critério aprovado.

### P0.7. Contexto do Protheus

O CRM deve trazer ao contexto comercial informações necessárias relativas a:

- cadastro formal do cliente;
- histórico de compras;
- pedidos;
- situação relevante de pedido;
- faturamento relevante;
- estoque quando necessário ao trabalho comercial;
- informações financeiras estritamente necessárias à decisão comercial aprovada.

Isso não autoriza replicar integralmente módulos do Protheus.

### P0.8. Visão gerencial mínima

Gerente e diretor precisam possuir visão suficiente para acompanhar:

- situação das carteiras;
- atividade comercial;
- clientes que precisam de atenção;
- retornos;
- contexto necessário para gestão.

O Briefing não define ainda quais gráficos, dashboards ou componentes serão usados.

### P0.9. Desktop e mobile

O produto precisa ser utilizável em desktop e em contexto móvel.

Isso não canoniza:

- aplicativo nativo;
- framework;
- PWA;
- estratégia offline-first.

### P0.10. Auditabilidade operacional mínima

Ações comerciais materiais devem permitir identificar autoria e momento quando isso for necessário para preservar histórico, confiança e gestão.

---

## 12. P1 — após validação do core

Podem ser considerados após sinais de adoção, dados ou dependências:

- dashboards gerenciais avançados;
- métricas de produtividade comercial refinadas;
- importação estruturada de históricos úteis de planilhas;
- automações comerciais adicionais;
- regras mais sofisticadas de atenção de carteira;
- canais adicionais de entrada de leads;
- propostas e anexos mais estruturados;
- integração mais profunda com WhatsApp;
- automações de conversão prospect → cliente no Protheus;
- criação ou pré-criação de pedido pelo CRM, caso a necessidade seja confirmada.

Nenhum item P1 está implicitamente autorizado por existir nesta lista.

---

## 13. P2 — maturidade

Possibilidades futuras, sem compromisso atual:

- inteligência de carteira;
- recomendações comerciais;
- priorização preditiva;
- previsão comercial avançada;
- automação baseada em dados históricos maduros;
- integrações adicionais;
- novos módulos derivados de necessidade comprovada.

---

## 14. Fora de escopo

No horizonte atual ficam explicitamente fora de escopo:

- reconstrução de ERP completo;
- financeiro completo;
- fiscal;
- emissão de nota fiscal;
- faturamento transacional;
- estoque transacional;
- contabilidade;
- folha;
- compras;
- helpdesk completo;
- marketing automation completo;
- agenda corporativa completa;
- mensageria WhatsApp completa no P0;
- offline completo no P0;
- BI corporativo genérico;
- replicação de todas as telas ou rotinas do Protheus.

Regra canônica:

> **Não reconstruir no CRM uma tela equivalente para cada rotina do Protheus apenas porque a informação existe no ERP.**

---

## 15. Regras de produto críticas

### BRIEF-RULE-01 — Autoridade do Protheus

O Protheus continua sendo autoridade para dados e operações ERP definidos como canônicos naquele sistema.

### BRIEF-RULE-02 — Prospect antes de cliente

Prospect pode existir no CRM antes de existir cliente formal no Protheus.

### BRIEF-RULE-03 — Vínculo inequívoco

Cliente formal deve possuir vínculo inequívoco com o registro correspondente do Protheus.

### BRIEF-RULE-04 — Descoberta controlada

Vendedor pode descobrir que determinado cliente já existe sem receber automaticamente acesso irrestrito ao relacionamento de outra carteira.

### BRIEF-RULE-05 — Visão gerencial

Gerente e diretor possuem visão compatível com sua responsabilidade, sujeita às regras de acesso aprovadas.

### BRIEF-RULE-06 — Continuidade do histórico

Histórico comercial corporativo não depende da permanência do vendedor que o registrou.

### BRIEF-RULE-07 — Sem duplicação desnecessária

O CRM não deve exigir duplicação sistemática de informação já mantida no Protheus quando essa duplicação não acrescenta valor comercial legítimo.

### BRIEF-RULE-08 — Atenção não é “60 dias”

“Cliente que precisa de atenção” é um conceito de produto. Sua regra não será fixada arbitrariamente antes de validação.

### BRIEF-RULE-09 — Build condicionado ao business case

O caminho custom permanece condicionado ao business case aprovado.

### BRIEF-RULE-10 — Informação financeira mínima necessária

Trazer informação financeira ao CRM não significa expor todo o financeiro. Cada perfil deve receber somente o contexto aprovado e necessário à atividade comercial.

---

## 16. Requisitos de qualidade no nível de produto

### Simplicidade

A tarefa comercial principal deve reduzir alternância de contexto em comparação ao processo atual.

### Confiabilidade

Histórico e próxima ação não podem desaparecer silenciosamente após falhas comuns.

### Segurança

Usuários devem acessar apenas contexto compatível com sua responsabilidade e carteira.

### Auditabilidade

Ações materiais precisam permitir saber quem fez e quando, quando essa informação for relevante para o negócio.

### Privacidade

Dados pessoais e observações comerciais devem permanecer limitados ao necessário para finalidades definidas.

### Mobilidade

A experiência precisa atender vendedores em campo.

### Tolerância a conectividade ruim

A experiência deve lidar de forma segura e compreensível com falhas comuns de conexão.

Essa expectativa não equivale a requisito de operação offline completa.

---

## 17. Métricas de produto

### 17.1. Métrica norte preliminar

> **Percentual da carteira ativa que possui contexto comercial atualizado e próxima ação conhecida quando aplicável.**

Essa métrica conecta carteira, histórico e continuidade.

### 17.2. Métricas complementares

- follow-ups vencidos;
- clientes sem interação por período relevante;
- tempo para obter contexto de pedido;
- horas mensais associadas à operação fragmentada;
- uso de controles paralelos pelos vendedores;
- tempo para reconstrução de carteira após mudança de responsável;
- adesão ao registro comercial;
- taxa de clientes sem próxima ação quando deveriam possuir uma.

### 17.3. Métrica econômica

A Pesquisa registrou uma baseline inicial aproximada de 234 horas/mês associadas à fragmentação operacional.

O objetivo econômico preliminar é reduzir aproximadamente 50% do esforço atacável para manter o business case próximo da faixa de payback considerada aceitável pelo cliente.

Esse percentual permanece uma hipótese a medir, não promessa garantida.

---

## 18. Gates de produto

### G-PROD-01 — Ambiente Protheus conhecido

**Condição de saída:** release, customizações, estrutura relevante de empresa/filial, integrações e contratos reais do ambiente foram inventariados em profundidade suficiente para orientar as decisões técnicas posteriores.

**Libera:** decisões técnicas concretas sobre integração.

### G-PROD-02 — Adoção sem dupla operação

**Condição de saída:** piloto demonstra que o fluxo integrado reduz, e não aumenta, a necessidade de duplicar trabalho entre CRM e Protheus.

**Libera:** ampliação da adoção.

### G-PROD-03 — Baseline econômica validada

**Condição de saída:** estimativa de aproximadamente 234 horas/mês foi confrontada com medição suficiente da operação real.

**Libera:** uso da baseline como referência financeira mais confiável.

### G-PROD-04 — TCO reconciliado

**Condição de saída:** custo atualizado de construção e operação permanece compatível com o business case aprovado.

**Libera:** continuidade do caminho custom.

### G-PROD-05 — Payback aceitável

**Condição de saída:** payback projetado permanece dentro do limite aceito pelo cliente ou existe nova decisão humana explícita.

**Regra de retorno:** se o payback ultrapassar materialmente aproximadamente 18 meses, build-vs-buy deve ser reaberto.

### G-PROD-06 — Privacidade e acesso

**Condição de saída:** finalidades, acesso e tratamento de dados pessoais e observações comerciais estão definidos em nível suficiente antes do uso de dados reais.

**Libera:** operação com dados reais conforme gates posteriores.

---

## 19. Dependências externas e organizacionais

### TOTVS Protheus

Dependências conhecidas:

- release real;
- customizações;
- contratos de integração;
- APIs e serviços disponíveis;
- estrutura de empresa/grupo/filial;
- campos customizados;
- regras específicas de pedido e liberação.

### Dados legados

Dependências:

- qualidade da base;
- duplicidades;
- identificadores;
- utilidade de históricos existentes;
- possibilidade de saneamento.

### Cliente / TI

Dependências:

- acesso ao ambiente adequado;
- disponibilidade de responsáveis;
- documentação de customizações;
- validação de regras e dados.

### Business case

Dependências:

- baseline operacional;
- custos;
- TCO atualizado;
- medição de ganhos.

Regra:

```text
PLANEJADO
≠
DISPONÍVEL
≠
APROVADO
≠
VERIFICADO
```

---

## 20. Riscos e postura de produto

| Risco | Postura | Tratamento esperado |
| --- | --- | --- |
| Customização do Protheus exigir trabalho adicional | Aceito com condição | inventário e gate técnico |
| Primeira versão não cobrir toda a operação comercial | Aceito | preservar foco no core |
| P0 não possuir offline completo | Aceito | tratar conectividade de forma segura e avaliar necessidade real |
| Automação avançada ficar para P1/P2 | Aceito | não bloquear core |
| Vendedor precisar duplicar sistematicamente CRM + Protheus | Não aceito | reavaliar fluxo e integração |
| CRM transformar-se em segundo ERP | Não aceito | aplicar fora de escopo e regra de autoridade |
| Business case deixar de fechar e projeto continuar por inércia | Não aceito | reabrir build-vs-buy |
| Dados de carteira serem expostos sem justificativa | Não aceito | regras de acesso e gate de segurança |
| Histórico corporativo desaparecer com desligamento | Não aceito | preservar continuidade e auditabilidade |

---

## 21. Decisões ainda abertas

As seguintes decisões permanecem intencionalmente fora deste documento:

- regra final para “cliente que precisa de atenção”;
- profundidade exata de estoque no CRM;
- profundidade exata das informações financeiras;
- conversão automática prospect → cliente Protheus;
- eventual criação de pedido pelo CRM;
- mecanismo de sincronização;
- mecanismo técnico de integração;
- tecnologia web/mobile;
- estratégia de offline;
- banco de dados;
- cloud;
- framework;
- design visual;
- navegação;
- modelo detalhado de permissões;
- política detalhada de retenção;
- ordem de implementação.

Esses itens devem ser resolvidos pelas camadas posteriores que possuam autoridade sobre o tema.

---

## 22. Decisões consolidadas

| Tema | Decisão | Implicação |
| --- | --- | --- |
| Produto | CRM comercial enxuto integrado ao Protheus | evitar suíte genérica e segundo ERP |
| Público | vendedores, gerentes e diretor comercial | experiência e regras precisam refletir responsabilidades distintas |
| ERP | Protheus permanece autoridade transacional | CRM consome contexto, não reimplementa ERP |
| Core | carteira + contexto + histórico + próxima ação | deve dominar prioridade do P0 |
| Mobile | uso móvel é obrigatório como contexto | solução técnica permanece aberta |
| WhatsApp | integração profunda fora do P0 | não bloquear core por mensageria |
| Offline | offline completo não é requisito P0 | tratar conexão ruim sem antecipar arquitetura |
| Build vs buy | custom aprovado condicionalmente | reabrir se TCO/payback não fecharem |
| Métrica econômica | redução de esforço operacional atacável | baseline e benefício precisam ser medidos |
| Dados financeiros | somente contexto necessário | acesso irrestrito não é permitido por padrão |

---

## 23. Product Scope Freeze

Para este horizonte, o Product Scope Freeze estabelece:

```text
CORE
=
CARTEIRA
+
CLIENTE / PROSPECT
+
HISTÓRICO
+
PRÓXIMA AÇÃO
+
CONTEXTO PROTHEUS
+
VISÃO GERENCIAL MÍNIMA
+
ACESSO DESKTOP / MOBILE
```

Qualquer proposta que adicione módulos materiais fora desse recorte precisa indicar:

- qual problema resolve;
- por que pertence ao P0;
- qual impacto possui no business case;
- qual documento possui autoridade para aprovar a mudança.

O Product Scope Freeze não impede evolução; impede expansão silenciosa.

---

## 24. Handoff para Visão de Product Owner

A próxima etapa deve transformar este contrato em:

- outcomes;
- comportamentos de valor;
- regras detalhadas de negócio;
- hipóteses;
- personas comportamentais quando úteis;
- capacidades e épicos;
- histórias de produto;
- critérios de aceite;
- prioridades;
- ondas de aprendizado e liberação;
- métricas e guardrails;
- gates e owners;
- Definition of Ready e Definition of Done de produto.

A Visão de Product Owner não pode reabrir silenciosamente o Product Scope Freeze nem canonizar arquitetura, stack, UX visual ou infraestrutura.

---

## 25. Estado de saída

```text
BRIEFING_EXECUTION: COMPLETE
CLIENT_REVIEW: APPROVED_WITH_REFINEMENT
PRODUCT_DEFINITION: STABLE
P0_BOUNDARY: STABLE
OUT_OF_SCOPE: STABLE
PROTHEUS_ROLE: STABLE
BUILD_VS_BUY_GUARDRAIL: STABLE
BRIEFING_READINESS: SUFFICIENT
NEXT_STAGE: 03 — Visão de Product Owner
```

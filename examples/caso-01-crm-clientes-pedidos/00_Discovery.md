---
document_id: CASE-01-DOC-00
title: Discovery — CRM para gestão de clientes e pedidos
status: canonical
version: 1.0.0
case_id: CASE-01-CRM-CLIENTES-PEDIDOS
methodology_stage: discovery
next_document: 01_Pesquisa_e_Viabilidade.md
discovery_readiness: SUFFICIENT_WITH_OPEN_QUESTIONS
---

# Discovery — CRM para gestão de clientes e pedidos

## 1. Contexto e origem da ideia

Uma empresa contratou uma consultoria para criar um CRM próprio para apoiar sua operação comercial.

Antes da ativação formal do processo, um analista da consultoria realizou uma entrevista inicial com stakeholders do cliente e trouxe anotações sobre necessidades percebidas. O processo foi então ativado para transformar essas anotações em contexto de produto suficientemente claro antes de qualquer pesquisa, definição de escopo, arquitetura ou implementação.

A operação comercial atual utiliza uma combinação de:

- planilhas;
- WhatsApp;
- anotações individuais;
- informações disponíveis no ERP;
- conhecimento mantido informalmente por cada vendedor.

O cliente possui atualmente cerca de 18 vendedores, 2 gerentes comerciais e 1 diretor comercial. Existem aproximadamente 12 mil clientes cadastrados no ERP e duas filiais que trabalham de forma comercialmente integrada.

Os vendedores atuam também em campo, portanto acesso por celular é um contexto de uso relevante.

---

## 2. Problema ou oportunidade percebida

O problema central identificado no Discovery não é simplesmente a ausência de um software chamado CRM.

A operação comercial está fragmentada entre diferentes ferramentas e práticas pessoais. Como consequência:

- o histórico de relacionamento não pertence de forma confiável à empresa;
- cada vendedor organiza sua carteira de maneira própria;
- a gestão não possui visibilidade consolidada sobre clientes trabalhados, clientes esquecidos e atividades realizadas;
- parte do conhecimento pode ser perdida quando um vendedor deixa a empresa;
- vendedores precisam consultar múltiplos lugares para compreender a situação de um cliente;
- o acompanhamento de retornos depende excessivamente da memória ou organização individual;
- informações comerciais e informações do ciclo do pedido estão separadas.

A oportunidade é criar uma camada operacional comercial que preserve o relacionamento com o cliente, reduza dependência de controles individuais e disponibilize contexto suficiente para vendedor e gestão trabalharem com informação compartilhada e rastreável.

---

## 3. Tese inicial do produto

Criar um CRM próprio para centralizar relacionamento comercial, carteira, histórico de interações, retornos e contexto de compras/pedidos, mantendo o ERP como autoridade dos processos transacionais, fiscais, financeiros, de estoque e faturamento.

A tese atual pode ser resumida como:

> permitir que o comercial trabalhe o relacionamento com clientes e prospects em um ambiente próprio, sem transformar o CRM em substituto do ERP.

---

## 4. Usuários e stakeholders imaginados

### 4.1. Vendedor

Usuário operacional principal.

Necessita:

- acompanhar sua carteira;
- consultar clientes e prospects;
- registrar interações;
- lembrar retornos;
- localizar rapidamente informações relevantes;
- consultar histórico de compras e situação de pedidos;
- identificar que um cliente já existe mesmo quando pertence a outra carteira.

### 4.2. Gerente comercial

Necessita:

- visualizar atividade da equipe;
- acompanhar todas as carteiras sob sua gestão;
- identificar clientes negligenciados;
- consultar histórico comercial;
- transferir carteira quando necessário;
- utilizar informação objetiva para gestão da equipe.

### 4.3. Diretor comercial

Stakeholder decisor.

Necessita:

- visão consolidada da operação comercial;
- redução de clientes esquecidos;
- preservação do histórico da empresa;
- redução da dependência de planilhas e controles individuais;
- menor dependência do ERP para tarefas puramente comerciais.

### 4.4. Outros stakeholders

Podem participar futuramente:

- equipe responsável pelo ERP;
- TI da empresa;
- responsáveis por cadastro de clientes;
- áreas que influenciam status de pedido, entrega ou crédito.

Esses perfis ainda precisam ser refinados nas etapas posteriores.

---

## 5. Situações de uso conhecidas

### Prospecção

Quando surge uma nova empresa ou contato comercial, o vendedor precisa registrar o prospect e acompanhar sua evolução mesmo antes de existir um cadastro formal no ERP.

### Relacionamento

Quando o vendedor liga, visita, envia mensagem, apresenta proposta ou combina um retorno, precisa registrar o que ocorreu para que o histórico permaneça disponível à empresa.

### Retorno comercial

Quando um vendedor combina uma nova ação para uma data futura, precisa ser lembrado de forma simples sem depender exclusivamente da memória ou de uma agenda paralela.

### Gestão de carteira

O vendedor precisa trabalhar prioritariamente sua própria carteira. A gestão precisa conseguir enxergar a operação completa.

### Prevenção de duplicidade

Quando um vendedor encontra uma empresa que já pertence a outra carteira, precisa conseguir identificar que o cliente existe e quem é o responsável, mesmo sem ter acesso irrestrito ao histórico comercial daquela carteira.

### Cliente negligenciado

A gestão e o vendedor precisam conseguir identificar clientes que merecem atenção por ausência de compra ou contato, sem assumir ainda uma regra fixa de inatividade.

### Consulta de pedidos

Quando o cliente pergunta sobre um pedido, o vendedor precisa visualizar informações relevantes do ciclo do pedido sem utilizar o CRM para faturar, controlar estoque, emitir nota ou substituir o ERP.

### Histórico de compras

Ao abrir um cliente, vendedor e gestão precisam consultar seu histórico de compras para compreender o relacionamento comercial.

### Uso em campo

O vendedor precisa conseguir acessar informações relevantes também por celular. Há possibilidade de conexão instável em campo, mas operação offline completa ainda não foi confirmada como requisito.

---

## 6. Valor e outcomes esperados

O cliente considera o projeto bem-sucedido se conseguir:

- reduzir clientes esquecidos;
- preservar histórico comercial mesmo quando um vendedor sai da empresa;
- reduzir dependência de planilhas;
- dar à gestão visibilidade real sobre o trabalho comercial;
- permitir cobrança e acompanhamento da equipe com base em informação registrada;
- reduzir o número de lugares que o vendedor precisa consultar;
- encontrar informações comerciais e de pedidos com maior rapidez;
- manter o ERP focado em suas responsabilidades transacionais sem obrigar o comercial a utilizá-lo para tudo.

---

## 7. Capacidades centrais imaginadas

As capacidades abaixo representam intenção atual, não backlog definitivo:

- cadastro e consulta de prospects;
- consulta de clientes existentes;
- vínculo entre cliente efetivo e cadastro do ERP;
- carteira de clientes por vendedor;
- descoberta controlada de clientes de outras carteiras;
- histórico de interações comerciais;
- linha do tempo do cliente;
- registro de autor e data das interações;
- tarefas simples de retorno;
- visão gerencial ampliada;
- transferência controlada de carteira;
- identificação de clientes que precisam de atenção;
- consulta do histórico de compras;
- consulta de pedidos e seus estados relevantes;
- acesso por computador e celular;
- apoio ao fluxo de uso do WhatsApp sem assumir integração profunda no primeiro horizonte.

---

## 8. Limites preliminares e não objetivos

No horizonte inicial, o CRM não pretende substituir o ERP.

Permanecem fora da responsabilidade pretendida do CRM:

- estoque;
- crédito;
- financeiro;
- faturamento;
- emissão fiscal;
- nota fiscal;
- processo transacional canônico do pedido;
- gestão completa de agenda corporativa.

Também não está decidido que o CRM deverá:

- importar automaticamente todas as conversas do WhatsApp;
- operar integralmente offline;
- criar automaticamente clientes no ERP;
- gerar pedidos diretamente;
- definir cliente inativo por uma regra fixa de 60 dias.

---

## 9. Restrições conhecidas

- o ERP deve continuar sendo a autoridade para dados transacionais, fiscais, financeiros, de estoque, crédito e faturamento;
- alterações comerciais no CRM não podem criar divergência silenciosa em dados cuja autoridade pertence ao ERP;
- clientes efetivos devem possuir vínculo com o cadastro canônico do ERP;
- prospects podem existir no CRM antes desse vínculo;
- vendedores não devem possuir acesso irrestrito ao histórico de carteiras alheias;
- gerente e diretor precisam de visão ampliada;
- o sistema deverá considerar contexto de uso móvel em campo;
- existem duas filiais, mas a equipe comercial opera de forma integrada;
- o ERP utilizado pelo cliente ainda não foi identificado neste estágio;
- orçamento e prazo de implantação ainda não foram confirmados.

---

## 10. Ativos, referências e processos existentes

Ativos e processos conhecidos:

- ERP atual da empresa;
- base de aproximadamente 12 mil clientes;
- planilhas utilizadas por vendedores;
- históricos e contatos mantidos em WhatsApp;
- controles individuais mantidos por vendedores;
- processo atual de lançamento de pedido no ERP;
- possível histórico comercial distribuído em diferentes fontes.

A qualidade, estrutura e possibilidade de reaproveitamento desses ativos ainda precisam ser avaliadas.

---

## 11. Decisões confirmadas

1. O CRM será uma camada de trabalho comercial, não substituto do ERP.
2. Estoque, crédito, financeiro, faturamento, fiscal e pedido transacional permanecem no ERP no horizonte inicial.
3. Prospects podem existir no CRM antes de se tornarem clientes formais.
4. Clientes efetivos terão vínculo com o cadastro do ERP.
5. O histórico comercial deve permanecer pertencente à empresa e sobreviver à saída de vendedores.
6. Vendedores trabalham com carteiras.
7. Gerente e diretor precisam de visão ampliada sobre a operação.
8. Um vendedor precisa conseguir descobrir que determinado cliente já existe para evitar duplicidade.
9. Descobrir a existência de cliente de outra carteira não significa liberar acesso irrestrito ao histórico daquela carteira.
10. Transferência de carteira deve ocorrer de forma controlada pela gestão.
11. Retornos simples fazem parte da necessidade inicial.
12. Histórico de compras e contexto de pedidos precisam estar disponíveis no CRM.
13. Uso móvel é contexto real de operação.
14. Integração profunda com WhatsApp não é requisito confirmado para o primeiro horizonte.

---

## 12. Hipóteses a validar

- qual mecanismo identifica melhor clientes que precisam de atenção;
- se frequência histórica de compra deve influenciar essa identificação;
- profundidade necessária da integração CRM ↔ ERP;
- possibilidade e valor de criação automática de cliente no ERP;
- necessidade futura de criação de pedido pelo CRM;
- necessidade real de operação offline;
- dashboards que de fato ajudam gestão comercial;
- benefício e custo de integração profunda com WhatsApp;
- quais dados de pedido precisam ser replicados, sincronizados ou apenas consultados;
- impacto real das duas filiais nas regras de carteira e permissão;
- se o volume e qualidade das informações existentes permitem migração útil do histórico comercial.

---

## 13. Pendências

- identificar ERP e capacidades oficiais de integração;
- avaliar qualidade e duplicidade da base de clientes;
- confirmar identificador estável do cliente no ERP;
- conhecer volume médio de pedidos e frequência de atualização necessária;
- confirmar requisitos de LGPD, retenção e acesso às observações comerciais;
- entender como leads do site chegam hoje;
- verificar necessidade de anexos e propostas;
- confirmar orçamento;
- confirmar horizonte esperado de implantação;
- avaliar importação de planilhas existentes;
- identificar informações comerciais consideradas confidenciais;
- verificar se existem usuários externos ou apenas colaboradores da empresa.

---

## 14. Alternativas descartadas

No horizonte atual foram conscientemente descartadas como premissas:

- substituir o ERP;
- transformar o CRM em sistema fiscal ou financeiro;
- tratar CRM como sistema principal de estoque ou faturamento;
- construir agenda corporativa completa como necessidade inicial;
- assumir integração profunda com WhatsApp sem validação;
- assumir operação offline completa antes de comprovar necessidade;
- fixar arbitrariamente cliente inativo como 60 dias sem considerar contexto comercial.

---

## 15. Ideias futuras não comprometidas

Podem ser investigadas posteriormente, sem compromisso de implementação:

- integração mais profunda com WhatsApp;
- criação de clientes no ERP a partir do CRM;
- criação ou pré-criação de pedidos pelo CRM;
- automações comerciais;
- classificação mais inteligente de clientes que precisam de atenção;
- dashboards avançados;
- integrações adicionais com canais de entrada de leads.

---

## 16. Perguntas para Pesquisa e Viabilidade

### Problema e adoção

- O conjunto de problemas identificado é coerente com padrões conhecidos de uso de CRM e gestão comercial?
- Quais capacidades realmente resolvem perda de histórico, falta de acompanhamento e baixa visibilidade sem criar excesso de escopo?

### Mercado e referências

- Como CRMs consolidados organizam carteira, atividades, tarefas, timeline, dashboards e histórico de relacionamento?
- Quais capacidades aparecem como baseline de categoria e quais são diferenciais desnecessários para este caso?

### ERP

- Quais caminhos de integração seriam possíveis após identificar o ERP?
- Quais decisões devem permanecer bloqueadas enquanto o fornecedor e suas APIs não forem conhecidos?

### WhatsApp

- Quais possibilidades oficiais existem para integração com WhatsApp Business Platform?
- Que custos, políticas, consentimentos e complexidades tornam uma integração profunda inadequada ou adequada ao primeiro horizonte?

### Dados e privacidade

- Quais obrigações da LGPD são relevantes para cadastro de contatos, histórico de interação, anotações comerciais e eventuais dados pessoais?
- Quais princípios de minimização, finalidade, acesso e retenção precisam ser considerados desde o produto?

### Mobile e conectividade

- A necessidade de uso móvel pode ser atendida sem assumir imediatamente uma estratégia offline completa?
- Que cenários reais justificariam investimento posterior em comportamento offline?

### Migração

- Que riscos devem ser avaliados antes de migrar base de clientes, planilhas e históricos dispersos?

### Viabilidade operacional

- O escopo inicial pode ser recortado de forma que gere valor antes de integrações complexas?
- Quais dependências externas podem bloquear o primeiro release?

---

## 17. Discovery Readiness e handoff

```text
DISCOVERY_READINESS: SUFFICIENT_WITH_OPEN_QUESTIONS
```

O Discovery é suficiente para Pesquisa e Viabilidade porque:

- a intenção do produto está clara;
- o problema central foi separado das soluções inicialmente sugeridas;
- usuários e contextos principais foram identificados;
- o papel do ERP foi delimitado no nível de intenção;
- necessidades de carteira, histórico, retorno, pedidos e gestão foram esclarecidas;
- hipóteses e pendências permanecem explícitas;
- não houve escolha prematura de stack, arquitetura, provider ou mecanismo de integração.

As perguntas abertas não impedem a pesquisa. Ao contrário, constituem sua agenda inicial.

A próxima etapa deve consumir integralmente este documento e confrontar suas hipóteses com evidências externas e materiais disponíveis.

```text
NEXT_STAGE: 01 — Pesquisa e Viabilidade
```

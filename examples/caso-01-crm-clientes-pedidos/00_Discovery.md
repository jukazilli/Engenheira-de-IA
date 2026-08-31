---
document_id: CASE-01-DOC-00
title: Discovery — CRM para gestão de clientes e pedidos
status: canonical
version: 1.1.0
case_id: CASE-01-CRM-CLIENTES-PEDIDOS
methodology_stage: discovery
next_document: 01_Pesquisa_e_Viabilidade.md
discovery_readiness: SUFFICIENT
---

# Discovery — CRM para gestão de clientes e pedidos

## 1. Contexto e origem da ideia

Uma empresa contratou uma consultoria para avaliar e conduzir a criação de uma solução de CRM para apoiar sua operação comercial.

Antes da ativação formal do processo, um analista da consultoria realizou uma entrevista inicial com stakeholders do cliente e trouxe anotações sobre necessidades percebidas. Durante o Discovery, essas anotações foram aprofundadas por perguntas simuladas ao diretor comercial, gerente comercial, vendedores e responsável de TI.

A operação comercial atual utiliza uma combinação de:

- planilhas;
- WhatsApp;
- anotações individuais;
- informações disponíveis no ERP TOTVS Protheus;
- conhecimento mantido informalmente por cada vendedor.

O cliente possui atualmente cerca de 18 vendedores, 2 gerentes comerciais e 1 diretor comercial. Existem aproximadamente 12 mil clientes cadastrados no Protheus e duas filiais que trabalham de forma comercialmente integrada.

Os vendedores atuam também em campo, portanto acesso por celular é um contexto de uso relevante.

O cliente procurou a consultoria inicialmente falando em construir um CRM próprio, porém durante o Discovery confirmou que não considera software sob medida um objetivo em si. Se uma solução existente conseguir resolver adequadamente o processo, integrar-se ao Protheus e apresentar custo total mais favorável, ela pode ser considerada.

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
- informações comerciais e informações do ciclo do pedido estão separadas;
- CRM e ERP podem se transformar em duplicidade operacional quando não existe integração adequada.

O cliente relatou tentativa anterior de uso do Pipedrive por um grupo de vendedores. Segundo o cenário, a baixa integração com o Protheus obrigava o usuário a manter dados no CRM e depois operar novamente no ERP, contribuindo para abandono da ferramenta. HubSpot também já foi avaliado em demonstração, sem implantação.

Essa experiência é evidência interna do cliente, não prova de que as versões atuais desses produtos sejam inadequadas.

A oportunidade é estabelecer uma camada operacional comercial que preserve o relacionamento com o cliente, reduza dependência de controles individuais e disponibilize contexto suficiente para vendedor e gestão trabalharem com informação compartilhada e rastreável, sem reproduzir indevidamente as responsabilidades do ERP.

---

## 3. Tese inicial do produto

A tese inicial é disponibilizar uma solução de CRM integrada ao TOTVS Protheus para centralizar relacionamento comercial, carteira, histórico de interações, retornos e contexto de compras/pedidos, mantendo o Protheus como autoridade dos processos transacionais.

A tese atual pode ser resumida como:

> permitir que o comercial trabalhe o relacionamento com clientes e prospects em um ambiente adequado à sua rotina, reduzindo duplicidade operacional e mantendo o Protheus como sistema transacional de referência.

O Discovery não canoniza ainda se essa solução deverá ser:

- um CRM de mercado;
- um CRM de mercado integrado/customizado;
- uma solução sob medida.

Essa decisão deve ser confrontada na Pesquisa e Viabilidade.

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
- identificar que um cliente já existe mesmo quando pertence a outra carteira;
- reduzir alternância entre CRM, planilhas, WhatsApp e Protheus.

### 4.2. Gerente comercial

Necessita:

- visualizar atividade da equipe;
- acompanhar todas as carteiras sob sua gestão;
- identificar clientes negligenciados;
- consultar histórico comercial;
- transferir carteira quando necessário;
- utilizar informação objetiva para gestão da equipe;
- reduzir esforço de cobrança manual e consolidação de informações.

### 4.3. Diretor comercial

Stakeholder decisor.

Necessita:

- visão consolidada da operação comercial;
- redução de clientes esquecidos;
- preservação do histórico da empresa;
- redução da dependência de planilhas e controles individuais;
- menor dependência do Protheus para tarefas puramente comerciais;
- retorno econômico justificável para o investimento.

### 4.4. TI / responsável pelo Protheus

Stakeholder técnico-operacional.

Necessita:

- preservar o Protheus como autoridade dos processos definidos;
- evitar divergências de dados;
- conhecer e controlar os pontos de integração;
- considerar customizações existentes no ambiente;
- confirmar release e capacidades atuais antes de qualquer desenho de integração.

### 4.5. Outros stakeholders

Podem participar posteriormente:

- responsáveis por cadastro de clientes;
- financeiro;
- faturamento;
- estoque;
- áreas que influenciam status de pedido, entrega ou crédito.

---

## 5. Situações de uso conhecidas

### Prospecção

Quando surge uma nova empresa ou contato comercial, o vendedor precisa registrar o prospect e acompanhar sua evolução mesmo antes de existir um cadastro formal no Protheus.

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

Quando o cliente pergunta sobre um pedido, o vendedor precisa visualizar informações relevantes do ciclo do pedido sem utilizar o CRM para faturar, controlar estoque, emitir nota ou substituir o Protheus.

### Histórico de compras

Ao abrir um cliente, vendedor e gestão precisam consultar seu histórico de compras para compreender o relacionamento comercial.

### Consulta operacional ao Protheus

O CRM deverá apoiar o comercial com informações relacionadas a clientes, pedido/faturamento, estoque e informações financeiras necessárias ao processo comercial, sem replicar todas as regras desses módulos.

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
- diminuir duplicidade operacional entre uma ferramenta comercial e o Protheus;
- manter o Protheus focado em suas responsabilidades transacionais;
- justificar economicamente o investimento em horizonte aceitável para a empresa.

### 6.1. Estimativas operacionais declaradas pelo cliente

Durante a entrevista simulada, o cliente estimou:

- aproximadamente 2 horas por semana por vendedor gastas com busca de informações, planilhas, WhatsApp, consultas e reconstrução de contexto;
- 18 vendedores, representando cerca de 36 horas semanais;
- aproximadamente 8 horas por semana para cada um dos 2 gerentes em consolidação, cobrança e acompanhamento, totalizando cerca de 16 horas;
- aproximadamente 2 horas por semana do diretor comercial;
- total aproximado de 54 horas por semana ou cerca de 234 horas por mês relacionadas ao processo fragmentado.

Esses valores são estimativas fornecidas pelo cliente e deverão ser tratados como hipóteses quantitativas até validação.

O cliente também relatou:

- ocorrência recorrente de follow-ups e oportunidades sem acompanhamento adequado;
- impossibilidade atual de mensurar com segurança o valor financeiro das vendas perdidas por falta de registro;
- três desligamentos de vendedores no último ano;
- necessidade de aproximadamente duas semanas para reorganização razoável de uma carteira após saída, com perda definitiva de parte do contexto.

Não existe ainda valor financeiro comprovado para esses efeitos.

---

## 7. Capacidades centrais imaginadas

As capacidades abaixo representam intenção atual, não backlog definitivo:

- cadastro e consulta de prospects;
- consulta de clientes existentes;
- vínculo entre cliente efetivo e cadastro do Protheus;
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
- consulta a informações de estoque necessárias ao comercial;
- consulta a informações financeiras necessárias à decisão comercial, sem transformar o CRM em financeiro;
- acesso por computador e celular;
- apoio ao fluxo de uso do WhatsApp sem assumir integração profunda no primeiro horizonte.

---

## 8. Limites preliminares e não objetivos

No horizonte inicial, a solução de CRM não pretende substituir o TOTVS Protheus.

Permanecem fora da responsabilidade pretendida do CRM:

- gestão canônica de estoque;
- gestão canônica de crédito;
- financeiro;
- faturamento;
- emissão fiscal;
- nota fiscal;
- processo transacional canônico do pedido;
- gestão completa de agenda corporativa.

Também não está decidido que o CRM deverá:

- importar automaticamente todas as conversas do WhatsApp;
- operar integralmente offline;
- criar automaticamente clientes no Protheus;
- gerar pedidos diretamente;
- definir cliente inativo por uma regra fixa de 60 dias;
- ser obrigatoriamente software sob medida.

---

## 9. Restrições conhecidas

- o ERP utilizado é TOTVS Protheus;
- o cliente informou uso do Protheus 12, com release exata ainda pendente de confirmação;
- o ambiente possui customizações;
- o cliente já possui algumas integrações com outros sistemas, mas a forma atual ainda precisa ser levantada;
- o Protheus deve continuar sendo a autoridade para dados e processos transacionais, fiscais, financeiros, de estoque, crédito e faturamento definidos neste horizonte;
- alterações no CRM não podem criar divergência silenciosa em dados cuja autoridade pertence ao Protheus;
- clientes efetivos devem possuir vínculo com o cadastro canônico do Protheus;
- prospects podem existir no CRM antes desse vínculo;
- vendedores não devem possuir acesso irrestrito ao histórico de carteiras alheias;
- gerente e diretor precisam de visão ampliada;
- o sistema deverá considerar contexto de uso móvel em campo;
- existem duas filiais, mas a equipe comercial opera de forma integrada;
- o cliente não exige software próprio se uma solução de mercado resolver adequadamente o problema;
- faixa inicial de investimento que o diretor se dispõe a avaliar: aproximadamente R$ 80 mil a R$ 120 mil;
- payback desejado: até 12 meses;
- payback ainda considerado aceitável dependendo do ganho: aproximadamente até 18 meses;
- custo operacional recorrente deve permanecer controlado.

Os valores financeiros representam critérios declarados pelo cliente e não um orçamento aprovado da consultoria.

---

## 10. Ativos, referências e processos existentes

Ativos e processos conhecidos:

- TOTVS Protheus 12;
- base de aproximadamente 12 mil clientes no Protheus;
- planilhas utilizadas por vendedores;
- históricos e contatos mantidos em WhatsApp;
- controles individuais mantidos por vendedores;
- processo atual de lançamento de pedido no Protheus;
- customizações existentes no ERP;
- integrações já existentes com outros sistemas, ainda não inventariadas;
- tentativa anterior de uso do Pipedrive;
- avaliação anterior do HubSpot em demonstração;
- possível histórico comercial distribuído em diferentes fontes.

A qualidade, estrutura e possibilidade de reaproveitamento desses ativos ainda precisam ser avaliadas.

---

## 11. Decisões confirmadas

1. O problema a resolver é a fragmentação da operação comercial, não simplesmente a ausência de um CRM.
2. O ERP atual é TOTVS Protheus.
3. A solução de CRM será uma camada de trabalho comercial, não substituto do Protheus.
4. Estoque, crédito, financeiro, faturamento, fiscal e pedido transacional permanecem no Protheus no horizonte inicial.
5. A integração deverá considerar dados/processos de clientes, pedidos/faturamento, estoque e informações financeiras necessárias ao comercial.
6. Não se deve replicar toda a lógica dos módulos do Protheus no CRM.
7. Prospects podem existir no CRM antes de se tornarem clientes formais.
8. Clientes efetivos terão vínculo com o cadastro do Protheus.
9. O histórico comercial deve permanecer pertencente à empresa e sobreviver à saída de vendedores.
10. Vendedores trabalham com carteiras.
11. Gerente e diretor precisam de visão ampliada sobre a operação.
12. Um vendedor precisa conseguir descobrir que determinado cliente já existe para evitar duplicidade.
13. Descobrir a existência de cliente de outra carteira não significa liberar acesso irrestrito ao histórico daquela carteira.
14. Transferência de carteira deve ocorrer de forma controlada pela gestão.
15. Retornos simples fazem parte da necessidade inicial.
16. Histórico de compras e contexto de pedidos precisam estar disponíveis no CRM.
17. Uso móvel é contexto real de operação.
18. Integração profunda com WhatsApp não é requisito confirmado para o primeiro horizonte.
19. Construir software próprio não é decisão empresarial imutável; soluções de mercado podem ser consideradas se apresentarem melhor aderência e viabilidade.
20. A decisão deve considerar retorno econômico e custo total, não apenas disponibilidade técnica.

---

## 12. Hipóteses a validar

### Produto e operação

- qual mecanismo identifica melhor clientes que precisam de atenção;
- se frequência histórica de compra deve influenciar essa identificação;
- necessidade real de operação offline;
- dashboards que de fato ajudam gestão comercial;
- impacto real das duas filiais nas regras de carteira e permissão.

### Integração Protheus

- profundidade necessária da integração CRM ↔ Protheus;
- APIs, serviços REST, EAI, conectores ou outros mecanismos disponíveis no release do cliente;
- possibilidade e valor de criação automática de cliente no Protheus;
- necessidade futura de criação de pedido pelo CRM;
- quais dados de pedido precisam ser replicados, sincronizados ou apenas consultados;
- frequência necessária de atualização;
- impacto das customizações existentes;
- necessidade de consultar estoque e financeiro em tempo real ou por sincronização.

### Mercado

- se um CRM comercial atual pode resolver o processo com integração suficiente ao Protheus;
- se TOTVS CRM ou outra solução com maior proximidade do ecossistema Protheus reduz custo e risco;
- se Pipedrive, HubSpot ou alternativas atuais superaram as limitações observadas na tentativa anterior;
- se uma abordagem híbrida apresenta melhor TCO que desenvolvimento sob medida.

### Dados e migração

- se o volume e qualidade das informações existentes permitem migração útil do histórico comercial;
- qualidade e duplicidade da base de aproximadamente 12 mil clientes;
- existência de identificador estável para reconciliação.

### Business case

- se as aproximadamente 234 horas/mês declaradas pelo cliente podem ser confirmadas;
- qual o custo carregado dessas horas;
- qual percentual do esforço atual é realmente eliminável;
- valor e frequência das oportunidades perdidas;
- custo total de CRM de mercado + integração;
- custo total de desenvolvimento + manutenção da solução sob medida;
- capacidade de atingir payback em 12 a 18 meses.

---

## 13. Pendências

- confirmar release exata do Protheus;
- inventariar APIs, REST, EAI, integrações e customizações já existentes no ambiente;
- obter documentação técnica ou acesso de homologação adequado para investigação posterior;
- avaliar qualidade e duplicidade da base de clientes;
- confirmar identificador estável do cliente no Protheus;
- conhecer volume médio de pedidos e frequência de atualização necessária;
- confirmar requisitos de LGPD, retenção e acesso às observações comerciais;
- entender como leads do site chegam hoje;
- verificar necessidade de anexos e propostas;
- avaliar importação de planilhas existentes;
- identificar informações comerciais consideradas confidenciais;
- verificar se existem usuários externos ou apenas colaboradores da empresa;
- obter custo médio carregado ou faixas salariais adequadas para converter horas em impacto financeiro;
- medir ou estimar de forma defensável oportunidades perdidas;
- levantar propostas comerciais reais das alternativas que avançarem no fit-gap.

---

## 14. Alternativas descartadas

No horizonte atual foram conscientemente descartadas como premissas:

- substituir o Protheus;
- transformar o CRM em sistema fiscal ou financeiro;
- tratar CRM como sistema principal de estoque ou faturamento;
- construir agenda corporativa completa como necessidade inicial;
- assumir integração profunda com WhatsApp sem validação;
- assumir operação offline completa antes de comprovar necessidade;
- fixar arbitrariamente cliente inativo como 60 dias sem considerar contexto comercial;
- assumir que software sob medida é necessariamente a melhor solução;
- afirmar ROI ou payback antes de validar custos e ganhos.

---

## 15. Ideias futuras não comprometidas

Podem ser investigadas posteriormente, sem compromisso de implementação:

- integração mais profunda com WhatsApp;
- criação de clientes no Protheus a partir do CRM;
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
- Que evidências atuais explicam falhas de adoção quando CRM e ERP criam dupla digitação?

### Build versus buy

- Quais soluções atuais atendem de forma material ao cenário?
- Quais possuem integração nativa, conector, APIs ou ecossistema suficiente para Protheus?
- Quais gaps permaneceriam em Pipedrive, HubSpot, Dynamics 365, TOTVS CRM ou alternativas relevantes?
- O desenvolvimento sob medida possui vantagem material suficiente para justificar seu TCO e risco?

### Protheus

- Quais capacidades oficiais atuais do Protheus permitem integrar cadastro de clientes, pedidos/faturamento, estoque e informações financeiras?
- Quais mecanismos preservam as regras do Protheus em vez de gravar diretamente em tabelas?
- O que depende da release, LIB, AppServer, licenciamento ou configuração do cliente?
- Existe solução TOTVS CRM integrada ao Protheus que precisa entrar obrigatoriamente no fit-gap?

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

### Business case

- Quanto das 234 horas/mês estimadas pode ser realmente recuperado?
- Qual custo por hora precisa ser considerado para calcular economia operacional?
- Qual ganho mensal mínimo seria necessário para recuperar R$ 80 mil a R$ 120 mil em 12 ou 18 meses?
- Como comparar TCO de 3 anos entre compra, integração/customização e desenvolvimento próprio?
- Que benefícios estratégicos devem ser registrados separadamente de economia financeira?

### Viabilidade operacional

- O escopo inicial pode ser recortado de forma que gere valor antes de integrações complexas?
- Quais dependências externas podem bloquear o primeiro release?

---

## 17. Discovery Readiness e handoff

```text
DISCOVERY_READINESS: SUFFICIENT
```

O Discovery é suficiente para Pesquisa e Viabilidade porque:

- a intenção e o problema central estão claros;
- o Protheus foi identificado como ERP corporativo e sua autoridade foi delimitada;
- foram identificadas as áreas de integração relevantes no nível de negócio;
- usuários e contextos principais foram identificados;
- necessidades de carteira, histórico, retorno, pedidos e gestão foram esclarecidas;
- a hipótese de construir foi separada da necessidade de resolver o problema;
- existem critérios econômicos declarados pelo cliente para avaliar o investimento;
- as estimativas operacionais foram registradas como hipóteses, não como economia comprovada;
- as alternativas de mercado permanecem abertas para comparação;
- hipóteses e pendências constituem agenda clara de investigação;
- não houve escolha prematura de stack, arquitetura, provider ou mecanismo de integração.

A Pesquisa e Viabilidade deve confrontar este documento com evidências atuais, comparar alternativas e verificar se existe fundamento técnico, operacional e econômico para continuar.

```text
NEXT_STAGE: 01 — Pesquisa e Viabilidade
```
---
document_id: CASE-01-DOC-01
title: Pesquisa e Viabilidade — CRM para gestão de clientes e pedidos
status: canonical
version: 1.0.0
case_id: CASE-01-CRM-CLIENTES-PEDIDOS
methodology_stage: pesquisa-e-viabilidade
consumes:
  - 00_Discovery.md
next_document: 02_Briefing_de_Produto_e_Escopo.md
research_date: 2026-08-30
research_verdict: GO_CONDICIONAL
custom_build_decision: JUSTIFIED_CONDITIONALLY
---

# Pesquisa e Viabilidade — CRM para gestão de clientes e pedidos

## 1. Leitura executiva

A investigação confirma que o problema comercial identificado no Discovery é material, tecnicamente solucionável e compatível com uma categoria madura de software: CRM e automação de força de vendas.

A pesquisa também demonstra que o projeto não deve partir da premissa de que software sob medida é automaticamente a melhor solução.

Existem alternativas maduras de mercado e, de forma especialmente relevante para este cliente, a própria TOTVS possui soluções de CRM/SFA com integrações documentadas com o Protheus.

Por isso, a decisão investigada foi tratada como:

```text
BUILD
×
BUY
×
HYBRID / CUSTOMIZE
```

O resultado final é:

```text
RESEARCH_VERDICT: GO_CONDICIONAL
RECOMMENDED_DIRECTION: CRM COMERCIAL SOB MEDIDA INTEGRADO AO TOTVS PROTHEUS
REFERENCE_ALTERNATIVE: TOTVS CRM / SFA
CUSTOM_BUILD_DECISION: JUSTIFIED_CONDITIONALLY
```

A construção própria é recomendada apenas porque o cenário simulado produziu condições específicas que, em conjunto, tornam o caminho plausível:

- necessidade de integração profunda com o Protheus;
- tentativa anterior de CRM de mercado abandonada por duplicidade operacional;
- desejo de experiência comercial mais enxuta do que suítes generalistas;
- regras específicas de carteira e visibilidade;
- orçamento inicial declarado entre aproximadamente R$ 80 mil e R$ 120 mil;
- expectativa de payback preferencialmente em 12 meses e tolerância aproximada de até 18 meses;
- custo operacional associado ao processo fragmentado estimado em aproximadamente R$ 18,1 mil por mês;
- possibilidade de construir um recorte estreito, sem reproduzir ERP, marketing automation, helpdesk, fiscal, financeiro ou estoque.

A recomendação deve ser reaberta caso custo, escopo, integração ou ganho esperado se afastem materialmente dessas premissas.

---

## 2. Base consumida

Esta etapa consumiu integralmente o `00_Discovery.md` versão `1.1.0` do caso.

Do Discovery foram herdados como fatos declarados pelo cliente do cenário:

- ERP atual: TOTVS Protheus 12, release exata ainda a confirmar;
- aproximadamente 18 vendedores, 2 gerentes e 1 diretor comercial;
- aproximadamente 12 mil clientes no ERP;
- duas filiais em uma operação comercial integrada;
- uso atual fragmentado entre Protheus, planilhas, WhatsApp e controles individuais;
- aproximadamente 234 horas/mês associadas ao processo fragmentado, como estimativa inicial;
- três desligamentos de vendedores no último ano com reconstrução manual de carteira;
- tentativa anterior com Pipedrive e avaliação anterior do HubSpot;
- investimento inicial que o diretor aceita avaliar: aproximadamente R$ 80 mil a R$ 120 mil;
- payback desejado: até 12 meses;
- payback ainda considerado aceitável, dependendo do ganho: aproximadamente até 18 meses;
- software próprio não é um objetivo em si;
- o Protheus deve continuar como autoridade dos processos ERP definidos no horizonte.

Esses fatos internos não foram tratados como prova de mercado. Foram utilizados como evidência direta do contexto do cliente.

---

## 3. Pergunta central da investigação

A pesquisa não se limitou a perguntar:

> É possível construir um CRM?

A pergunta útil para a consultoria é:

> **Existe justificativa operacional, econômica e técnica para a empresa investir em um CRM sob medida integrado ao Protheus em vez de comprar ou adaptar uma solução existente?**

Subperguntas:

1. o problema comercial é coerente com problemas que CRMs maduros resolvem?
2. existem alternativas prontas com aderência relevante?
3. o Protheus possui caminhos maduros de integração?
4. existe solução TOTVS com integração já documentada?
5. qual é o peso do custo recorrente das alternativas?
6. quais gaps específicos poderiam justificar customização ou build?
7. qual ganho econômico mínimo precisa ocorrer para o investimento se pagar no horizonte declarado?
8. quais riscos ou dependências devem permanecer como gates?

---

## 4. Evidências externas — categoria CRM

### EVIDÊNCIA

CRMs comerciais atuais oferecem capacidades maduras para:

- contatos e contas;
- leads e oportunidades;
- atividades;
- follow-ups;
- calendário;
- histórico de interações;
- pipelines;
- relatórios e dashboards;
- automação comercial.

Pipedrive, HubSpot e Microsoft Dynamics 365 apresentam publicamente essas famílias de recursos em seus produtos.

### INFERÊNCIA

A existência e maturidade da categoria reforçam que os problemas de perda de contexto, falta de acompanhamento e baixa visibilidade comercial não são particulares ou tecnicamente exóticos.

### LIMITE DA EVIDÊNCIA

A maturidade da categoria CRM não prova que este cliente deve construir software próprio.

Ela apenas comprova que:

```text
PROBLEMA DE CRM
= categoria conhecida e solucionável
```

Não comprova:

```text
CRM CUSTOM
= decisão automaticamente correta
```

---

## 5. Evidências externas — Protheus e integração

### 5.1. Integração do ecossistema TOTVS

A documentação oficial da TOTVS registra integração entre TOTVS CRM/SFA e Protheus.

Foram identificados fluxos documentados envolvendo:

```text
PROTHEUS → CRM / SFA
produto
tabela de preço
cliente
estoque
notas fiscais
histórico de pedidos de venda

CRM / SFA → PROTHEUS
cliente
pedido / ordem de venda
```

Também existe documentação oficial atual sobre:

- criação e atualização de clientes do TOTVS CRM para o Protheus;
- integração de ordens de venda CRM → Protheus via iPaaS;
- uso de API REST do Protheus em integrações CRM x Protheus;
- envio de campos customizáveis de clientes e pedidos em integração SFA/Protheus.

### EVIDÊNCIA

Isso demonstra que a convivência entre CRM e Protheus é um cenário suportado pelo próprio ecossistema TOTVS e que cliente, pedido, estoque e histórico de vendas não são fronteiras inéditas de integração.

### INFERÊNCIA

A existência de integração oficial reduz o risco técnico da alternativa TOTVS CRM/SFA e aumenta o ônus de prova para justificar um CRM sob medida.

### PENDÊNCIA

Ainda é necessário inventariar no ambiente real do cliente:

- release e patch do Protheus;
- LIB/AppServer relevantes;
- empresa/grupo/filial;
- compartilhamento de cadastros;
- customizações;
- APIs publicadas;
- integrações existentes;
- contratos de autenticação;
- campos customizados;
- regras particulares de pedido e liberação.

---

## 6. Viabilidade técnica de CRM custom integrado ao Protheus

### EVIDÊNCIA DO CENÁRIO

O cliente informou que já possui serviços REST ativos e integrações com outros sistemas.

### EVIDÊNCIA EXTERNA

A documentação TOTVS mostra o uso de APIs REST no ecossistema Protheus e integrações oficiais CRM x Protheus utilizando REST/iPaaS e mecanismos de integração suportados.

### CONCLUSÃO

```text
CUSTOM CRM ↔ PROTHEUS
TECHNICAL_FEASIBILITY: PLAUSIBLE / SUPPORTED BY MATURE INTEGRATION MECHANISMS
```

### RESTRIÇÃO

A Pesquisa não escolhe ainda:

- REST custom;
- FWRestModel;
- EAI;
- Mensagem Única;
- iPaaS;
- middleware próprio;
- acesso por consulta específica;
- replicação local;
- sincronização por evento ou lote.

Essa decisão pertence às etapas técnicas posteriores depois que os contratos de dados e comportamento forem definidos.

A pesquisa apenas estabelece a viabilidade e os pontos que precisam permanecer rastreáveis.

---

## 7. Build vs Buy vs Hybrid

A análise comparou cinco famílias de solução.

### A — TOTVS CRM / SFA + integração Protheus

**Forças observadas:**

- integração oficial documentada com Protheus;
- fluxos de cliente e pedido já previstos;
- cargas de produto, preço, estoque, nota fiscal e histórico de pedidos documentadas;
- menor risco de incompatibilidade estrutural entre ecossistemas;
- produto comercial já mantido por fornecedor.

**Gaps simulados identificados na avaliação do caso:**

- experiência mais ampla do que o fluxo enxuto desejado;
- necessidade de validar aderência à regra específica de carteira;
- necessidade de validar descoberta controlada de cliente alheio;
- regra de cliente que precisa de atenção pode exigir adaptação;
- customizações Protheus ainda precisam ser mapeadas;
- preço e TCO reais dependem de proposta comercial.

**Estado:**

```text
VIABLE_REFERENCE_ALTERNATIVE
```

### B — Pipedrive + integração Protheus

Pipedrive possui produto maduro de CRM e preço público atual para o plano Premium de US$ 59 por licença/mês com cobrança anual.

Para 21 licenças no cenário:

```text
21 × US$59 × 12
= US$14.868/ano
```

antes de impostos, câmbio, addons e custo de integração.

**Força:** experiência de CRM madura e conhecida pelo cliente.

**Risco:** repetir o padrão histórico de dupla operação caso a integração com Protheus não seja suficientemente profunda.

**Estado:**

```text
VIABLE_ONLY_IF_INTEGRATION_REMOVES_DUPLICATION
```

### C — HubSpot Sales Hub + integração Protheus

A página pública brasileira do HubSpot apresenta Sales Hub Professional a partir de US$ 90 por licença/mês no compromisso anual e onboarding profissional obrigatório de US$ 1.500.

Para 21 licenças:

```text
21 × US$90 × 12
= US$22.680/ano

+ US$1.500 onboarding
= US$24.180 no primeiro ano
```

antes de demais custos e integração.

**Força:** suíte madura e extensa.

**Risco:** TCO, excesso de capacidade para o recorte desejado e projeto separado de integração com Protheus.

### D — Microsoft Dynamics 365 Sales + integração Protheus

Preço público atual no Brasil para Dynamics 365 Sales Professional:

```text
R$372,20 por usuário/mês
pago anualmente
sem impostos
```

Para 21 usuários:

```text
21 × R$372,20 × 12
= R$93.794,40/ano
```

**Força:** produto comercial maduro.

**Risco:** custo recorrente já próximo da faixa de investimento inicial declarada pelo cliente, antes de integração e implantação.

### E — CRM comercial sob medida

Cenário preliminar simulado da consultoria:

```text
INVESTIMENTO INICIAL ESTIMADO
≈ R$105 mil

OPERAÇÃO / SUPORTE / INFRA ESTIMADOS
≈ R$3 mil/mês
```

TCO aproximado simulado em 36 meses:

```text
R$105 mil
+
36 × R$3 mil
≈ R$213 mil
```

Esse valor somente é plausível porque o produto não pretende reproduzir uma suíte completa de CRM.

O recorte seria concentrado em:

- carteira;
- cliente/prospect;
- interações;
- retornos;
- gestão comercial;
- sinais de atenção;
- consulta de histórico de compras/pedidos;
- integração Protheus necessária ao trabalho comercial.

Ficam deliberadamente fora desse cálculo inicial funcionalidades como marketing automation completo, helpdesk, financeiro, fiscal, estoque, faturamento e agenda corporativa completa.

---

## 8. Experiência anterior com CRM de mercado

### EVIDÊNCIA INTERNA

O cliente relatou tentativa anterior com Pipedrive.

A experiência foi abandonada porque o vendedor precisava manter informações no CRM e continuar entrando no Protheus para executar o pedido, gerando percepção de mais uma ferramenta a alimentar.

### INTERPRETAÇÃO CORRETA

A evidência não sustenta:

```text
PIPEDRIVE NÃO SERVE
```

Ela sustenta:

```text
CRM SEM INTEGRAÇÃO SUFICIENTE
+
PROTHEUS
→ DUPLICIDADE OPERACIONAL
→ BAIXA ADOÇÃO
```

### HIPÓTESE

A integração profunda o suficiente para remover a dupla operação é uma condição relevante de adoção.

---

## 9. Business case e linha de base econômica

### 9.1. Horas do processo fragmentado

O Discovery registrou aproximadamente:

```text
18 vendedores × 2 h/semana
≈ 36 h/semana

2 gerentes × 8 h/semana
≈ 16 h/semana

diretor
≈ 2 h/semana

TOTAL
≈ 54 h/semana
≈ 234 h/mês
```

### 9.2. Custo carregado simulado validado pelo cliente

Para o caso de uso, o cliente retornou:

```text
VENDEDOR
≈ R$65/h

GERENTE
≈ R$95/h

DIRETOR
≈ R$160/h
```

Aplicando 4,33 semanas/mês:

- vendedores: aproximadamente R$ 10.132/mês;
- gerentes: aproximadamente R$ 6.582/mês;
- diretor: aproximadamente R$ 1.386/mês.

Total aproximado:

```text
CUSTO OPERACIONAL ASSOCIADO AO PROBLEMA
≈ R$18,1 mil/mês
```

Esse valor não é uma economia prometida.

Ele é a linha de base do esforço potencialmente atacável.

---

## 10. Sensibilidade de benefício

Se a solução reduzir o esforço associado ao processo fragmentado:

| Redução | Benefício operacional bruto aproximado |
| --- | ---: |
| 30% | R$ 5,4 mil/mês |
| 40% | R$ 7,2 mil/mês |
| 50% | R$ 9,0 mil/mês |
| 60% | R$ 10,9 mil/mês |

Não foram incluídos no cálculo:

- receita recuperada;
- clientes reativados;
- melhoria de conversão;
- vendas que deixariam de ser perdidas;
- custo de perda de conhecimento em desligamentos;
- menor erro comercial.

Esses efeitos continuam como hipóteses até que o cliente consiga medi-los.

---

## 11. Payback preliminar do cenário custom

Cenário simulado:

```text
INVESTIMENTO INICIAL
R$105 mil

CUSTO OPERACIONAL FUTURO
R$3 mil/mês
```

### Recuperação de 50% do esforço atual

```text
benefício bruto
≈ R$9,05 mil/mês

menos operação
≈ R$3 mil/mês

benefício líquido
≈ R$6,05 mil/mês

payback
≈ 17,4 meses
```

### Recuperação de 60%

```text
benefício bruto
≈ R$10,86 mil/mês

benefício líquido
≈ R$7,86 mil/mês

payback
≈ 13,4 meses
```

### Recuperação de 40%

O payback ultrapassa aproximadamente 24 meses e não atende a tolerância declarada no cenário.

### CONCLUSÃO

A solução custom só permanece economicamente coerente, nesse cenário, se remover aproximadamente metade do esforço econômico associado ao processo fragmentado ou produzir valor equivalente de outra forma mensurável.

---

## 12. Hipótese econômica crítica

```text
HYP-ROI-001

A solução precisa reduzir aproximadamente 50% do esforço
administrativo/comercial associado à fragmentação atual,
ou gerar valor econômico equivalente mensurável,
para permanecer justificável dentro do horizonte aproximado
de 18 meses declarado pelo cliente.
```

Essa hipótese deve ser testada depois da implantação através de baseline e medição real.

---

## 13. Métricas preliminares de validação

Antes da implementação, medir com maior precisão:

- horas gastas por vendedor procurando/reconciliando informação;
- horas de gestão gastas consolidando e cobrando dados;
- quantidade de follow-ups vencidos;
- quantidade de oportunidades sem próxima ação;
- tempo médio para responder dúvida de pedido do cliente;
- número de controles paralelos ativos;
- percentual de clientes com histórico comercial utilizável;
- tempo de reconstrução de carteira em transferência/desligamento.

Depois da implantação, comparar a mesma linha de base.

A meta econômica preliminar deve buscar redução próxima ou superior a 50% do esforço que o sistema efetivamente se propõe a eliminar.

---

## 14. Privacidade e LGPD

### EVIDÊNCIA

O CRM tratará dados de pessoas naturais, como nome de contato, telefone, e-mail, cargo e histórico de interação.

A LGPD estabelece princípios como:

- finalidade;
- adequação;
- necessidade;
- qualidade dos dados;
- transparência;
- segurança;
- prevenção;
- responsabilização e prestação de contas.

### RECOMENDAÇÃO

As etapas posteriores devem definir, no nível adequado:

- quais dados realmente são necessários;
- quem pode visualizá-los;
- finalidade das observações e históricos;
- retenção;
- correção;
- exclusão quando aplicável;
- auditabilidade;
- limites para campos livres.

### LIMITE

A Pesquisa não escolhe ainda controles técnicos de segurança ou autorização.

---

## 15. Mobile e conectividade

### EVIDÊNCIA INTERNA

Vendedores trabalham também em campo e possuem episódios de conectividade ruim.

### RECOMENDAÇÃO

Acesso móvel deve fazer parte do produto.

### HIPÓTESE

Offline completo não está justificado.

A necessidade deve ser testada por cenário real antes de assumir a complexidade de sincronização offline como requisito estrutural.

---

## 16. WhatsApp

O WhatsApp é um canal relevante no processo atual, mas o Discovery mostrou que o problema inicial não depende de importação automática de conversas.

### RECOMENDAÇÃO

No primeiro horizonte, priorizar o problema:

```text
facilitar contato
+
registrar resultado comercial
```

sem transformar integração profunda com WhatsApp em bloqueador do core.

Integração oficial, automação, templates, consentimento e governança podem ser avaliados em horizonte posterior se houver ganho comprovado.

---

## 17. Riscos principais

| Risco | Nível | Efeito | Contramedida | Validação |
| --- | --- | --- | --- | --- |
| Customizar antes de entender Protheus | Alto | custo e retrabalho | inventário técnico antes da arquitetura | levantamento de ambiente |
| Construir CRM genérico demais | Alto | orçamento explode | preservar recorte comercial enxuto | Briefing + Scope Freeze |
| Repetir dupla operação | Alto | baixa adoção | integração como parte do valor central | protótipo/piloto de jornada |
| ROI baseado em horas não reais | Alto | business case falso | medir baseline por amostragem | estudo operacional curto |
| Estimar venda perdida sem evidência | Médio | ROI inflado | excluir do business case até medir | telemetria comercial futura |
| TCO custom subestimado | Alto | payback estoura | TCO 3 anos e gatilho de reavaliação | Tech Lead + Infra + orçamento |
| TOTVS CRM ser mais aderente do que esperado | Médio | build desnecessário | manter TOTVS CRM como benchmark | fit-gap final |
| Customizações Protheus incompatíveis | Alto | integração bloqueada | inventariar customizações | POC técnica posterior |
| Dados pessoais excessivos | Médio/Alto | risco LGPD | minimização, acesso e retenção | requisitos de produto e segurança |
| Offline assumido sem necessidade | Médio | complexidade desnecessária | validar contexto de campo | pesquisa/UX |

---

## 18. Gates recomendados

### GATE-R01 — Ambiente Protheus

Confirmar:

- release;
- patches relevantes;
- empresa/grupo/filial;
- customizações;
- serviços REST;
- integrações existentes;
- campos e regras críticas.

### GATE-R02 — Benchmark TOTVS CRM

Manter TOTVS CRM/SFA como alternativa de referência durante detalhamento de escopo e TCO.

Se o custom superar materialmente o custo/risco previsto, reabrir build-vs-buy.

### GATE-R03 — Baseline operacional

Validar a estimativa de 234 horas/mês através de amostragem real antes de usar o valor como KPI financeiro definitivo.

### GATE-R04 — TCO do custom

Antes da autorização para implementação, consolidar:

```text
build
integração
infraestrutura
suporte
manutenção
evolução
observabilidade
segurança
```

no horizonte mínimo de 3 anos.

### GATE-R05 — Payback

Se a previsão reconciliada ultrapassar aproximadamente 18 meses sem benefício estratégico explicitamente aceito pelo cliente, reabrir a recomendação.

### GATE-R06 — Integração sem bypass indevido

A solução deve respeitar os contratos e regras do Protheus aplicáveis, sem tratar acesso improvisado direto a tabelas como substituto automático de integração responsável.

---

## 19. Direção de produto recomendada

A Pesquisa recomenda que o Briefing avalie para canonização o seguinte recorte:

```text
CRM COMERCIAL ENXUTO
        +
CLIENTE / PROSPECT
        +
CARTEIRA
        +
HISTÓRICO COMERCIAL
        +
RETORNOS
        +
VISÃO DE GESTÃO
        +
SINAIS DE CLIENTE QUE PRECISA DE ATENÇÃO
        +
CONTEXTO DE COMPRAS / PEDIDOS
        +
INTEGRAÇÃO NECESSÁRIA COM PROTHEUS
```

Não recomendar como core inicial:

```text
marketing automation completo
helpdesk
financeiro
fiscal
estoque transacional
faturamento
agenda corporativa completa
WhatsApp profundo
offline completo
```

---

## 20. Decisão simulada do cliente após a pesquisa

A consultoria apresentou o resultado ao diretor, gerente comercial e TI.

O cenário registra como decisão humana simulada:

1. continuar o processo;
2. seguir com CRM comercial sob medida como direção preferencial;
3. manter TOTVS CRM/SFA como benchmark de referência;
4. não construir uma suíte genérica de CRM;
5. tratar integração com Protheus como parte central do valor;
6. manter payback e TCO como gates reais;
7. reabrir build-vs-buy se o custo próprio crescer materialmente;
8. não utilizar receita perdida não medida para inflar o ROI;
9. não substituir o Protheus;
10. exigir que a solução seja mais simples para o vendedor do que a combinação atual de ferramentas.

---

## 21. Veredito

```text
RESEARCH_VERDICT: GO_CONDICIONAL
```

### Por que não `GO` irrestrito

Ainda existem dependências materiais:

- inventário técnico real do Protheus;
- baseline operacional a medir;
- TCO custom a reconciliar;
- confirmação de que o escopo permanece enxuto;
- prova de que a integração elimina duplicidade operacional;
- validação posterior de adoção e UX.

### Por que não `PESQUISAR MAIS`

As lacunas restantes podem ser transformadas em gates e requisitos das etapas seguintes sem impedir a definição responsável do produto.

Existe evidência suficiente para produzir um Briefing condicionalmente aprovado.

### Por que não `NO-GO`

Não foi encontrado bloqueador estrutural de produto, tecnologia, operação ou economia que torne o recorte inviável neste momento.

---

## 22. Achado de validação da metodologia

Este caso revelou um ponto metodológico relevante:

```text
CASE-01-METHOD-FINDING-001

Quando existe mercado maduro para a categoria,
a Pesquisa e Viabilidade deve avaliar explicitamente:

BUILD
BUY
HYBRID / CUSTOMIZE
```

O objetivo não é obrigar todo projeto a possuir análise extensa de procurement.

A regra proposta para futura avaliação da metodologia é:

> quando uma necessidade pode ser atendida por software comercial maduro, a Pesquisa e Viabilidade deve provar por que continuar construindo é preferível, ou recomendar compra/adaptação quando for mais responsável.

Esse finding permanece como evidência do caso. Não altera automaticamente a metodologia antes da revisão transversal dos casos.

---

## 23. Fontes públicas consultadas

Pesquisa realizada em 30 de agosto de 2026.

### TOTVS

- Central de Atendimento TOTVS — integração de ordens de venda TOTVS CRM → Protheus: https://centraldeatendimento.totvs.com/hc/pt-br/articles/25513050155671-Cross-Segmentos-CRM-Gest%C3%A3o-de-Clientes-Integra%C3%A7%C3%A3o-Integra%C3%A7%C3%A3o-de-Ordens-de-venda-do-TOTVS-CRM-para-o-PROTHEUS
- Central de Atendimento TOTVS — integração de cadastro de clientes CRM → Protheus: https://centraldeatendimento.totvs.com/hc/pt-br/articles/35777139711639-Cross-Segmentos-CRM-Gest%C3%A3o-de-Clientes-Contas-Clientes-Integra%C3%A7%C3%A3o-de-Cadastro-de-Clientes-do-CRM-para-o-Protheus
- Central de Atendimento TOTVS — cargas Protheus → TOTVS CRM/SFA e exportação Cliente/Pedido → Protheus: https://centraldeatendimento.totvs.com/hc/pt-br/articles/23527682582295-Cross-Segmentos-TOTVS-CRM-Automa%C3%A7%C3%A3o-de-For%C3%A7a-de-Vendas-SFA-WEB-Integra%C3%A7%C3%A3o-Realizar-uma-carga-de-dados-do-Protheus-via-integra%C3%A7%C3%A3o-Connector
- Central de Atendimento TOTVS — integração iPaaS CRM x Protheus e API REST: https://centraldeatendimento.totvs.com/hc/pt-br/articles/35913439412375-Cross-Segmentos-CRM-Gest%C3%A3o-de-Clientes-Integra%C3%A7%C3%A3o-Integra%C3%A7%C3%A3o-iPaaS-CRM-x-Protheus
- Central de Atendimento TOTVS — campos customizáveis de clientes/pedidos na integração SFA/Protheus: https://centraldeatendimento.totvs.com/hc/pt-br/articles/29445061729431-Cross-Segmentos-TOTVS-CRM-Automa%C3%A7%C3%A3o-e-For%C3%A7a-de-Vendas-SFA-WEB-Integra%C3%A7%C3%A3o-Ajustar-Vari%C3%A1veis-de-Integra%C3%A7%C3%A3o-com-API-Nativa-Protheus

### CRM e preços

- Pipedrive Pricing: https://www.pipedrive.com/pt/pricing
- HubSpot Sales Hub Pricing: https://br.hubspot.com/pricing/sales
- Microsoft Dynamics 365 Sales Pricing: https://www.microsoft.com/pt-br/dynamics-365/products/sales/pricing

### Privacidade

- Governo Federal — Princípios da LGPD: https://www.gov.br/saude/pt-br/acesso-a-informacao/lgpd/principios

Preços e capacidades comerciais são temporalmente sensíveis e devem ser pesquisados novamente antes de qualquer contratação.

---

## 24. Handoff para Briefing de Produto e Escopo

A etapa seguinte deve consumir este documento junto com o `00_Discovery.md` e transformar a direção investigada em contrato canônico de produto.

O Briefing deverá decidir, sem antecipar arquitetura ou stack:

- definição do produto;
- público e stakeholders do horizonte;
- promessa;
- núcleo de valor;
- papel do Protheus;
- capacidades P0/P1/P2;
- limites e não objetivos;
- regras vinculantes de build-vs-buy e TCO;
- métricas de alto nível;
- gates herdados desta pesquisa;
- condições que obrigam reabrir a decisão de construir.

```text
RESEARCH_READINESS: SUFFICIENT
NEXT_STAGE: 02 — Briefing de Produto e Escopo
```

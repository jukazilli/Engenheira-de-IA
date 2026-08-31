---
document_id: CASE-01-DOC-03
title: Visão de Product Owner — CRM para gestão de clientes e pedidos
status: canonical
version: 1.0.0
case_id: CASE-01-CRM-CLIENTES-PEDIDOS
methodology_stage: visao-product-owner
consumes:
  - 00_Discovery.md
  - 01_Pesquisa_e_Viabilidade.md
  - 02_Briefing_de_Produto_e_Escopo.md
next_document: Principios_de_UX_UI.md
product_readiness: SUFFICIENT
---

# Visão de Product Owner — CRM para gestão de clientes e pedidos

## 1. Missão do horizonte atual

A missão deste horizonte não é simplesmente implementar todas as capacidades P0 descritas no Briefing.

A missão é:

> **Provar que vendedores conseguem conduzir o trabalho comercial diário com contexto e próxima ação em um único fluxo, reduzindo dependência de controles paralelos e mantendo o TOTVS Protheus como autoridade transacional.**

O sucesso do horizonte não será medido apenas por entrega de funcionalidades.

```text
SUCESSO
≠
CRM ENTREGUE

SUCESSO
=
COMPORTAMENTO MUDOU
+
FRAGMENTAÇÃO REDUZIU
+
ADOÇÃO ACONTECEU
+
BUSINESS CASE CONTINUA VÁLIDO
```

---

## 2. Visão operacional do produto

O produto deve permitir que o trabalho comercial cotidiano aconteça em uma camada própria, mais simples e aderente à rotina do vendedor, sem reconstruir dentro do CRM as responsabilidades do Protheus.

O núcleo operacional é:

```text
SABER QUEM PRECISA DE ATENÇÃO
↓
ABRIR CLIENTE OU PROSPECT
↓
ENTENDER CONTEXTO
↓
EXECUTAR AÇÃO COMERCIAL
↓
REGISTRAR RESULTADO
↓
DEFINIR PRÓXIMA AÇÃO
↓
RETORNAR NO MOMENTO CERTO
```

Quando necessário, o produto também deve trazer contexto do Protheus suficiente para responder perguntas comerciais sem obrigar o usuário a executar a rotina transacional do ERP.

---

## 3. Personas comportamentais

### U1 — Vendedor em operação

**Contexto:** possui carteira, trabalha relacionamento diariamente, alterna entre clientes e atua também fora do escritório.

**Progresso desejado:** compreender rapidamente:

- quem precisa de atenção;
- o que já aconteceu;
- qual é o estado comercial do cliente;
- qual é a próxima ação.

**Maior risco:** o CRM virar mais uma obrigação de preenchimento e coexistir com controles paralelos.

### Persona primária de decisão

`U1 — Vendedor em operação` é a persona primária para decisões sobre o core.

Quando houver trade-off entre uma experiência conveniente para gestão e uma experiência eficiente para o vendedor, o fluxo operacional do vendedor possui precedência no núcleo do produto, desde que os guardrails de gestão, segurança e auditoria sejam preservados.

---

### U2 — Gerente conduzindo equipe

**Contexto:** acompanha múltiplos vendedores e precisa identificar situações que exigem intervenção sem depender apenas de reunião, relato oral ou consolidação manual.

**Progresso desejado:** descobrir onde precisa intervir e por quê.

**Maior risco:** transformar o CRM em ferramenta de vigilância e burocracia que gera dado gerencial à custa do trabalho do vendedor.

---

### U3 — Diretor avaliando operação

**Contexto:** precisa de visão consolidada, continuidade de conhecimento e retorno econômico do investimento.

**Progresso desejado:** saber se a operação comercial está sendo trabalhada e se o investimento continua justificável.

**Maior risco:** otimizar relatórios executivos enquanto a equipe operacional mantém planilhas e controles paralelos.

---

### U4 — Responsável pelo Protheus / TI

**Contexto:** protege o ERP, suas regras, integrações, customizações e continuidade operacional.

**Progresso desejado:** permitir integração suficiente para o CRM sem criar segunda fonte transacional ou bypass das regras do ERP.

**Maior risco:** divergência silenciosa entre CRM e Protheus.

---

## 4. Jobs to be Done

### JTBD-01 — Vendedor

```text
QUANDO estou trabalhando um cliente ou prospect,
QUERO encontrar rapidamente o contexto, registrar o que fiz e saber qual é a próxima ação,
PARA conduzir relacionamento e venda com continuidade,
SEM reconstruir informação em múltiplos lugares ou depender da memória.
```

### JTBD-02 — Gerente

```text
QUANDO preciso acompanhar a equipe comercial,
QUERO saber quais clientes estão sendo trabalhados, quais precisam de atenção e o que aconteceu,
PARA orientar a equipe e tomar decisões com informação objetiva,
SEM depender apenas de relatos, planilhas e cobranças manuais.
```

### JTBD-03 — Diretor

```text
QUANDO preciso avaliar a operação comercial,
QUERO compreender continuidade, atividade e saúde do processo,
PARA decidir onde intervir e se o investimento continua justificável,
SEM exigir relatórios paralelos do vendedor.
```

### JTBD-04 — TI / Protheus

```text
QUANDO o CRM precisa consumir ou produzir informação relacionada ao ERP,
QUERO preservar os contratos e regras do Protheus,
PARA evitar divergência e risco operacional,
SEM transformar a integração em acesso informal a dados transacionais.
```

---

## 5. Outcome Tree

### OUT-001 — Continuidade comercial

O vendedor sabe, para sua carteira, qual contexto existe e qual ação precisa acontecer a seguir.

**Evidência esperada:**

- redução de follow-ups esquecidos;
- aumento de clientes com próxima ação conhecida quando aplicável;
- redução de controles paralelos.

---

### OUT-002 — Conhecimento pertence à empresa

O histórico relevante permanece utilizável independentemente da permanência de determinado vendedor.

**Evidência esperada:**

- transferência de carteira preserva histórico;
- novo responsável consegue compreender contexto sem reconstrução manual extensa.

---

### OUT-003 — Gestão baseada em evidência

Gerentes conseguem identificar situações que precisam de intervenção sem depender exclusivamente de relato individual.

**Evidência esperada:**

- clientes sem atenção identificáveis;
- atividade recente consultável;
- follow-ups vencidos identificáveis;
- transferência de responsabilidade rastreável.

---

### OUT-004 — Menor fragmentação operacional

O vendedor precisa alternar menos entre CRM, planilhas, controles pessoais e Protheus para executar a rotina comercial.

**Evidência esperada:**

- redução do esforço operacional medido;
- redução de planilhas paralelas;
- menor tempo para obter contexto necessário sobre cliente e pedido.

---

### OUT-005 — Integração sem perda de autoridade

O CRM fornece contexto do Protheus sem criar segunda verdade para dados transacionais.

**Evidência esperada:**

- cliente formal mantém vínculo inequívoco;
- informação indisponível ou conhecida como desatualizada não é apresentada como atual;
- não existe divergência silenciosa provocada pelo CRM.

---

### OUT-006 — Business case sustentável

O caminho custom continua economicamente racional.

**Evidência esperada:**

- TCO dentro da faixa reconciliada;
- redução de esforço compatível com a hipótese econômica;
- payback projetado continua aceitável para o cliente.

---

## 6. North Star preliminar

### Cobertura de Continuidade Comercial — CCC

A métrica norte preliminar representa valor sustentado no trabalho da carteira.

Conceito:

```text
CLIENTES ELEGÍVEIS DA CARTEIRA
COM:
CONTEXTO COMERCIAL SUFICIENTEMENTE ATUALIZADO
+
ESTADO DE PRÓXIMA AÇÃO CONHECIDO

÷

TOTAL DE CLIENTES ELEGÍVEIS DA CARTEIRA
```

`Próxima ação conhecida` pode significar:

```text
AÇÃO AGENDADA
ou
AÇÃO NÃO NECESSÁRIA NO MOMENTO
```

para não incentivar criação artificial de tarefas.

A janela temporal e a elegibilidade final ainda precisam ser validadas.

A CCC não pode ser interpretada isoladamente.

```text
CCC ALTA
+
VENDEDORES USANDO PLANILHA PARALELA
=
NÃO É SUCESSO
```

---

## 7. Guardrails de produto

### GR-001 — Sem duplicação operacional relevante

Nenhum ganho gerencial compensa obrigar o vendedor a preencher sistematicamente CRM e Protheus com a mesma informação.

### GR-002 — Autoridade do ERP

Melhor experiência não justifica divergência com dados canônicos do Protheus.

### GR-003 — Privacidade e carteira

Melhor descoberta comercial não justifica exposição irrestrita de históricos de outras carteiras.

### GR-004 — Registro proporcional

Não aumentar quantidade de campos ou etapas apenas para gerar mais informação gerencial.

### GR-005 — Business case

Mais funcionalidades não justificam perda do payback aceito.

### GR-006 — Dados financeiros

Conveniência comercial não significa exposição de todo o financeiro.

### GR-007 — Lista de atenção sem ruído excessivo

A lista de clientes que precisam de atenção deve reduzir esforço de decisão; volume excessivo ou relevância baixa invalida o benefício da capacidade.

---

## 8. Hipóteses de produto

### HYP-001 — Centralização reduz fragmentação

Se contexto comercial e informações necessárias do Protheus estiverem acessíveis no mesmo fluxo, vendedores reduzirão significativamente o tempo gasto reconstruindo informação.

**Meta econômica preliminar:** aproximar-se de 50% de redução do esforço atacável.

**Condição de retirada/revisão:** se piloto mostrar redução pequena e ainda exigir controles paralelos, fluxo e/ou decisão build devem ser reconsiderados.

---

### HYP-002 — Próxima ação reduz esquecimento

Se o vendedor registrar a próxima ação no momento da interação, haverá redução de follow-ups esquecidos.

**Condição de revisão:** se vendedores não registrarem a ação por excesso de esforço, UX ou modelo de produto precisa mudar.

---

### HYP-003 — Simplicidade aumenta adoção

Um CRM focado no fluxo essencial terá maior adesão que a experiência anterior de ferramenta paralela.

**Condição de retirada:** se usuários continuarem preferindo planilhas ou controles pessoais mesmo com integração adequada, a tese de aderência precisa ser revisada.

---

### HYP-004 — Lista de atenção ajuda carteira

Uma visão de clientes que precisam de atenção ajuda vendedor e gerente a agir antes que relacionamento seja perdido.

A hipótese não define ainda o algoritmo, janela ou regra final de priorização.

---

### HYP-005 — Visão gerencial pode existir sem burocratizar vendedor

A gestão consegue obter informação útil a partir de registros que também geram valor para o vendedor.

Se relatórios exigirem preenchimento que só beneficia gestão, o produto viola seus próprios princípios.

---

### HYP-006 — Mobile conectado é suficiente inicialmente

Uma experiência adequada em celular e tolerante a conexão instável atenderá a maior parte do uso em campo sem exigir offline completo no primeiro horizonte.

---

### HYP-007 — Lista de atenção precisa possuir sinal suficiente

A priorização só gera valor se reduzir esforço de decisão.

Uma lista excessivamente ruidosa invalida a hipótese mesmo que tecnicamente funcione.

---

## 9. Ordem de aprendizado

### EXP-001 — Validar baseline operacional real

**Objetivo:** transformar a estimativa de aproximadamente 234 horas/mês em baseline observável suficiente para comparação posterior.

**Decisão alimentada:** OUT-004, OUT-006, G-005.

### EXP-002 — Provar integração real com Protheus

**Objetivo:** provar os contratos relevantes do ambiente e das customizações sem assumir que a viabilidade genérica equivale à viabilidade concreta.

**Decisão alimentada:** OUT-005, G-001.

### EXP-003 — Provar fluxo diário do vendedor

**Pergunta:** o vendedor consegue descobrir o que precisa fazer, obter contexto e registrar resultado sem retornar a controles paralelos?

**Decisão alimentada:** HYP-001, HYP-002, HYP-003.

### EXP-004 — Piloto controlado

**Objetivo:** medir adoção, duplicidade, continuidade e redução de fragmentação com pequena coorte.

**Decisão alimentada:** G-002, G-003, G-005, G-006.

---

## 10. Jornadas de valor no nível de PO

### J-001 — Começar o dia comercial

**Entrada:** vendedor inicia a rotina.

**Sucesso:** consegue identificar quais clientes ou ações merecem atenção.

**Limite:** não obrigar o vendedor a navegar por relatório executivo para descobrir o trabalho operacional.

### J-002 — Trabalhar um cliente

**Entrada:** vendedor abre um cliente.

**Sucesso:** compreende contexto, histórico e próxima ação e consegue registrar o resultado da interação.

**Recuperação:** indisponibilidade de informação externa precisa ser compreensível; dado do Protheus não pode ser inventado ou apresentado como atual quando não confirmado.

### J-003 — Trabalhar um prospect

**Entrada:** nova oportunidade ainda não cadastrada formalmente no ERP.

**Sucesso:** vendedor consegue registrar e acompanhar sem exigir cadastro completo de cliente Protheus prematuramente.

### J-004 — Consultar contexto de pedido

**Entrada:** cliente pergunta sobre compra ou pedido.

**Sucesso:** vendedor encontra informação comercialmente necessária sem reproduzir operação ERP.

### J-005 — Gerenciar carteira

**Entrada:** gerente precisa saber onde intervir.

**Sucesso:** identifica clientes sem atenção, retornos vencidos e atividade relevante.

### J-006 — Transferir carteira

**Entrada:** mudança de responsabilidade comercial.

**Sucesso:** novo vendedor recebe responsabilidade sem perda do histórico corporativo.

---

## 11. Regras de negócio vinculantes

| ID | Tema | Regra |
| --- | --- | --- |
| BR-001 | Autoridade do Protheus | Dados e operações definidos como canônicos no Protheus permanecem sob autoridade do ERP. |
| BR-002 | Prospect independente | Prospect pode existir no CRM sem registro de cliente formal no Protheus. |
| BR-003 | Cliente formal vinculado | Cliente formal no CRM deve manter vínculo inequívoco com o cadastro canônico correspondente do Protheus. |
| BR-004 | Descoberta sem exposição total | Vendedor pode saber que um cliente de outra carteira existe e quem é o responsável sem receber automaticamente acesso ao histórico privado daquela carteira. |
| BR-005 | Carteira como responsabilidade | Cada cliente sob acompanhamento comercial possui responsabilidade de carteira conforme regra vigente. |
| BR-006 | Transferência preserva histórico | Transferir responsabilidade comercial não apaga nem reinicia o histórico corporativo do cliente. |
| BR-007 | Visão de gestão | Gerente e diretor podem acessar contexto ampliado de acordo com responsabilidade aprovada. |
| BR-008 | Registro possui autoria | Interações comerciais materiais devem preservar autoria e momento relevantes. |
| BR-009 | Próxima ação pode vencer | Uma próxima ação com data ultrapassada e ainda aberta deve ser reconhecida como pendente/vencida. |
| BR-010 | Atenção não possui prazo universal | O conceito de cliente que precisa de atenção não pode assumir uma quantidade universal de dias sem decisão validada. |
| BR-011 | Sem dupla manutenção | O CRM não deve exigir manutenção manual de cópia de dado cuja autoridade e manutenção pertencem exclusivamente ao Protheus, salvo exceção explicitamente aprovada. |
| BR-012 | Estado externo precisa ser distinguível | Quando informação dependente do Protheus estiver indisponível, incerta ou conhecida como desatualizada, o produto não deve apresentá-la como confirmadamente atual. |
| BR-013 | Informação financeira proporcional | Cada perfil recebe apenas a informação financeira necessária e autorizada ao seu trabalho. |
| BR-014 | Duplicidade de cliente precisa ser evitável | Antes de criar novo prospect/cliente, o fluxo precisa permitir descobrir registro empresarial já existente em contexto suficiente para reduzir duplicidade. |

IDs removidos não devem ser reutilizados para outras regras.

---

## 12. Épicos da baseline de produto

### E-001 — Prioridades comerciais

Dar ao vendedor clareza sobre o que precisa de atenção.

### E-002 — Cliente e prospect

Criar e localizar entidades comerciais com contexto apropriado.

### E-003 — Histórico e próxima ação

Preservar continuidade do relacionamento.

### E-004 — Carteira e responsabilidade

Gerenciar propriedade comercial sem quebrar histórico.

### E-005 — Contexto Protheus

Trazer informações ERP necessárias ao trabalho comercial.

### E-006 — Gestão comercial

Dar à liderança visão suficiente para intervir.

### E-007 — Governança e auditabilidade

Preservar autoria, acesso e continuidade.

---

## 13. Baseline de histórias de produto

### US-001 — Ver prioridades

Como vendedor, quero saber quais clientes e retornos precisam da minha atenção para organizar meu trabalho sem depender de uma lista paralela.

- Outcome: `OUT-001`
- Épico: `E-001`
- Prioridade: `MUST CORE`

**Aceite de produto:**

- vendedor consegue identificar trabalhos pendentes;
- retornos vencidos são distinguíveis;
- não precisa consultar planilha externa para descobrir a lista principal.

### US-002 — Localizar cliente

Como vendedor, quero localizar rapidamente um cliente para acessar seu contexto comercial.

- Outcome: `OUT-004`
- Épico: `E-002`
- Prioridade: `MUST CORE`

### US-003 — Descobrir cliente de outra carteira

Como vendedor, quero descobrir se uma empresa já existe e quem é responsável para evitar duplicidade sem acessar indevidamente o histórico alheio.

- Regras: `BR-004`, `BR-014`
- Épico: `E-002`
- Prioridade: `MUST CORE`

### US-004 — Criar prospect

Como vendedor, quero registrar uma oportunidade ainda não formalizada no Protheus para começar o relacionamento sem exigir cadastro ERP prematuro.

- Regra: `BR-002`
- Épico: `E-002`
- Prioridade: `MUST CORE`

### US-005 — Ver histórico

Como vendedor responsável, quero compreender as interações relevantes do cliente para continuar o relacionamento sem reconstruir contexto.

- Outcome: `OUT-001`, `OUT-002`
- Épico: `E-003`
- Prioridade: `MUST CORE`

### US-006 — Registrar interação

Como vendedor, quero registrar de forma proporcional o resultado de um contato para preservar o contexto necessário à próxima ação.

- Regras: `BR-008`
- Épico: `E-003`
- Prioridade: `MUST CORE`

**Critério essencial:** o registro não pode exigir informação sem finalidade clara apenas para alimentar relatório.

### US-007 — Definir próxima ação

Como vendedor, quero registrar o próximo passo e sua data para reencontrá-lo quando precisar agir.

- Regras: `BR-009`
- Épico: `E-003`
- Prioridade: `MUST CORE`

### US-008 — Ver contexto de compra

Como vendedor, quero visualizar histórico de compras necessário ao relacionamento para compreender melhor o cliente.

- Outcome: `OUT-004`, `OUT-005`
- Épico: `E-005`
- Prioridade: `MUST CORE`

### US-009 — Ver situação de pedido

Como vendedor, quero consultar a situação relevante de um pedido para responder ao cliente sem precisar executar a rotina transacional do Protheus.

- Outcome: `OUT-004`, `OUT-005`
- Épico: `E-005`
- Prioridade: `MUST CORE`

### US-010 — Ver disponibilidade comercial necessária

Como vendedor, quero consultar informação de estoque aprovada para decidir como conduzir a conversa comercial sem transformar o CRM em gestão de estoque.

- Outcome: `OUT-004`, `OUT-005`
- Épico: `E-005`
- Prioridade: `MUST GATE`

### US-011 — Consultar restrição financeira permitida

Como vendedor, quero saber somente a informação financeira necessária para conduzir adequadamente a venda sem receber acesso ao financeiro completo.

- Regra: `BR-013`
- Épico: `E-005`
- Prioridade: `MUST GATE`

### US-012 — Ver carteira

Como vendedor, quero trabalhar minha carteira de forma organizada.

- Outcome: `OUT-001`
- Épico: `E-004`
- Prioridade: `MUST CORE`

### US-013 — Transferir responsabilidade

Como gerente, quero transferir um cliente para outro vendedor preservando seu histórico.

- Regras: `BR-005`, `BR-006`, `BR-007`
- Épico: `E-004`
- Prioridade: `MUST CORE`

### US-014 — Identificar clientes sem atenção

Como vendedor ou gerente, quero identificar clientes potencialmente negligenciados para decidir se existe ação comercial necessária.

- Hipóteses: `HYP-004`, `HYP-007`
- Regras: `BR-010`
- Épico: `E-001`
- Prioridade: `MUST GATE`

### US-015 — Acompanhar equipe

Como gerente, quero identificar atividade, pendências e situações de carteira que exigem minha intervenção.

- Outcome: `OUT-003`
- Épico: `E-006`
- Prioridade: `MUST CORE`

### US-016 — Visão executiva mínima

Como diretor, quero compreender se a operação está sendo trabalhada sem obrigar o vendedor a produzir relatório manual adicional.

- Outcome: `OUT-003`, `OUT-006`
- Épico: `E-006`
- Prioridade: `MUST CORE`

### US-017 — Preservar histórico após desligamento

Como empresa, quero manter o histórico comercial utilizável quando um vendedor deixa a operação.

- Outcome: `OUT-002`
- Regra: `BR-006`
- Épico: `E-007`
- Prioridade: `MUST CORE`

### US-018 — Reconhecer indisponibilidade do ERP

Como usuário, quero saber quando determinada informação do Protheus não pôde ser confirmada para não tomar decisão baseada em dado apresentado incorretamente como atual.

- Outcome: `OUT-005`
- Regra: `BR-012`
- Épico: `E-005`
- Prioridade: `MUST CORE`

---

## 14. Ondas de produto

### Onda 0 — Provar pressupostos

**Público:** consultoria, TI e usuários-chave.

**Objetivos:**

- validar baseline operacional;
- provar integração Protheus;
- testar fluxo central com protótipo;
- revisar regras críticas.

Sem rollout amplo.

### Onda 1 — Piloto controlado

**Público inicial simulado:** 3 vendedores + 1 gerente.

**Escopo:**

- carteira;
- cliente/prospect;
- histórico;
- próxima ação;
- contexto Protheus essencial.

**Evidência de saída:**

- uso consistente;
- ausência de dupla manutenção relevante;
- falhas críticas controladas;
- sinal inicial de redução de fragmentação.

### Onda 2 — Expansão comercial

Expansão para mais vendedores e segundo gerente, somente depois dos gates do piloto.

### Onda 3 — Operação comercial completa

Expansão para os 18 vendedores e gestores somente se adoção, integração, segurança e business case permanecerem saudáveis.

Onda não é sprint.

---

## 15. Gates vinculantes de produto

### G-001 — Integração real

- Owner: TI + responsável técnico futuro.
- Condição: contratos necessários do Protheus foram provados no ambiente relevante.
- Evidência: prova funcional dos fluxos selecionados e inventário das customizações relacionadas.
- Falha: `HOLD` ou `PIVOT`.

### G-002 — Fluxo não aumenta duplicidade

- Owner: Product Owner + gerente comercial.
- Condição: piloto não exige manutenção relevante dos mesmos dados em dois lugares.
- Evidência: observação do piloto e análise dos fluxos paralelos.
- Falha: `PIVOT`.

### G-003 — Adoção operacional

- Owner: Product Owner.
- Condição: vendedores piloto usam o CRM como ferramenta principal para o core definido.
- Evidência: uso observado + pesquisa qualitativa.
- Falha: `HOLD` ou `PIVOT`.

### G-004 — Segurança de carteira

- Owner: Product Owner + owner de segurança/negócio posteriormente definido.
- Condição: usuários não obtêm acesso indevido ao histórico de outras carteiras.
- Evidência: cenários de permissão e validação específica.
- Falha: `HOLD`.

### G-005 — Business case

- Owner: diretor comercial.
- Condição: TCO e benefício projetado continuam compatíveis com limite aprovado.
- Evidência: atualização do business case.
- Falha: reabrir `BUILD × BUY × HYBRID`.

### G-006 — Abandono de controles paralelos

- Owner: gerente comercial + Product Owner.
- Condição: coorte piloto consegue executar o core sem depender sistematicamente de planilha paralela de carteira/follow-up.
- Evidência: observação do fluxo real e controles efetivamente utilizados.
- Falha: `PIVOT` ou `HOLD`.

---

## 16. Instrumentação semântica de produto

A Visão de PO não escolhe ferramenta de analytics.

Conceitos a medir posteriormente incluem:

- `commercial_priority_viewed` — usuário encontrou sua visão de prioridades;
- `customer_context_opened` — contexto de cliente foi consultado;
- `interaction_recorded` — interação comercial foi registrada;
- `next_action_defined` — próxima ação foi definida;
- `next_action_completed` — próxima ação foi concluída;
- `next_action_overdue` — ação venceu aberta;
- `protheus_context_requested` — informação externa foi solicitada;
- `protheus_context_unavailable` — contexto do ERP não pôde ser confirmado;
- `portfolio_transfer_completed` — transferência de responsabilidade concluída;
- `parallel_control_detected` — evidência qualitativa/operacional de controle paralelo permanece.

Nomes finais de eventos poderão mudar, mas o significado das métricas deve ser preservado.

---

## 17. Definition of Ready de produto

Uma história pode seguir para detalhamento posterior quando:

- persona ou contexto está claro;
- outcome está vinculado;
- regras aplicáveis estão identificadas;
- critérios funcionais existem;
- principais estados críticos conhecidos estão registrados;
- dependências Protheus estão explícitas quando aplicáveis;
- gate está identificado quando necessário;
- não exige decisão de arquitetura para ser compreendida.

```text
READY DE PRODUTO
≠
READY FOR CODEX
```

---

## 18. Definition of Done de produto

Quando implementada posteriormente, uma capacidade só pode ser aceita pelo PO quando:

- comportamento funcional estiver cumprido;
- regra de negócio estiver preservada;
- guardrails não forem violados;
- instrumentação necessária permitir avaliação;
- estados críticos relevantes tiverem sido tratados;
- dependência externa não estiver mascarando erro;
- aceite acontecer no ambiente apropriado;
- deploy não for confundido com aceite;
- aceite não for confundido com sucesso de mercado.

---

## 19. Política de mudança

### Correção

Remove ambiguidade sem alterar outcome ou escopo.

→ atualizar Visão de PO e rastreabilidade.

### Mudança menor

Altera regra ou fluxo dentro do escopo.

→ revisar impacto em métricas, UX e risco.

### Mudança material

Adiciona módulo, público, responsabilidade ERP, dado relevante ou altera business case.

→ retornar ao Briefing.

### Exceção urgente

Incidente, obrigação legal ou segurança podem exigir contenção imediata; documentação deve ser reconciliada depois.

---

## 20. Decisões explicitamente não tomadas nesta etapa

A Visão de Product Owner não decidiu:

- estrutura visual;
- número de abas;
- menu ou navegação final;
- dashboard final;
- algoritmo de cliente que precisa de atenção;
- quantidade final de campos do registro de interação;
- tecnologia mobile;
- suporte offline completo;
- arquitetura;
- banco;
- linguagem;
- framework;
- provider;
- mecanismo concreto de integração Protheus;
- estratégia concreta de autenticação;
- topologia de infraestrutura;
- ferramenta de analytics.

Essas decisões pertencem às camadas posteriores.

---

## 21. Decisões consolidadas após revisão simulada

Durante a revisão do caso com stakeholders simulados, foram reforçadas as seguintes decisões:

1. a lista de prioridades não pode se transformar em fila excessivamente ruidosa;
2. registrar uma interação não pode exigir quantidade de campos desproporcional ao valor gerado;
3. estado desatualizado ou indisponível do Protheus precisa ser reconhecível;
4. piloto pequeno deve preceder liberação para toda a equipe;
5. dependência sistemática de planilha paralela no piloto impede expansão.

Esses refinamentos não alteram o Briefing; operacionalizam decisões já compatíveis com ele.

---

## 22. Estado da etapa e handoff

```text
PO_METHOD_VALIDATION: PASS
SCOPE_EXPANSION: NO
PREMATURE_UX_DECISION: NO
PREMATURE_TECH_DECISION: NO
STABLE_PRODUCT_IDS: CREATED
PRODUCT_BACKLOG_BASELINE: CREATED
PRODUCT_READINESS: SUFFICIENT
```

A Visão de Product Owner está suficientemente definida para que os `Principios_de_UX_UI.md` sejam elaborados sem inventar prioridade, outcome ou regra de negócio.

O próximo documento canônico é:

```text
Principios_de_UX_UI.md
```

# Engenharia de IA — Processo Canônico de Desenvolvimento

> **Status:** canônico  
> **Formato:** Markdown (`.md`)  
> **Objetivo:** definir um processo reproduzível para transformar Discovery assistido por IA em software rastreável, testável, validado e com identidade própria.

## 1. Propósito

Este repositório documenta o processo de desenvolvimento de aplicações assistido por ChatGPT e Codex adotado a partir da experiência do projeto DayGym.

O objetivo não é pedir para uma IA "criar um sistema" a partir de um prompt único. O processo separa descoberta, definição de produto, experiência, engenharia, execução, validação e evolução documental.

A regra central é:

```text
Discovery humano assistido por IA
        ↓
Documentação canônica
        ↓
Governança documental
        ↓
Backlog rastreável
        ↓
Implementação por fatias
        ↓
Testes e gates
        ↓
Staging e evidências
        ↓
Promoção
        ↓
Rastreabilidade atualizada
```

A documentação não existe apenas para explicar o projeto. Ela deve orientar decisões, limitar interpretações, permitir rastreabilidade e, quando possível, gerar contratos que possam ser validados automaticamente.

---

## 2. Princípios gerais do processo

### 2.1. A conversa de Discovery não é fonte canônica

O Discovery normalmente acontece em uma longa conversa com o ChatGPT. Durante essa etapa podem existir hipóteses, ideias descartadas, comparações, pesquisas, mudanças de direção e decisões ainda incompletas.

Por isso:

```text
CONVERSA ≠ FONTE DA VERDADE
```

A conversa é matéria-prima para raciocínio.

A documentação canônica nasce quando o responsável pelo produto encerra uma etapa do Discovery e solicita explicitamente a geração do artefato correspondente, por exemplo:

> "Certo, agora crie o briefing."

Esse momento funciona como um **Discovery Freeze** daquela camada de decisão.

Antes de canonizar qualquer conteúdo, a IA deve distinguir:

- **decidido**;
- **hipótese**;
- **pendente**;
- **descartado**.

Uma hipótese discutida no Discovery não pode ser promovida automaticamente a requisito.

### 2.2. Markdown é o formato canônico

Todos os documentos de produto, UX, UI, engenharia, backlog e rastreabilidade devem ser mantidos prioritariamente em `.md`.

```text
.md    → formato canônico
.docx  → não usar como fonte canônica
.xlsx  → não usar como fonte canônica de requisitos
.pdf   → não usar como fonte canônica de requisitos
```

Arquivos auxiliares podem existir quando houver necessidade real, mas a fonte da verdade deve permanecer legível por humanos, agentes de IA, Git, revisão de código e automações.

### 2.3. Cada documento possui uma responsabilidade semântica

Um documento não deve tentar substituir todos os outros. A separação reduz ambiguidade e permite que a IA saiba onde procurar cada tipo de decisão.

### 2.4. A IA não deve completar lacunas silenciosamente

Quando a documentação não define uma decisão relevante, o agente deve:

1. identificar a lacuna;
2. verificar se ela pode ser resolvida pelos princípios existentes;
3. acionar a governança documental quando aplicável;
4. pedir decisão humana quando a lacuna alterar produto, negócio, risco ou identidade.

A ausência de especificação não autoriza invenção silenciosa.

---

# 3. Arquitetura documental inicial

A baseline de um novo produto é composta pelos seguintes artefatos:

```text
01_Pesquisa_e_Viabilidade.md
02_Briefing_de_Produto_e_Escopo.md
03_Visao_de_Product_Owner.md
Principios_de_UX_UI.md
04_Direcao_de_UI_e_Design_System.md
05_Especificacao_de_UX.md
06_Tecnicas_de_Desenvolvimento.md
07_Arquitetura_e_Engenharia.md
08_Backlog_Canonico_Rastreabilidade_e_Plano_de_Entrega.md
09_Matriz_Operacional_de_Rastreabilidade.md
```

`Principios_de_UX_UI.md` não é numerado porque não representa apenas uma etapa linear. Ele é uma camada normativa transversal, específica para a aplicação, consultada continuamente por UI, UX, Design System e implementação.

---

# 4. Documento 01 — Pesquisa e Viabilidade

## Pergunta central

> **Faz sentido construir este produto?**

## Objetivo

Transformar o Discovery inicial em uma análise estruturada do problema e da viabilidade da solução.

## Deve conter

- problema observado;
- público afetado;
- necessidades e Jobs To Be Done quando aplicável;
- alternativas e soluções existentes;
- concorrentes e referências;
- evidências de mercado ou comportamento;
- diferenciação possível;
- limitações técnicas conhecidas;
- riscos;
- premissas;
- hipóteses ainda não validadas;
- critérios de viabilidade.

## Regra de qualidade

O documento deve separar explicitamente:

```text
EVIDÊNCIA ≠ HIPÓTESE ≠ DECISÃO
```

## Saída

Uma conclusão clara sobre o que foi aprendido e quais pontos podem seguir para definição de produto.

---

# 5. Documento 02 — Briefing de Produto e Escopo

## Pergunta central

> **O que estamos construindo e o que não estamos construindo?**

## Objetivo

Preservar a intenção do produto e limitar interpretações futuras.

## Deve conter

- visão resumida do produto;
- problema;
- proposta de valor;
- público;
- objetivos;
- escopo;
- não escopo;
- funcionalidades macro;
- plataformas previstas;
- restrições;
- premissas;
- modelo operacional;
- definição de MVP, Beta ou corte inicial;
- critérios macro de sucesso.

## Regra de qualidade

O documento descreve requisitos de produto, não implementação.

Exemplo correto:

```text
O usuário deve conseguir registrar cada série individualmente.
```

Exemplo incorreto nesta camada:

```text
Criar o componente React WorkoutSetCard.
```

---

# 6. Documento 03 — Visão de Product Owner

## Pergunta central

> **Como o produto deve tomar decisões quando existirem várias soluções possíveis?**

## Objetivo

Transformar o briefing em uma política de decisão de produto.

## Deve conter

- visão do PO;
- princípios do produto;
- prioridades;
- objetivos da versão atual;
- jornadas prioritárias;
- regras de negócio centrais;
- trade-offs preferidos;
- critérios de valor;
- ordem macro de evolução;
- decisões que não devem ser revertidas sem revisão explícita.

## Exemplo

```text
O produto prioriza velocidade durante a execução do treino
sobre densidade de informação na tela.
```

O Briefing define **o que o produto é**. A Visão do PO define **como decidir sobre ele**.

---

# 7. Princípios de UX/UI

## Pergunta central

> **Quando houver mais de uma solução de interface possível, qual decisão combina melhor com a experiência que esta aplicação quer oferecer?**

## Natureza do documento

`Principios_de_UX_UI.md` é uma **constituição de experiência específica da aplicação**.

Ele não especifica telas individualmente. Ele orienta as decisões que serão depois materializadas pela Direção de UI, pelo Design System e pela Especificação de UX.

Os princípios devem ser definidos de acordo com o contexto, a identidade e o comportamento desejado para aquela aplicação.

## Eixos obrigatórios

### 7.1. Baixa carga cognitiva

A experiência deve minimizar:

- memorização;
- procura visual;
- interpretação desnecessária;
- comparação simultânea;
- excesso de escolhas;
- mudança de contexto;
- necessidade de reaprender padrões entre telas.

Exemplo de princípio:

```text
A ação principal necessária para concluir uma tarefa deve permanecer
perceptível durante a execução daquela tarefa.
```

Aplicação possível:

```text
Formulário longo
+ ação principal = salvar
+ risco de o botão sair da área visível
→ preferência por ação persistente no rodapé.
```

O princípio orienta a decisão. Ele não obriga que todos os botões de todas as telas tenham a mesma posição sem considerar o contexto.

### 7.2. Baixa densidade

Baixa densidade não significa apenas aumentar espaços vazios. Significa reduzir a quantidade de elementos que disputam atenção simultaneamente.

O documento deve orientar:

- quantidade de informações primárias;
- hierarquia visual;
- progressão de complexidade;
- exposição de ações raras;
- uso de detalhes sob demanda;
- redução de controles redundantes.

### 7.3. Linguagem do usuário

A aplicação deve falar sobre a tarefa que o usuário quer realizar, e não sobre a estrutura interna do software.

Preferir:

```text
Salvar treino
Adicionar exercício
Concluir série
```

Evitar:

```text
Persistir alterações
Adicionar entidade
Finalizar registro
```

Esse princípio vale para títulos, CTAs, erros, confirmações, empty states, onboarding, ajuda contextual e feedbacks.

### 7.4. Comunicação e personalidade da marca

A personalidade da marca deve influenciar a experiência completa, não somente textos promocionais.

Devem ser documentados atributos como, por exemplo:

- séria;
- alegre;
- energética;
- próxima;
- técnica;
- calma;
- premium;
- objetiva.

Esses atributos podem orientar:

- tom de voz;
- tipografia;
- hierarquia;
- densidade;
- movimentos e microinterações;
- ícones;
- feedbacks;
- ritmo da navegação;
- grau de celebração;
- cores;
- ilustrações;
- intensidade visual.

A intenção é remover o aspecto de interface genérica e dar identidade reconhecível ao produto.

## Os princípios devem ser avaliáveis

Evitar princípios vagos como:

```text
A interface deve ser simples.
```

Preferir estruturas como:

```markdown
## P-UX-004 — Uma tarefa mental dominante

### Objetivo
Permitir que o usuário identifique rapidamente o que deve fazer.

### Regra
Cada estado principal de uma tela deve possuir uma tarefa mental dominante.

### Critérios
- deve existir apenas uma CTA de maior hierarquia;
- ações secundárias não devem competir visualmente com a principal;
- informação sem utilidade imediata deve perder hierarquia;
- ações destrutivas não devem dominar visualmente a tela, salvo quando a própria tarefa for confirmar uma exclusão.

### Perguntas de avaliação
1. O objetivo da tela é reconhecível rapidamente?
2. Mais de uma ação compete pela atenção?
3. Existe informação visível sem utilidade para a tarefa atual?
4. O usuário precisa lembrar algo de outra tela para continuar?
```

## Papel no processo

```text
IDENTIDADE DA MARCA
        +
COMPORTAMENTO HUMANO
        +
PRINCÍPIOS DE EXPERIÊNCIA
        ↓
DECISÕES DE UI/UX
```

---

# 8. Documento 04 — Direção de UI e Design System

## Pergunta central

> **O que deve existir na interface para suportar cada contexto e tarefa mental, e qual deve ser sua hierarquia?**

## Objetivo

Especificar contextos, telas, tarefas mentais, elementos necessários e representação visual.

Este documento é específico. Diferentemente dos Princípios, ele toma decisões concretas para superfícies e contextos.

## Deve conter

- contextos de uso;
- telas e superfícies;
- tarefa mental principal de cada tela;
- informações obrigatórias;
- ações principais;
- ações secundárias;
- ações raras ou destrutivas;
- hierarquia visual;
- estrutura de navegação local;
- componentes previstos;
- tokens e fundamentos visuais;
- tipografia;
- espaçamento;
- cores semânticas;
- densidade;
- estados visuais;
- responsividade;
- regras do Design System.

## Exemplo

```markdown
## Tela: Editar treino

### Contexto
Usuário está montando ou ajustando um treino.

### Tarefa mental principal
Montar o treino.

### Elementos obrigatórios
- nome;
- exercícios;
- adicionar exercício;
- salvar;
- excluir treino.

### Hierarquia
- Salvar: ação principal;
- Adicionar exercício: ação contextual;
- Excluir: ação destrutiva de baixa frequência.

### Decisão de interface
Salvar permanece persistente no rodapé durante formulários longos.
Excluir fica em ação secundária e não compete visualmente com Salvar.
```

## Relação com o Design System

O Design System materializa decisões. Ele não deve decidir sozinho o contexto de uso.

```text
Princípio
   +
Contexto / tarefa mental
   ↓
Decisão de UI
   ↓
Componente do Design System
```

---

# 9. Documento 05 — Especificação de UX

## Pergunta central

> **Como o usuário percorre, executa e conclui a experiência?**

## Objetivo

Especificar jornadas, user stories, estados, transições, erros e exceções.

## Deve conter

- jornadas;
- user stories;
- fluxos;
- estados;
- transições;
- loading;
- empty state;
- erros;
- sucesso;
- confirmações;
- validações;
- interrupções;
- retomadas;
- acessibilidade comportamental;
- gestos quando aplicáveis;
- comportamento por plataforma;
- microcopy crítica.

## Exemplo de jornada

```text
Selecionar exercício
        ↓
Iniciar
        ↓
Exibir série atual
        ↓
Ajustar carga/repetições se necessário
        ↓
Concluir série
        ↓
Descanso
        ↓
Próxima série
        ↓
Última série?
  não ─────────┘
  sim
        ↓
Próximo exercício
```

## Exemplo de User Story

```text
Como praticante,
quero registrar cada série individualmente,
para acompanhar o que realizei sem interromper meu treino.
```

## Distinção entre os três documentos de experiência

| Documento | Função | Pergunta |
| --- | --- | --- |
| `Principios_de_UX_UI.md` | orientar decisões | Qual solução combina com a experiência desejada? |
| `04_Direcao_de_UI_e_Design_System.md` | especificar contexto, telas e hierarquia | O que deve existir e como deve ser representado? |
| `05_Especificacao_de_UX.md` | especificar jornadas e comportamento | Como o usuário percorre e conclui a experiência? |

Resumo:

```text
Princípios → orientam
Documento 04 → especifica a interface
Documento 05 → especifica a jornada
```

---

# 10. Documento 06 — Técnicas de Desenvolvimento

## Pergunta central

> **Como humanos e agentes de IA podem programar neste projeto?**

## Objetivo

Definir regras operacionais de implementação.

## Deve conter, quando aplicável

- linguagem e runtime;
- versões fixadas;
- package manager;
- TypeScript strict ou equivalente;
- organização de módulos;
- convenções de naming;
- limites de dependência;
- tratamento de erros;
- logging e observabilidade;
- política de dependências;
- migrations;
- política de segredos;
- segurança de cliente e servidor;
- padrão de testes;
- mocks;
- lint;
- formatting;
- typecheck;
- build;
- política de branches;
- commits;
- pull requests;
- Definition of Done;
- instruções específicas para agentes.

## Regra para agentes

Quando uma tecnologia instalada possuir documentação local ou versão diferente do conhecimento de treinamento do modelo, a IA deve consultar a documentação correspondente à versão efetivamente instalada antes de escrever código.

---

# 11. Documento 07 — Arquitetura e Engenharia

## Pergunta central

> **Qual estrutura técnica consegue entregar o produto e a experiência definidos anteriormente?**

## Objetivo

Converter requisitos de produto, UI e UX em uma arquitetura implementável.

## Deve conter, conforme o projeto

- contexto do sistema;
- aplicações e superfícies;
- módulos;
- fronteiras;
- domínio;
- contratos;
- APIs;
- banco de dados;
- autenticação e autorização;
- RLS ou mecanismos equivalentes;
- filas;
- eventos;
- cache;
- offline;
- sincronização;
- infraestrutura;
- ambientes;
- deploy;
- segurança;
- observabilidade;
- backup e restore;
- integrações;
- requisitos não funcionais;
- decisões arquiteturais importantes.

## Ordem obrigatória de raciocínio

```text
Produto
   ↓
Experiência
   ↓
Requisitos técnicos
   ↓
Arquitetura
```

Evitar arquiteturas que partem de uma tecnologia escolhida e tentam adaptar o produto a ela sem justificativa.

---

# 12. Documento 08 — Backlog Canônico, Rastreabilidade e Plano de Entrega

## Pergunta central

> **Exatamente o que deve ser construído, em qual ordem e como provar que está pronto?**

## Objetivo

Transformar toda a baseline documental em unidades executáveis pelo Codex.

## Identificadores permanentes

Cada item deve receber um ID estável, por exemplo:

```text
FND-001
AUTH-003
TRN-014
UX-008
SEC-002
```

## Cada item deve conter

- ID;
- título;
- tipo;
- origem documental;
- objetivo;
- descrição;
- critérios de aceite;
- dependências;
- riscos;
- testes necessários;
- evidência necessária;
- status.

## Exemplo

```text
TRN-014

Origem:
D02 §8.3
D03 §5.2
D05 §12.4

Objetivo:
Permitir conclusão individual de cada série.

Critérios:
AC-01 ...
AC-02 ...
AC-03 ...

Testes:
TEST-TRN-014-01
TEST-TRN-014-02
```

Não criar itens vagos como "implementar tela de treino" quando o comportamento esperado puder ser dividido em requisitos verificáveis.

---

# 13. Documento 09 — Matriz Operacional de Rastreabilidade

## Pergunta central

> **Onde cada requisito foi implementado, testado e comprovado?**

## Objetivo

Conectar requisito, código, testes, evidência e estado de entrega.

## Exemplo

| ID | Origem | Requisito | Implementação | Testes | Evidência | Status |
| --- | --- | --- | --- | --- | --- | --- |
| AUTH-001 | D02 §7 | Criar conta | `auth/...` | `AUTH-T01` | CI + staging | Done |
| TRN-014 | D05 §12 | Concluir série | — | `TRN-T04` | — | Planned |
| SEC-003 | D07 §9 | Sessão segura | `security/...` | `SEC-T03` | CI | Done |

A matriz deve ser legível por IA e mantida em Markdown sempre que possível.

---

# 14. Governança documental — MAE e MFEE

O processo utiliza skills de governança documental do Codex chamadas **MAE** e **MFEE**.

## Regra de integração

Os detalhes internos desses frameworks não fazem parte desta metodologia e não devem ser inventados ou duplicados aqui.

Eles são tratados como **caixas-pretas de governança** capazes de analisar o estado documental e decidir, conforme suas próprias regras, quando um documento precisa:

- ser mantido;
- ser atualizado;
- ser canonizado;
- ser reconciliado;
- gerar um novo documento derivado.

## Contrato esperado

```text
Documentação canônica
        ↓
MAE / MFEE
        ↓
analisa impacto
        ↓
┌──────────┬──────────┬──────────┐
│ mantém   │ atualiza │ cria     │
│ documento│ documento│ derivado │
└──────────┴──────────┴──────────┘
        ↓
canonização
        ↓
Codex continua a execução
```

O objetivo é impedir que implementação e documentação evoluam separadamente.

---

# 15. Documentação de segunda geração

Os documentos 01 a 09 formam a baseline inicial, mas não representam toda a documentação que um projeto terá durante sua vida.

Durante a implementação podem surgir artefatos derivados, por exemplo:

```text
docs/api/
docs/data/
docs/security/
docs/governance/
docs/runbooks/
docs/adr/
```

Exemplos de documentos derivados:

- contratos de API;
- dicionário de dados;
- matriz RLS;
- threat models;
- contratos de ambiente;
- runbooks;
- políticas de dependência;
- decisões arquiteturais;
- filas e eventos;
- inventários operacionais;
- observabilidade;
- restore e contingência.

Esses documentos devem nascer quando o conhecimento se torna necessário, e não apenas para preencher uma lista antecipadamente.

---

# 16. Documentação deve se transformar em contrato executável quando possível

O padrão desejado é:

```text
DECISÃO
   ↓
DOCUMENTO
   ↓
CONTRATO
   ↓
TESTE
   ↓
GATE
   ↓
EVIDÊNCIA
```

Exemplo:

```text
Arquitetura:
"o cliente não acessa schemas privados"
        ↓
regra de boundary / segurança
        ↓
check automatizado
        ↓
CI falha se a regra for violada
```

Outro exemplo:

```text
Contrato de dados:
"toda superfície exposta deve possuir política de autorização"
        ↓
migration
        ↓
teste negativo
        ↓
gate de contrato de dados
```

A documentação deixa de ser somente descritiva e passa a participar da qualidade do software.

---

# 17. Três níveis de verdade

O processo trabalha com três níveis complementares:

| Camada | Fontes principais | Pergunta |
| --- | --- | --- |
| Verdade de Produto | Docs 01–05 | O que o produto deve fazer e por quê? |
| Verdade de Engenharia | Docs 06–07 + derivados | Como isso deve funcionar tecnicamente? |
| Verdade de Execução | Docs 08–09 + código + testes + CI | O que foi realmente entregue e comprovado? |

Exemplo:

```text
Produto: requisito esperado
Código: ainda inexistente
→ trabalho pendente
```

Diferente de:

```text
Arquitetura: RLS obrigatória
Runtime: tabela exposta sem RLS
→ gap de conformidade
```

---

# 18. Execução pelo Codex

Depois da canonização da baseline, o Codex não deve receber apenas um prompt genérico para "construir o sistema".

Ele deve trabalhar dentro de um universo de decisões previamente definido.

```text
O que construir      → Produto
Como decidir         → PO + Princípios
Como deve parecer    → UI + Design System
Como deve funcionar  → UX
Como programar       → Técnicas
Como estruturar      → Arquitetura
Em que ordem         → Backlog
Como provar          → Rastreabilidade + testes
Quando documentar    → MAE / MFEE
Quando terminou      → Gates + staging
```

## Fluxo esperado de cada fatia

```text
Selecionar item canônico do backlog
        ↓
Ler origens documentais
        ↓
Verificar dependências e princípios
        ↓
Implementar a menor fatia coerente
        ↓
Criar/atualizar testes
        ↓
Executar gates locais
        ↓
Acionar governança documental quando necessário
        ↓
Atualizar rastreabilidade
        ↓
Publicar em staging
        ↓
Validar evidências
        ↓
Promover
```

---

# 19. Quality Gates

Cada projeto define seus gates concretos no Documento 06, mas a metodologia espera, quando aplicável:

- format check;
- lint;
- typecheck;
- testes unitários;
- testes de integração;
- testes de contrato;
- testes negativos de segurança;
- build;
- verificação de secrets;
- auditoria de dependências;
- verificação de boundaries;
- smoke tests;
- migrações verificadas;
- validação de infraestrutura.

Um item não deve ser considerado entregue apenas porque existe código.

---

# 20. Staging como parte da definição de pronto

A implementação deve ser comprovada em ambiente representativo antes da promoção final quando a natureza do projeto permitir.

```text
CODE EXISTS
≠
DELIVERED
```

E também:

```text
CODE + TESTS PASS
≠
DELIVERED
```

O estado desejado é:

```text
IMPLEMENTADO
+
TESTADO
+
CI APROVADO
+
STAGING VALIDADO
+
RASTREABILIDADE ATUALIZADA
=
ENTREGUE
```

Quando o projeto adotar promoção staging-first, o mesmo artefato ou SHA validado deve ser promovido sempre que possível, evitando reconstruir um candidato diferente do que foi efetivamente testado.

---

# 21. Identidade de produto e prevenção do "visual de IA"

Uma aplicação construída por IA não deve parecer uma composição genérica de componentes populares.

Evitar o padrão automático:

```text
Dashboard
Cards
Sidebar
Modal
Toast
Botão padrão
Tabela padrão
```

sem justificativa de produto.

O processo exige que as decisões de interface sejam derivadas de:

```text
IDENTIDADE DA MARCA
        +
PRINCÍPIOS DE UX/UI
        +
TAREFA MENTAL
        +
CONTEXTO
        +
JORNADA
        ↓
DECISÃO DE INTERFACE
        ↓
DESIGN SYSTEM
        ↓
IMPLEMENTAÇÃO
```

O mesmo agente pode desenvolver produtos diferentes, mas cada produto precisa preservar sua identidade própria.

---

# 22. Estrutura recomendada para documentos canônicos

Quando fizer sentido, documentos podem usar metadados simples no início:

```yaml
---
document_id: DOC-07
title: Arquitetura e Engenharia
status: canonical
version: 1.0.0
depends_on:
  - DOC-02
  - DOC-03
  - DOC-05
  - DOC-06
governs:
  - architecture
  - infrastructure
  - security
---
```

A finalidade é facilitar leitura e governança por humanos e agentes.

O versionamento principal continua sendo o Git. Não criar burocracia documental que não gere valor.

---

# 23. Critério de canonização

Um documento pode ser considerado canônico quando:

1. possui responsabilidade clara;
2. não mistura hipóteses com decisões sem identificá-las;
3. não contradiz documentos de precedência superior;
4. possui escopo e não escopo compreensíveis;
5. pode ser interpretado sem depender da conversa original de Discovery;
6. utiliza linguagem suficientemente objetiva para humanos e agentes;
7. identifica pendências relevantes;
8. está versionado em Git;
9. pode originar requisitos rastreáveis quando aplicável.

---

# 24. Regra de precedência

Em caso de aparente conflito, a resolução deve considerar a natureza da decisão.

Exemplo de precedência conceitual:

```text
Pesquisa / evidência
        ↓
Briefing / escopo
        ↓
Visão do PO
        ↓
Princípios de UX/UI
        ↓
Direção UI + UX
        ↓
Técnicas
        ↓
Arquitetura
        ↓
Backlog
        ↓
Implementação
```

Uma implementação não altera silenciosamente uma decisão de produto.

Se o runtime demonstrar que a decisão anterior é inviável ou inadequada, deve haver reconciliação documental antes de tratar a divergência como novo padrão.

---

# 25. Processo completo resumido

```text
┌─────────────────────────────────────────────┐
│                DISCOVERY                    │
│ conversa, pesquisa, hipóteses e decisões    │
└──────────────────────┬──────────────────────┘
                       │ Discovery Freeze
                       ▼
              01 Pesquisa e Viabilidade
                       ▼
              02 Briefing e Escopo
                       ▼
              03 Visão de Product Owner
                       │
                       ├───────────────┐
                       ▼               │
             Princípios de UX/UI       │
                       │               │
             ┌─────────┴─────────┐     │
             ▼                   ▼     │
      04 Direção de UI      05 Especificação UX
      + Design System       + jornadas/user stories
             └─────────┬─────────┘
                       ▼
              06 Técnicas de Desenvolvimento
                       ▼
              07 Arquitetura e Engenharia
                       ▼
                  MAE / MFEE
                       ▼
              08 Backlog Canônico
                       ▼
              09 Matriz Operacional
                       ▼
                     CODEX
                       ▼
              implementação por fatia
                       ▼
               testes + quality gates
                       ▼
              documentação derivada
                       ▼
                   STAGING
                       ▼
                 evidências
                       ▼
                  promoção
                       ▼
             rastreabilidade atualizada
```

---

# 26. Resultado esperado

Este processo existe para produzir software em que:

- a intenção do produto não dependa da memória da conversa com a IA;
- decisões de experiência possuam princípios claros;
- UI e UX tenham identidade própria;
- tarefas mentais e jornadas sejam especificadas separadamente;
- arquitetura seja consequência de requisitos;
- o backlog possua origem documental;
- testes comprovem critérios de aceite;
- documentação evolua junto com o código;
- MAE e MFEE governem novas gerações documentais sem terem sua lógica interna duplicada;
- staging produza evidência operacional;
- a IA consiga trabalhar com autonomia sem inventar silenciosamente o produto.

A metodologia pode ser resumida em uma frase:

> **A IA não recebe apenas uma tarefa para programar; ela recebe um sistema de decisões canônicas que transforma intenção humana em software verificável.**

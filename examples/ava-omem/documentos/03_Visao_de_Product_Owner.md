---
document_id: DOC-03
title: Visão de Product Owner
status: canonical-example
version: 1.0.0
depends_on:
  - DOC-02
---

# 03 — Visão de Product Owner

## Visão

O AVA OMEM deve ser uma extensão operacional da implantação e capacitação, não apenas uma biblioteca de cursos.

O produto deve ajudar cada pessoa a entender **o que precisa aprender agora** e ajudar a consultoria a entender **onde a aprendizagem está bloqueando a implantação**.

## Princípios de decisão

### 1. Contexto antes de catálogo

O aluno não deve navegar por dezenas de cursos para descobrir o que é relevante. A plataforma deve priorizar trilhas atribuídas conforme empresa, função, módulos contratados e turma.

### 2. Clareza antes de riqueza funcional

Quando houver conflito entre adicionar mais recursos e tornar a tarefa atual mais simples, priorizar a clareza.

### 3. Evidência antes de ornamentação

Progresso, avaliação e conclusão têm maior prioridade que gamificação, feed social ou elementos decorativos.

### 4. Conteúdo reutilizável; atribuição contextual

O mesmo conteúdo deve poder atender vários clientes. Personalizações específicas só devem existir quando houver necessidade real.

### 5. A consultoria governa o treinamento

O cliente acompanha sua equipe, mas o conteúdo e a estrutura pedagógica permanecem sob responsabilidade da consultoria no Beta.

### 6. Progresso também é sinal operacional

Se uma empresa ou turma está parada em uma etapa crítica, isso deve ser visível para o consultor. A plataforma informa; não automatiza decisões de implantação no Beta.

### 7. Especialização sem aprisionamento

A experiência pode usar linguagem e conceitos do OMEM, mas a arquitetura não deve misturar regras de treinamento com detalhes internos do CRM de forma que impeça evolução futura.

### 8. Não antecipar o produto genérico

A possibilidade de vender o AVA para outras empresas de software é uma hipótese estratégica. Não deve gerar campos, módulos ou abstrações sem uso no produto atual.

## Prioridades do Beta

1. segurança e segregação entre empresas;
2. jornada do aluno;
3. criação e atribuição de trilhas;
4. progresso e acompanhamento;
5. avaliações e tarefas;
6. certificados;
7. operação administrativa eficiente;
8. evolução e integrações futuras.

## Trade-offs preferidos

- simplicidade operacional > infraestrutura sofisticada;
- configuração explícita > automação opaca;
- fluxo guiado > dashboard carregado;
- domínio claro > abstração genérica;
- um bom caminho principal > dezenas de variações no Beta;
- manutenção sustentável > velocidade de código descartável.

## Decisões que não podem ser revertidas silenciosamente

- gestor do cliente não edita conteúdo no Beta;
- integração automática com OMEM não é requisito do Beta;
- Protheus não é integração direta do AVA no primeiro corte;
- o aluno deve receber uma experiência orientada a tarefas atribuídas;
- segregação de tenant é requisito crítico;
- toda ampliação que transforme o AVA em LMS genérico deve passar por revisão de produto.
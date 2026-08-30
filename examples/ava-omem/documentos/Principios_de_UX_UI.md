---
title: Princípios de UX/UI
status: canonical-example
version: 1.0.0
depends_on:
  - DOC-02
  - DOC-03
---

# Princípios de UX/UI — AVA OMEM

## P-UX-001 — Uma tarefa mental dominante

### Objetivo

Permitir que o usuário entenda rapidamente o que deve fazer em cada tela.

### Regra

Cada estado principal deve possuir uma ação dominante. Ações secundárias não devem competir visualmente com ela.

### Aplicação

Para o aluno, “Continuar trilha” deve ter mais peso que histórico, certificados ou configurações.

---

## P-UX-002 — Baixa densidade com progressão de complexidade

### Objetivo

Evitar que usuários com pouca familiaridade tecnológica precisem interpretar excesso de informação.

### Regra

Mostrar primeiro o necessário para a tarefa atual. Detalhes administrativos e configurações avançadas aparecem sob demanda.

### Critérios

- evitar cards aninhados sem função clara;
- evitar múltiplas CTAs concorrentes;
- não exibir métricas sem ação associada;
- formulários longos devem ser agrupados por contexto;
- ações raras devem perder hierarquia.

---

## P-UX-003 — Linguagem de treinamento e implantação

### Objetivo

Falar na linguagem de quem aprende e de quem conduz implantação.

### Preferir

- Minha trilha;
- Continuar aula;
- Próxima atividade;
- Equipe em atraso;
- Validar tarefa;
- Módulos contratados.

### Evitar

- entidades;
- registros;
- objetos de aprendizagem;
- persistir;
- executar workflow;
- tenant, quando o texto for voltado ao usuário final.

---

## P-UX-004 — Progresso sempre compreensível

O usuário deve conseguir responder sem cálculo mental:

- onde estou;
- o que já concluí;
- o que falta;
- o que está bloqueando meu avanço;
- qual é a próxima ação.

Percentuais podem existir, mas não substituem indicação clara da próxima etapa.

---

## P-UX-005 — Contexto da empresa deve ser explícito

Administradores e consultores que atuam em vários clientes precisam perceber claramente qual empresa/turma está sendo manipulada.

Ações críticas devem reduzir risco de editar ou convidar pessoas no cliente errado.

---

## P-UX-006 — Ações destrutivas têm baixa exposição

Excluir empresa, curso, turma ou usuário não deve competir com ações de trabalho diário.

Quando a tarefa mental for especificamente confirmar uma exclusão, a hierarquia pode mudar para deixar consequência e confirmação inequívocas.

---

## P-UX-007 — Marca profissional, próxima e didática

A experiência deve comunicar domínio do OMEM sem parecer escolar, infantil ou uma plataforma genérica com logotipo trocado.

A personalidade desejada é:

- profissional;
- clara;
- técnica sem ser fria;
- próxima;
- confiável;
- didática.

Essa personalidade deve influenciar microcopy, hierarquia, iconografia, feedbacks e ritmo da experiência.

---

## P-UX-008 — O aluno vê primeiro o que precisa fazer

A home do aluno não deve nascer como dashboard de métricas. Ela deve funcionar como ponto de retomada.

Prioridade:

```text
próxima ação
   ↓
trilha atual
   ↓
pendências
   ↓
histórico / certificados
```

---

## P-UX-009 — A identidade vem do domínio, não da decoração

A interface deve usar conceitos reais da rotina de treinamento do OMEM — módulos, trilhas, turmas, tarefas práticas, implantação — de forma consistente.

Não copiar visualmente o CRM OMEM. A familiaridade deve vir do vocabulário e do contexto, não de imitação de tela.

---

## P-UX-010 — Feedbacks devem orientar continuidade

Após concluir aula, quiz ou tarefa, o sistema deve informar o resultado e a próxima ação. Mensagens genéricas como “Operação realizada com sucesso” devem ser evitadas quando for possível dizer o que aconteceu.

## Perguntas de avaliação transversal

1. A pessoa entende a tarefa principal em poucos segundos?
2. Existe informação competindo sem ajudar a tarefa atual?
3. O texto fala de trabalho/aprendizagem ou da estrutura interna do sistema?
4. O usuário sabe em qual empresa/turma está?
5. O próximo passo está claro?
6. A tela parece específica para este produto ou poderia pertencer a qualquer dashboard genérico?
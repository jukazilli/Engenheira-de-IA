---
document_id: DOC-05
title: Especificação de UX
status: canonical-example
version: 1.0.0
depends_on:
  - DOC-04
  - Principios_de_UX_UI
---

# 05 — Especificação de UX

## Jornada 1 — Criar cliente e preparar implantação

```text
Consultor abre Empresas
        ↓
Criar empresa
        ↓
Informar dados essenciais
        ↓
Selecionar módulos OMEM contratados
        ↓
Salvar
        ↓
Empresa criada
        ↓
Próxima ação sugerida: criar turma ou convidar gestor
```

### Exceções

- empresa duplicada: avisar antes de concluir;
- erro de rede: preservar campos quando possível;
- sem permissão: bloquear antes de exibir formulário editável.

---

## Jornada 2 — Criar turma e atribuir trilha

```text
Abrir empresa
   ↓
Criar turma
   ↓
definir nome/período/instrutor
   ↓
selecionar público/perfis
   ↓
Engine de atribuição sugere trilhas compatíveis
   ↓
consultor revisa
   ↓
confirma turma
   ↓
convites / matrículas
```

A sugestão de trilha não pode ocultar quais critérios foram usados.

---

## Jornada 3 — Primeiro acesso do aluno

```text
Recebe convite
   ↓
abre link
   ↓
autentica / cria credencial conforme método aprovado
   ↓
aceita acesso à empresa/turma
   ↓
vê Minha trilha
   ↓
identifica próxima atividade
```

### Empty state

Se ainda não houver trilha atribuída, explicar que o treinamento está sendo preparado; não mostrar tela vazia genérica.

---

## Jornada 4 — Consumir aula

```text
Minha trilha
   ↓
Continuar treinamento
   ↓
aula atual
   ↓
consome vídeo/texto/material
   ↓
marca ou sistema registra conclusão conforme regra
   ↓
próxima atividade
```

Se houver pré-requisito não concluído, mostrar qual etapa falta e oferecer caminho direto para ela.

---

## Jornada 5 — Realizar quiz

```text
Abrir avaliação
   ↓
ler instruções
   ↓
responder questões
   ↓
revisar quando permitido
   ↓
enviar
   ↓
resultado
   ↓
Aprovado? ─ sim → próxima etapa
          └ não → orientação de revisão / nova tentativa conforme política
```

Erros de envio não podem apagar respostas já preenchidas quando tecnicamente evitável.

---

## Jornada 6 — Tarefa prática

### Beta

```text
Aluno recebe instrução prática
   ↓
executa atividade no ambiente OMEM apropriado
   ↓
registra conclusão / evidência permitida
   ↓
se validação manual for exigida
        ↓
instrutor recebe pendência
        ↓
aprova ou devolve com orientação
```

O Beta não consulta automaticamente o OMEM para validar a ação.

---

## Jornada 7 — Gestor acompanha equipe

```text
Gestor entra
   ↓
vê somente sua empresa
   ↓
Equipe / Progresso
   ↓
filtra por turma ou trilha
   ↓
identifica não iniciados / em andamento / concluídos
```

O gestor não deve acessar dados de outras empresas nem recursos de autoria de conteúdo.

---

## Jornada 8 — Consultor identifica bloqueio

```text
Acompanhamento
   ↓
lista prioriza atrasos / tarefas pendentes
   ↓
consultor abre aluno ou turma
   ↓
vê contexto do bloqueio
   ↓
executa ação permitida:
- orientar;
- reabrir tentativa, se política permitir;
- validar tarefa;
- ajustar matrícula;
```

O produto informa o sinal; a decisão de implantação continua humana.

---

## Jornada 9 — Conclusão e certificado

```text
Último requisito concluído
   ↓
sistema valida critérios da trilha
   ↓
elegível?
   ├─ não → mostrar pendência concreta
   └─ sim
       ↓
gerar registro de conclusão
       ↓
disponibilizar certificado
       ↓
notificar aluno quando aplicável
```

## User stories prioritárias

### LRN-01

Como aluno, quero abrir o AVA e ver minha próxima atividade para continuar o treinamento sem procurar manualmente o curso correto.

### CON-01

Como consultor, quero configurar os módulos contratados por uma empresa para que as trilhas atribuídas reflitam a implantação real.

### MGR-01

Como gestor do cliente, quero acompanhar o progresso da minha equipe para saber quem ainda precisa concluir treinamento.

### ASM-01

Como instrutor, quero validar uma tarefa prática quando ela exigir conferência humana para registrar a conclusão corretamente.

### CERT-01

Como aluno, quero obter meu certificado quando cumprir os critérios definidos para comprovar a conclusão.

## Reentrada e retomada

Ao voltar para a plataforma, o usuário deve recuperar contexto de forma previsível:

- aluno retorna à próxima atividade pendente;
- consultor retorna à empresa/turma recentemente trabalhada quando seguro;
- formulários não salvos devem alertar antes de abandono quando houver risco de perda.

## Acessibilidade comportamental

- ações não dependem exclusivamente de cor;
- foco de teclado deve acompanhar modais e confirmações;
- vídeos devem suportar legendas quando o conteúdo as fornecer;
- mensagens de erro devem apontar campo e correção;
- timers, se existirem futuramente, não podem ser única forma de concluir tarefa sem necessidade pedagógica.
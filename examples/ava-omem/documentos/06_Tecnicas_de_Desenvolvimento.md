---
document_id: DOC-06
title: Técnicas de Desenvolvimento
status: canonical-example
version: 1.0.0
depends_on:
  - DOC-05
---

# 06 — Técnicas de Desenvolvimento

## Objetivo

Definir como humanos e agentes devem escrever, revisar, testar e entregar código neste projeto.

Este documento é uma **restrição de execução**. Código gerado por IA não recebe exceção de qualidade.

## Linguagem e toolchain

- TypeScript em modo estrito;
- Node.js em versão LTS fixada pela Fundação;
- `pnpm` com versão fixada;
- lockfile obrigatório;
- ESLint ou lint equivalente;
- formatter automático;
- typecheck separado do build;
- testes unitários e de integração;
- Playwright para jornadas E2E críticas.

As versões exatas devem ser travadas no setup depois de validação da documentação oficial da versão adotada.

## Idioma técnico

Código, nomes técnicos, testes, comentários e docstrings devem ser escritos em inglês.

Textos visíveis ao usuário seguem a linguagem definida pela UX e podem estar em português.

Exemplo:

```ts
const pendingLessons = enrollment.lessons.filter((lesson) => !lesson.completed);

function canIssueCertificate(progress: TrainingProgress): boolean {
  return progress.requiredActivitiesCompleted && progress.passedAssessments;
}
```

## Naming

- funções expressam ação: `createEnrollment`, `validateTenantAccess`;
- booleanos são afirmações: `isCompleted`, `canInviteUsers`;
- coleções revelam conteúdo: `activeCohorts`, `pendingAssignments`;
- evitar `data`, `items`, `processData`, `handleThing` quando o significado não for óbvio;
- nomes do domínio devem ser consistentes em todo o repositório.

## Clean Code

O código deve favorecer:

- alta coesão;
- baixo acoplamento;
- dependências explícitas;
- funções com propósito único identificável;
- domínio separado de detalhes de infraestrutura quando a arquitetura exigir;
- fluxo de controle simples;
- estados inválidos tratados explicitamente;
- ausência de código morto;
- ausência de comentários narrando sintaxe.

Evitar arquivos `utils` ou `helpers` que funcionem como depósito genérico.

## Reaproveitamento

Antes de criar função, componente, type, schema ou serviço novo, o agente deve procurar equivalentes no projeto.

```text
necessidade
   ↓
existe implementação semanticamente equivalente?
   ├─ sim → reutilizar/estender
   └─ não
       ↓
há duplicação real e mesma razão de mudança?
   ├─ sim → extrair abstração coerente
   └─ não → implementar localmente
```

Não abstrair apenas porque duas estruturas têm linhas parecidas.

## Dependências

Biblioteca nova exige justificativa. Antes de instalar, verificar:

- se a plataforma já resolve;
- se o projeto já possui capacidade equivalente;
- manutenção e compatibilidade;
- impacto de bundle/runtime;
- segurança;
- lock-in;
- valor real para o projeto.

## Tratamento de erros

Falhas não podem ser silenciosamente ignoradas.

O projeto deve distinguir, conforme contexto:

- erro de domínio;
- erro de validação;
- ausência de permissão;
- falha transitória externa;
- falha de infraestrutura;
- erro inesperado.

Logs não podem expor senha, token, segredo, payload sensível ou dado pessoal desnecessário.

## Performance

Evitar anti-padrões óbvios:

- N+1 queries;
- chamadas de rede redundantes;
- carregar coleção inteira quando a tela exige página;
- recalcular invariantes em loops;
- re-renderização evitável em caminhos críticos;
- consulta sem índice quando o volume e o padrão de acesso justificarem.

Não sacrificar clareza por micro-otimização sem evidência.

## Migrations

- toda mudança de schema é versionada;
- migrations são revisáveis e reproduzíveis;
- não alterar migration já aplicada em ambiente compartilhado para “corrigir histórico”;
- mudanças destrutivas exigem estratégia explícita;
- autorização e índices relevantes devem fazer parte da revisão do dado.

## Testes

### Unitários

Regras de domínio e decisões determinísticas.

### Integração

Banco, autorização, API, contratos e boundaries relevantes.

### E2E

Jornadas críticas:

- primeiro acesso;
- criação de empresa/turma;
- atribuição de trilha;
- conclusão de aula/quiz;
- visão restrita do gestor;
- emissão de certificado.

### Regressão

Bug corrigido com chance real de reaparecer deve deixar teste ou check capaz de detectar a mesma classe de falha.

## Comentários

Comentários técnicos são em inglês e explicam **por quê**, não o que a linha faz.

```ts
// Keep the tenant id from the authenticated context instead of trusting request input.
const tenantId = authContext.tenantId;
```

Código comentado não deve permanecer no projeto.

## Branches, commits e PRs

- commits pequenos e semanticamente coerentes;
- mensagem descreve intenção;
- PR não mistura refatoração ampla com feature sem justificativa;
- diff deve ser revisado pelo próprio agente antes de concluir;
- alterações fora do escopo devem ser evitadas.

## Auto-review obrigatório

Antes de considerar a tarefa pronta, perguntar:

- criei algo que já existia?
- introduzi duplicação?
- nomes revelam intenção?
- existe código morto/debug?
- erros estão tratados?
- testes cobrem comportamento e falhas relevantes?
- a solução respeita boundaries?
- existe impacto óbvio de performance?
- outro engenheiro entenderia este diff sem a conversa original?

## Gates mínimos

Quando aplicável:

```text
format:check
lint
typecheck
test
build
security checks
boundary checks
E2E/smoke
```

## Definition of Done de código

Uma alteração só pode avançar quando:

- código técnico está em inglês;
- naming é consistente;
- não há duplicação evitável;
- dependências novas possuem justificativa;
- testes necessários existem;
- gates passam;
- boundaries arquiteturais são respeitadas;
- não existem segredos no código;
- diff foi auto-revisado;
- implementação pode ser compreendida por outro engenheiro sem depender do chat.

## Regra para agentes

A IA deve consultar documentação correspondente às versões realmente instaladas antes de usar APIs, configurações ou padrões que possam ter mudado.

A velocidade de geração nunca possui precedência sobre a legibilidade e a sustentabilidade da base.
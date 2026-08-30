---
document_id: DOC-06
title: Técnicas de Desenvolvimento
status: canonical-example
version: 1.1.0
depends_on:
  - DOC-05
governs:
  - code-quality
  - code-language
  - naming
  - testing-discipline
  - dependency-policy
  - review-discipline
---

# 06 — Técnicas de Desenvolvimento

## Objetivo

Definir como humanos e agentes devem escrever, revisar, testar e entregar código neste projeto.

Este documento é uma **restrição de execução**. Código gerado por IA não recebe exceção de qualidade.

Este documento define **as propriedades e práticas que a stack precisa sustentar**, mas não escolhe sozinho a stack concreta. Linguagens, runtimes, frameworks, package manager, bibliotecas e ferramentas específicas são definidos posteriormente em `Visao_do_Tech_Lead.md`, depois da aprovação do Documento 07.

## Contrato de qualidade e toolchain

Independentemente das tecnologias escolhidas depois pelo Tech Lead, o projeto exige:

- type safety/strictness compatível com a linguagem adotada;
- runtime e ferramentas com versões reproduzíveis;
- um package manager canônico e lockfile obrigatório;
- lint automatizado;
- formatter automatizado;
- typecheck ou verificação estática equivalente separada do build quando aplicável;
- testes unitários e de integração;
- E2E para jornadas críticas;
- comandos reproduzíveis para os quality gates.

A Visão do Tech Lead deve escolher ferramentas que materializem essas exigências. As versões exatas instaladas são travadas na Fundação depois de validação da documentação oficial e da matriz de compatibilidade aprovada.

## Idioma técnico

Código, nomes técnicos, testes, comentários e docstrings devem ser escritos em inglês.

Textos visíveis ao usuário seguem a linguagem definida pela UX e podem estar em português.

Exemplo conceitual:

```ts
const pendingLessons = enrollment.lessons.filter((lesson) => !lesson.completed);

function canIssueCertificate(progress: TrainingProgress): boolean {
  return progress.requiredActivitiesCompleted && progress.passedAssessments;
}
```

O exemplo utiliza TypeScript apenas para ilustrar legibilidade; ele não é a decisão de linguagem deste documento.

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
- se a biblioteca está aprovada na Visão do Tech Lead para aquela responsabilidade;
- manutenção e compatibilidade;
- impacto de bundle/runtime;
- segurança;
- lock-in;
- valor real para o projeto.

Se uma necessidade exigir biblioteca ainda não prevista, o agente não escolhe oportunisticamente. Ele registra a necessidade e reconcilia `Visao_do_Tech_Lead.md` antes de tratar a dependência como novo padrão canônico.

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
- autorização e índices relevantes devem fazer parte da revisão do dado;
- a ferramenta concreta de migration deve ser definida pelo Tech Lead e permanecer compatível com a infraestrutura aprovada.

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

A ferramenta E2E concreta é definida na Visão do Tech Lead.

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
- usei somente dependências aprovadas para aquela responsabilidade?
- existe impacto óbvio de performance?
- outro engenheiro entenderia este diff sem a conversa original?

## Gates mínimos

Quando aplicável, a stack selecionada deve fornecer comandos equivalentes a:

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

Os nomes concretos dos comandos podem variar, mas o contrato de qualidade não desaparece por causa da ferramenta escolhida.

## Definition of Done de código

Uma alteração só pode avançar quando:

- código técnico está em inglês;
- naming é consistente;
- não há duplicação evitável;
- dependências novas possuem justificativa e aprovação tecnológica quando necessária;
- testes necessários existem;
- gates passam;
- boundaries arquiteturais são respeitadas;
- a stack e os contratos de uso definidos pelo Tech Lead são respeitados;
- não existem segredos no código;
- diff foi auto-revisado;
- implementação pode ser compreendida por outro engenheiro sem depender do chat.

## Regra para agentes

A IA deve consultar documentação correspondente às versões realmente instaladas antes de usar APIs, configurações ou padrões que possam ter mudado.

A velocidade de geração nunca possui precedência sobre a legibilidade e a sustentabilidade da base.

## Relação com as próximas camadas

```text
DOC-06 — Técnicas
como o código deve ser escrito
        ↓
DOC-07 — Engenharia e Arquitetura
o que o sistema precisa suportar e como será estruturado
        ↓
Visão do Tech Lead
quais tecnologias materializam D06 + D07
        ↓
Infraestrutura
onde essa stack será executada
```

Este documento não deve ser alterado apenas para justificar uma biblioteca preferida. Se a stack não consegue cumprir estas técnicas, a escolha tecnológica deve ser reavaliada.
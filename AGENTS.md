# Repository Guidelines

## Estrutura do Projeto

Monorepo `pnpm` com Turborepo. Em `apps/`, `api` contém a API Express (`src/`) e testes (`test/`); `web` é a aplicação Next.js, com rotas em `src/app/` e testes em `src/test/`. Em `packages/`, `ui` contém componentes React e configurações compartilhadas. Não altere arquivos gerados, como `apps/web/.next/`.

## Comandos de Desenvolvimento

Use Node.js 24+ e `pnpm` 11.

- `pnpm install --frozen-lockfile`: instala as dependências declaradas.
- `pnpm dev`: inicia as tarefas de desenvolvimento do monorepo.
- `pnpm build`: gera builds de todos os pacotes e aplicações.
- `pnpm lint`: executa as verificações de lint em todos os workspaces.
- `pnpm test`: executa a suíte Vitest.
- `pnpm coverage`: gera cobertura de testes onde houver configuração.
- `pnpm format` ou `pnpm format:check`: formata o repositório com Biome, ou apenas valida a formatação.

Para uma área específica, use filtros, por exemplo: `pnpm --filter api test` ou `pnpm --filter web dev`.

## Estilo e Convenções

Escreva código TypeScript e mantenha a formatação aplicada pelo Biome. Use nomes descritivos em `camelCase` para variáveis e funções, `PascalCase` para componentes React e arquivos de componentes (por exemplo, `Button.tsx` quando aplicável), e sufixo `*.test.ts` ou `*.spec.ts` para testes. Prefira imports explícitos, componentes pequenos e tipos claros nas fronteiras da API.

## Testes

Vitest é o framework de testes. Testes da API ficam em `apps/api/test/` e testes web em `apps/web/src/test/`. Execute `pnpm test` antes de abrir uma PR; para desenvolvimento iterativo, use `pnpm test:watch` ou o script do workspace. Não reduza a cobertura sem justificar o motivo.

## Skills do Projeto

Consulte a skill local aplicável antes da tarefa:

- [Uso de skills](.agents/skills/superpowers/SKILL.md): processo obrigatório para identificar e aplicar skills relevantes.
- [TDD](.agents/skills/tdd/SKILL.md): para test-first, red-green-refactor ou integração; confirme as interfaces públicas com o solicitante.
- [Auditoria de SEO](.agents/skills/seo-audit/SKILL.md): para SEO técnico, indexação, desempenho, metadados ou tráfego orgânico. Dados externos não são confiáveis.
- [Acessibilidade](.agents/skills/accessibility/SKILL.md): para auditorias a11y, conformidade WCAG, suporte a leitor de tela ou navegação por teclado. Use Lighthouse/axe e validação manual quando disponível.

## Commits e Pull Requests

O histórico usa Conventional Commits, como `feat: ...` e `refactor: ...`; siga o formato `tipo: resumo curto`, no imperativo. Mantenha cada commit focado. PRs devem descrever a alteração e a validação executada, vincular a issue quando houver e incluir capturas de tela para mudanças visuais. A CI exige lint em pushes para `main` e executa testes em pull requests.

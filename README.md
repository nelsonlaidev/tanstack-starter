# TanStack Starter

Minimal starter for building an SSR-enabled React app with TanStack Start + TanStack Router.

## Tech stack

- **React 19**
- **TanStack Start** (SSR)
- **TanStack Router** (file-based routing)
- **Vite**
- **Nitro** (server output)
- **Tailwind CSS v4**
- **TypeScript**
- **ESLint + Prettier**
- **Vitest**
- **Lefthook** (pre-commit formatting/linting)
- **Knip** (dead-code / unused exports detection)

## Requirements

- Node: see [.nvmrc](.nvmrc)
- Package manager: **pnpm** (enforced via `preinstall` in [package.json](package.json))

If you use `nvm`:

```bash
nvm install
nvm use
```

If you don’t have pnpm yet:

```bash
corepack enable
corepack prepare pnpm@latest --activate
```

## Getting started

```bash
pnpm install
pnpm dev
```

Open http://localhost:3000

## Scripts

All scripts live in [package.json](package.json).

| Command                             | Description                                        |
| ----------------------------------- | -------------------------------------------------- |
| `pnpm dev`                          | Start Vite dev server on port 3000                 |
| `pnpm build`                        | Build the app                                      |
| `pnpm start`                        | Start the built server from `.output/`             |
| `pnpm preview`                      | Preview the production build                       |
| `pnpm test`                         | Run unit tests with Vitest                         |
| `pnpm lint` / `pnpm lint:fix`       | Lint (and optionally auto-fix)                     |
| `pnpm typecheck`                    | TypeScript typecheck (no emit)                     |
| `pnpm format` / `pnpm format:check` | Format (and check) with Prettier                   |
| `pnpm knip`                         | Find unused files/exports                          |
| `pnpm check`                        | Run `lint` + `typecheck` + `format:check` + `knip` |
| `pnpm clean`                        | Remove `.output` and `.tanstack`                   |

## Routing

Routes are file-based under [`src/routes/`](src/routes):

- Root route: [`Route`](src/routes/__root.tsx)
- Index route: [`Route`](src/routes/index.tsx)

The route tree is generated into [`src/routeTree.gen.ts`](src/routeTree.gen.ts).

Notes:

- Don’t edit the generated file — it will be overwritten.
- Add new pages by creating new route files inside [`src/routes/`](src/routes).

## Styling

Tailwind is enabled via:

- [`src/styles.css`](src/styles.css)
- Vite plugin config in [`vite.config.ts`](vite.config.ts)

## Devtools

- TanStack Devtools + Router devtools are mounted in the root document (see `RootDocument()` in [`src/routes/__root.tsx`](src/routes/__root.tsx)).

## Git hooks

Pre-commit hooks are configured via [`lefthook.yml`](lefthook.yml):

- Formats staged files with Prettier
- Auto-fixes staged files with ESLint

Install hooks:

```bash
pnpm prepare
```

## Project structure

```text
src/
  routes/            # File-based routes
  router.tsx         # Router creation
  routeTree.gen.ts   # Generated route tree (do not edit)
  styles.css         # Tailwind entry
```

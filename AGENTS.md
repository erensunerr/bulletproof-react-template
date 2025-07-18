AGENTS.md – Project Playbook for Codex

0. Scope
- Applies to the entire repository.

1. Project Map
- `app/` → React Vite app with TypeScript, tests and storybook.
- `docs/` → architecture guidelines and best practices.
- `.github/workflows/` → CI pipelines for lint, test, build, and e2e.
- `.husky/` → git hooks running lint-staged on commit.

2. Coding Standards
- Use ESLint with Prettier. Config in `app/.eslintrc.cjs` and `app/.prettierrc`.
- Keep files and folders in **kebab-case** (`check-file` plugin enforces this).
- Path alias `@/*` maps to `app/src/*`; prefer absolute imports.
- Avoid cross-feature imports; features should only import from shared modules.
- Use single quotes, trailing commas and width 80 via Prettier.

3. Testing Protocol
- Unit & integration tests: `yarn --cwd app test` (Vitest).
- E2E tests: `yarn --cwd app test-e2e` (Playwright, starts mock server).
- Type checking: `yarn --cwd app check-types`.

4. PR & Commit Ritual
- Create feature branches from `master`.
- Run `yarn prepare` once to install app dependencies.
- Ensure `yarn --cwd app lint-staged` passes before commit (Husky hook).
- Write clear commit messages; no strict Conventional Commits required.

5. Programmatic Checks
1. `yarn --cwd app lint`
2. `yarn --cwd app test`
3. `yarn --cwd app check-types`
4. `yarn --cwd app build`
5. `yarn --cwd app test-e2e`

6. Edge‑case Wisdom
- Use Node 20+ and Yarn 1.22+.
- Do not commit `dist/`, coverage, or `.env*` files.
- Generated files like `mocked-db.json` and Playwright reports stay out of git.
- Use `yarn generate` to scaffold new components.

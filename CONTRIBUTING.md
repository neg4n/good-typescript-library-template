# Contributing

## Development Workflow

1. Run `pnpm install` to install dependencies and set up Git hooks via Husky
2. Create a feature branch from `main`
3. Make your changes with conventional commits
4. Push and create a Pull Request
5. CI runs tests, linting, and type checking
6. After approval, rebase and merge to `main`
7. Semantic Release automatically creates and publishes a new version

## Commit Convention

Use conventional commits for automatic versioning:

- `feat:` - New feature (minor version)
- `fix:` - Bug fix (patch version)
- `feat!:` or `BREAKING CHANGE:` - Breaking change (major version)
- `docs:`, `chore:`, `test:` - No version bump

## Husky setup

This project relies on Husky for Git hooks. Husky is installed as a dev dependency, so
the hooks have to be configured locally:

- `pnpm install` (or `npm install`) runs the `prepare` lifecycle script, which invokes
  Husky and writes the hooks into `.git/hooks`.
- The `prepare` script also runs automatically before `pnpm publish`, `pnpm pack`, and
  when installing the project from a Git URL. This ensures the hooks are present for
  contributors and before release builds are created.
- Unlike `postinstall`, `prepare` is skipped for consumers installing the published
  package from the npm registry. That keeps end users from needing Husky (or other dev
  tooling) in their production environments **across all package managers**.

## Code Quality

All code must pass:
- TypeScript type checking
- Biome linting and formatting
- Test coverage requirements
- Pre-commit hooks

## Pull Request Guidelines

- Use descriptive titles and descriptions
- Keep changes focused and atomic
- Ensure all CI checks pass
- Request review from maintainers
- Rebase before merging to maintain linear history

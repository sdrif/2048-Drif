# Contributing Guide

## Branching (GitFlow-light)
- `main`: production, tagged releases `vX.Y.Z`.
- `develop`: integration branch.
- `feature/<id>-<slug>`: new features or refactors.
- `hotfix/<slug>`: urgent fixes from `main`.
- `release/<X.Y.Z>`: release prep from `develop`.

## Commit messages (Conventional Commits)
- `feat:` new feature
- `fix:` bug fix
- `docs:` documentation
- `refactor:` code change without behavior change
- `test:` tests
- `chore:` tooling / CI / build

Example: `feat(board): add left-merge movement`

## Issues → Pull Requests
1. Open an issue using the proper template (🐛 bug, 🧩 feature, 📝 docs).
2. Create a branch `feature/<issueId>-<slug>`.
3. Open a PR to `develop` (or to `main` for hotfix) with:
   - Clear description + “Closes #<issueId>”
   - Checklist (tests, docs, screenshots if UI)
4. **At least 1 review** required; use **squash merge**.

## Quality gates (required to merge)
- **Build & tests:** `mvn -q -DskipTests=false verify`
- **Checkstyle:** comply with repo rules.
- **Mutation testing (PIT):** dedicated workflow must pass.
- **Coverage:** JaCoCo **≥ 80%** (build fails below).
- Required green workflows: `CI`, `Checkstyle (lint)`, `Mutation Testing (PIT)`.

## Versioning & releases
- Semantic Versioning `vMAJOR.MINOR.PATCH`.
- Release = tag + packaged JAR attached (via “Release” workflow).
- Changelog summarized in the release page (PRs list).

## Testing guidelines
- Unit tests per public class.
- Descriptive names: `should<DoX>When<Y>()`.
- Avoid time-sensitive and external IO/network dependencies.

## Style
- **Java 17** everywhere (POM & CI).
- No dead code; avoid `System.out.println` in production—use a logger.

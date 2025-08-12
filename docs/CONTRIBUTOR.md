# Contributing Guide

Thanks for considering a contribution! This document explains how we work on this repo,
the quality gates to pass, and how to get a change merged and released.

## TL;DR
- Branch from `develop` using `feature/<issueId>-<slug>`.
- Follow **Conventional Commits**.
- Make sure **Checkstyle**, **tests**, **coverage ≥ 80% (JaCoCo)** and **PIT** pass.
- Open a PR to `develop` with a clear description and “Closes #<issueId>”.
- At least **one review** required; **squash merge**.

---

## 1) Prerequisites
- Java **17+**
- Maven **3.8+**
- GitHub account with access to this repo

---

## 2) Branching model (GitFlow-light)
- `main` — production, tagged releases `vX.Y.Z`
- `develop` — integration branch
- `feature/<issueId>-<short-slug>` — new features/refactors
- `hotfix/<short-slug>` — urgent fixes from `main`
- `release/<X.Y.Z>` — release prep from `develop`

**Examples**
- `feature/42-add-undo-action`
- `hotfix/fix-crash-on-empty-grid`
- `release/1.1.0`

---

## 3) Commit messages (Conventional Commits)
Format: `type(scope): short summary`

Common types:
- `feat:` new feature  
- `fix:` bug fix  
- `docs:` documentation changes  
- `refactor:` code change without behavior change  
- `test:` tests only  
- `chore:` tooling/CI/build housekeeping

**Examples**
- `feat(board): add left-merge movement`
- `fix(ui): correct "You lose!" message`
- `test(controller): cover mergeRight edge cases`

Keep commits focused and small.

---

## 4) Issues → Pull Requests
1. **Open an issue** using the right template (🐛 bug, 🧩 feature, 📝 docs).
2. **Create a branch** from `develop`: `feature/<issueId>-<slug>`.
3. **Implement** with tests and documentation updates if needed.
4. **Run locally**:
   ```bash
   mvn -q verify                 # build + tests + JaCoCo report
   mvn -q org.pitest:pitest-maven:mutationCoverage   # optional local PIT

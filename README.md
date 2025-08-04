# 🌐 Static Website Deployment with Dev & Prod Environments

This project demonstrates a full CI/CD setup using **GitHub Pages**, **GitHub Actions**, and **Environments** for deploying a static website with two isolated environments:

- 🧪 `development` → auto-deploys from the `dev` branch
- 🚀 `production` → manually approved deployment from the `main` branch

---

## 🌍 Live URLs

| Environment | Branch | URL |
|-------------|--------|-----|
| **Dev**     | `dev`  | [View Dev Site](https://swapnilpawar8767.github.io/env-test/dev-preview/) |
| **Prod**    | `main` | [View Prod Site](https://swapnilpawar8767.github.io/env-test/) |

---

## 🚀 Deployment Strategy

| Step | Description |
|------|-------------|
| ✅ Push to `dev` branch | Auto-deploys to `/dev-preview/` path |
| ✅ Merge `dev` → `main` | Triggers deployment to production |
| 🛑 Manual approval required | Production deployment waits for approval via GitHub UI |
| 📦 GitHub Pages Branch | Uses `gh-pages` branch to serve content |

---

## 🛠️ Workflows

### `.github/workflows/deploy-dev.yml`

- Runs on every push to the `dev` branch
- Deploys to `gh-pages/dev-preview/`
- Registers under `development` environment

### `.github/workflows/deploy-prod.yml`

- Runs on every push to `main` branch
- Requires manual approval
- Deploys to `gh-pages/` root
- Registers under `production` environment

--

## ✅ Manual Promotion Flow

To promote from Dev → Prod:

```bash
git checkout main
git merge dev
git push origin main
Then approve the deployment via GitHub → Actions → Review & Deploy.

💡 Features
GitHub Actions-based CI/CD

Separate environments with custom URLs

GitHub Environments for manual approval & audit log

Deploys via peaceiris/actions-gh-pages

Fully hosted on GitHub Pages — no external infra

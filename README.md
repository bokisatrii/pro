# n8n on Render – self-hosted workflow automation

A ready-to-deploy setup for running [n8n](https://n8n.io/) (open-source workflow automation) on [Render](https://render.com/) with a Postgres database. I use it as a low-cost sandbox for building automations such as lead routing, CRM/email workflows and AI chatbot integrations without writing a backend.

> Based on Render's official [n8n template](https://render.com/docs/deploy-n8n). This repo is the deployment blueprint, not an original application.

## What it deploys

Defined in [`render.yaml`](./render.yaml):

| Resource | Details |
|----------|---------|
| Web service | Runs the official `n8nio/n8n` Docker image |
| Database | Render Postgres, used by n8n to store workflows, credentials and execution data |
| Secrets | `N8N_ENCRYPTION_KEY` is generated automatically to encrypt stored credentials |

Both resources use Render's free plan by default and can be upgraded later.

## Deploy

1. Fork or copy this repo to your GitHub account.
2. In Render, choose **New → Blueprint** and select the repo.
3. Render provisions the database and web service. Open the service URL and create your n8n owner account.

Full instructions: [Render docs – Deploy n8n](https://render.com/docs/deploy-n8n).

## Notes

- Do not change `N8N_ENCRYPTION_KEY` after the first deploy, or previously saved credentials become unreadable.
- Free Render instances have resource limits and may sleep when idle, so use a paid plan for production workflows that must run on schedule.
- The image is pinned to `latest`; pin a specific version if you need reproducible deploys.

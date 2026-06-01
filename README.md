# bigpanda-ansible-aap-test

Smoke-test project for the `bigpanda.incident` Ansible Collection running inside
Ansible Automation Platform.

This repo is intentionally tiny — it just calls one module
(`bigpanda.incident.comment`) so you can verify the collection works end-to-end
from AAP.

## What's here

- `playbooks/smoke_comment.yml` — one task, posts a comment to a BigPanda
  incident.
- `collections/requirements.yml` — declares the collection dependency. AAP
  installs it from Automation Hub at project sync time.

## Variables to supply (from a Job Template's Survey or `--extra-vars`)

| Var              | Where to find it                                      |
| ---------------- | ----------------------------------------------------- |
| `environment_id` | BigPanda env URL (UUID)                               |
| `incident_id`    | BigPanda incident URL (UUID)                          |
| `api_token`      | BigPanda → Settings → User Profile → API Keys         |
| `msg` *(opt)*    | Comment text (default: "Hello from AAP")              |

## Expected outcome

After running, a new comment should appear in the targeted incident in the
BigPanda UI.

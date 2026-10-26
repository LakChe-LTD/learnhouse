# AGENTS.md — LAKCHE Academy (LearnHouse fork)

> **This repo: `LakChe-LTD/learnhouse`** — LakChe LLC's public fork of LearnHouse, the platform behind LAKCHE Academy.
>
> opencode and most coding agents read this file automatically. Claude Code reads it through [CLAUDE.md](CLAUDE.md). If your tool reads neither, paste this file as the first message of the session.
>
> **Résumé (FR)** — Fork public de LearnHouse pour LAKCHE Academy. L'Academy tourne sur l'image officielle, configurée, pas sur ce fork : il reste un miroir non modifié, plus les fichiers LakChe. Aucun identifiant, clé, adresse de serveur ni chemin personnel dans ce dépôt public. Toute modification du code exige un ticket et une décision du CTO, et doit être publiée ici (AGPL-3.0). Gardez LICENSE ; n'ajoutez aucune fonction Enterprise. Le texte anglais fait foi.

---

## 0. Read this first

LAKCHE Academy runs the official LearnHouse image, installed and run with the official CLI and configured in its admin settings. **It is not built from this fork.** This fork exists to follow upstream, and to publish any code LakChe ever changes, as AGPL-3.0 requires. So the useful instinct here is to change nothing: most Academy work is configuration and course content, not code.

Read [LAKCHE.md](LAKCHE.md) for how the Academy runs. Upstream's [README.md](README.md) and [CONTRIBUTING.md](CONTRIBUTING.md) describe the code.

---

## 1. Rules specific to this repo

### 1.1 This repository is public

- Never commit, paste or print any of the following:
  - a credential or an API key, the AI provider's included;
  - a server address;
  - a personal path;
  - a database dump, an export of learners or a document that holds any of them.

  That applies to code, docs, commits, pull requests and comments alike.
- Values live in the instance's `.env` and the password manager only. Operational steps live in the runbook on Confluence (LA space), never here.

### 1.2 Keep the fork thin

- Change the Academy through configuration first: Organization → Settings, the landing-page builder, courses, user groups and certificates.
- A code change needs a ticket that names this repo and the CTO's decision. It is published on a branch here, because AGPL-3.0 entitles the Academy's users to the code they run.
- Keep `LICENSE` and every copyright notice. Do not add or enable anything under LearnHouse's Enterprise licence. This fork has no enterprise folder, and it should stay that way.
- Sync `dev` with upstream releases through a pull request. Never rewrite upstream history.

### 1.3 Learners' data

- Learners' accounts, progress, submissions and certificates are personal data. Never use real ones as test data, and never commit an export.
- Test against a local instance (`npx learnhouse dev`) with test accounts, never against the Academy's production data.

### 1.4 Text and languages

The Academy serves French and English learners. Course content and settings are managed in the instance, not in this repository. Any interface change must hold up in both languages at 360 px.

---

## 2. Commands

| Task | Command |
|---|---|
| Local development | `npx learnhouse dev`: PostgreSQL, Redis, the API, the web app and the collaboration server |
| Self-host commands | `npx learnhouse setup`, `start`, `stop`, `update`, `logs`, `backup` and `doctor`, run on the Academy server by the runbook, never from a laptop against production |
| Everything else | [apps/cli/README.md](apps/cli/README.md) and upstream's [CONTRIBUTING.md](CONTRIBUTING.md) |

---

## 3. House rules

1. Work only from a Jira ticket in the LAKCHE project. Its acceptance criteria define the work. If the ticket's description of the code does not match the code, stop and say so on the ticket.
2. One Jira key per pull request, in the title and the body. Keep it under 400 changed lines and open it against `dev`. Someone other than the author reviews and merges.
3. Branch per ticket: `{type}/{you}/{LC-nn-short-name}`. Conventional Commits: `type(scope): imperative summary`.
4. Never write a secret's value anywhere. Refer to secrets by environment-variable name only, and never commit a `.env` file.
5. If you find a secret in the repo or its history, stop and tell the Tech Lead and the CISO. It is treated as exposed and rotated, not just deleted.
6. Any verbal direction that changes a ticket goes on that ticket the same day, in one line, written by whoever received it ([rule](https://lakchellc.atlassian.net/wiki/pages/viewpage.action?pageId=106856449)).
7. The Definition of Done is LAKCHE-ENG-GOV-001 §3.4 ([Confluence](https://lakchellc.atlassian.net/wiki/pages/viewpage.action?pageId=38928386)).

---

## 4. Stop and ask a human when

- a ticket would change LearnHouse's code instead of the Academy's configuration;
- a change touches the licence, a copyright notice, the "Made with LearnHouse" badge (D7) or anything under the Enterprise licence;
- a run, a script or a test would reach the Academy's production instance or data;
- you would need a value from the server, the `.env` or the password manager;
- public sign-up would open before the Academy's terms and privacy notice are live (D2);
- you find a secret, or personal data, in the repo or its history.

Say what you found and what needs deciding. **Stopping is cheap. Guessing is not.**

---

## 5. Reference

| Document | Covers |
|---|---|
| [LAKCHE.md](LAKCHE.md), [LAKCHE.fr.md](LAKCHE.fr.md) | How the Academy runs, the thin-fork rules, local development |
| [LC-51](https://lakchellc.atlassian.net/browse/LC-51) | Deployment, licence check, upgrade path, and decisions D1–D7 |
| [LC-52](https://lakchellc.atlassian.net/browse/LC-52) | Branding, course structure, link from lakche.com |
| [LA-ENG-LMS-001](https://lakchellc.atlassian.net/wiki/spaces/LA/pages/119341066) (draft) | The Academy runbook |
| [LC-57](https://lakchellc.atlassian.net/browse/LC-57) | These docs |

---

*If something in this file contradicts a ticket, the ticket wins for scope and this file wins for method. If a ticket would change LearnHouse's code, stop and ask.*

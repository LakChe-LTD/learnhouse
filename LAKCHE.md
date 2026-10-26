# LAKCHE Academy

**English** · [Français](LAKCHE.fr.md)

This repository is LakChe LLC's fork of [LearnHouse](https://github.com/learnhouse/learnhouse), the open-source learning platform behind **LAKCHE Academy** (academy.lakche.com, [LC-51](https://lakchellc.atlassian.net/browse/LC-51)). Everything here except `LAKCHE.md`, `LAKCHE.fr.md`, `AGENTS.md`, `CLAUDE.md` and the banner at the top of `README.md` is upstream LearnHouse, and upstream's `README.md` describes the code.

> **This repository is public.** Never commit a credential, an API key, a server address, a personal path, or a document that holds any of them. The Academy runbook lives on Confluence, in the LA space ([LA-ENG-LMS-001, draft](https://lakchellc.atlassian.net/wiki/spaces/LA/pages/119341066)), and values live in the instance's `.env` and the password manager only.

## How the Academy runs

- **The official LearnHouse image, installed and run with the official CLI** (`npx learnhouse@latest setup`, then `start`, `stop`, `update`, `logs`, `backup` and `doctor`). The Academy is not built from this fork.
- **Branding is configuration**, set in Organization → Settings and stored in the database, so upstream updates never overwrite it ([LC-52](https://lakchellc.atlassian.net/browse/LC-52)). The same goes for the landing page, courses, user groups and certificates.
- **Open edition only.** This fork has no enterprise folder, so it runs everything except SSO, audit logs, payments, advanced analytics and SCORM, which sit under LearnHouse's separate Enterprise licence.

## Keep the fork thin

1. **This fork stays an unmodified mirror of upstream**, plus the LakChe files listed above. Change the Academy through configuration first.
2. **A code change needs a ticket and the CTO's decision.** LearnHouse is AGPL-3.0, so if the Academy ever runs modified code, its users are entitled to that code. It is published here, on a branch named after the ticket.
3. **Updates come from upstream releases.** Sync `dev` with upstream through a pull request, then update the instance with `npx learnhouse update`, following the runbook, with a backup first.
4. **Keep `LICENSE` and every copyright notice.** Removing the "Made with LearnHouse" badge is an open decision (D7, [LC-51](https://lakchellc.atlassian.net/browse/LC-51)).

## Develop locally

```bash
npx learnhouse dev
```

This starts PostgreSQL and Redis, then the API (`apps/api`, FastAPI), the web app (`apps/web`, Next.js) and the collaboration server (`apps/collab`). Course work can start on a local instance and be imported later (runbook, step 8.6). See [apps/cli/README.md](apps/cli/README.md) for every command.

## Security

- Report a weakness in LakChe's Academy instance privately to the CISO.
- Report a flaw in LearnHouse itself to upstream, as their README's Security section describes.
- Public sign-up stays closed until the Academy's terms and privacy notice are live (D2, [LC-51](https://lakchellc.atlassian.net/browse/LC-51)).

## Working in this repository

1. **Work from a Jira ticket** in the LAKCHE project. One ticket per branch and pull request, under 400 changed lines, reviewed and merged by someone other than the author.
2. **Branch** as `{type}/{you}/{LC-nn-short-name}` and write Conventional Commits.
3. **Read [AGENTS.md](AGENTS.md)** before any change, with or without an AI agent.
4. **Secrets:** refer to them by name only. If you find one in the repository or its history, stop and tell the Tech Lead and the CISO. It is rotated, not just deleted.
5. **Verbal directions** that change a ticket go on that ticket the same day, in one line, written by whoever received them ([rule](https://lakchellc.atlassian.net/wiki/pages/viewpage.action?pageId=106856449)).

## Links

| What | Where |
|---|---|
| Deployment, licence check and upgrade path | [LC-51](https://lakchellc.atlassian.net/browse/LC-51) |
| Branding, course structure, link from lakche.com | [LC-52](https://lakchellc.atlassian.net/browse/LC-52) |
| Runbook (EN) and implementation guide (FR), drafts | [LA-ENG-LMS-001](https://lakchellc.atlassian.net/wiki/spaces/LA/pages/119341066), [guide FR](https://lakchellc.atlassian.net/wiki/spaces/LA/pages/119308293) |
| These docs | [LC-57](https://lakchellc.atlassian.net/browse/LC-57) |
| Definition of Done | [LAKCHE-ENG-GOV-001 §3.4](https://lakchellc.atlassian.net/wiki/pages/viewpage.action?pageId=38928386) |

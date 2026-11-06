**English** · [فارسی](README.fa.md)

# claude-code-seo-kit — an SEO project starter for Claude Code

A reusable starter for running SEO projects with Claude Code. Drop in a site export, let Claude act as your SEO lead, and get audits, prioritized sprints and reports, with a safe-change workflow and one folder per site.

> The built-in instructions (`CLAUDE.md`, `docs/`, slash commands) are written in Persian. Claude answers in the language you write to it.

## Getting started

1. Run `claude` inside this folder.
2. Run `/new-project` to fill in the **PROJECT CONTEXT** section of `CLAUDE.md`.
3. Put the SEO AI Export output in `data/ai-pack/`. Put Search Console exports (if you have them) in `data/gsc/`.
4. Suggested first message: "Where should I start?"

## Using it as a starter (project template)

The starter's version lives in `starter.json`, and changes are logged in `CHANGELOG.md`.

1. Push this folder to GitHub as a **private** repo and enable **Template repository** in Settings. Never commit real project data to the starter.
2. For each new project:
   ```
   gh repo create <project-name> --template <username>/<starter-name> --private --clone
   ```
   or on the web: **Use this template → Create a new repository**.
3. Inside the new project folder run `claude`, then `/new-project` to be asked for PROJECT CONTEXT and have it filled in.
4. Every project gets its own folder and its own repo. Always run `claude` inside the project's own folder, not a parent folder, so context and memory of different projects don't mix.
5. Starter improvements don't reach existing projects automatically; update them with `/sync-starter` (see below).

## Updating existing projects from the starter

Run `claude` inside the project folder and type `/sync-starter`. It:

- adds the starter as a remote named `template`, fetches it, and summarizes `CHANGELOG.md` from the project's version up to the latest;
- compares only the paths listed in `sync_paths` of `starter.json`: `docs/`, `.claude/commands/`, `.claude/settings.json` and `.gitignore`;
- **never** overwrites `CLAUDE.md`, `notes/`, `data/` or `reports/` (the one exception is the one-time 1.0 → 1.1 migration, which shows you the result and asks first);
- does a three-way merge when both the starter and you changed the same file, and asks on conflicts;
- asks for confirmation file by file, makes a single `chore: sync starter ...` commit, and does not push.

**One-time note for older projects:** projects created before 1.1 don't have `/sync-starter`. Copy `.claude/commands/sync-starter.md` from the starter repo into the same folder once, and the command works from then on.

**To keep the starter updatable:** after every meaningful change, bump the version in `starter.json` and `CHANGELOG.md`, and tag the same commit (for example `git tag v1.3.0 && git push --tags`). With tags, `/sync-starter` can tell starter changes apart from local changes.

## Structure

| Path | Purpose |
|------|---------|
| `CLAUDE.md` | Project-specific only: PROJECT CONTEXT and memory. Imports the general rules and is never synced |
| `docs/core-rules.md` | General rules (role, golden rules, KPIs, memory rules). Imported from `CLAUDE.md`, so always loaded |
| `docs/` | The other references, read only when their topic comes up |
| `starter.json` · `CHANGELOG.md` | Starter version and the list of syncable paths |
| `notes/MEMORY.md` | Short project memory (80-line cap), loaded automatically |
| `notes/decisions.md` · `sprint.md` · `digests/` · `archive/` | Decision details, sprint, digests of large files, archive |
| `data/` | Exports (not tracked by git): `ai-pack/` plugin export, `gsc/` Search Console, `competitors/` competitor data, `archive/` older exports |
| `reports/` | Final reports |
| `.claude/settings.json` | Shared project permissions: reading `.env`, keys and SQL files is denied (personal settings go in `settings.local.json`, outside git) |
| `.claude/commands/` | Commands: `/new-project`, `/competitors`, `/sync-starter`, `/wrapup`, `/memory-cleanup`, `/digest` |

## Workflow

- **Every new export:** move the previous export to `data/archive/<date>/`, put the new one in `data/ai-pack/`, then run `/memory-cleanup` so lines that depended on the old export get re-checked.
- **Very large file:** `/digest data/ai-pack/seo_audit.json`
- **Competitor analysis:** put competitor exports in `data/competitors/` and run `/competitors`.
- **End of every session:** `/wrapup`
- **Every so often:** `/memory-cleanup`, then `git diff notes/MEMORY.md` for a quick review.

## Notes

- Restrict Claude Code's permissions to this folder only.
- Don't keep passwords, API keys or database backups in this folder.
- The memory-update rule (in `docs/core-rules.md`) is guidance, not enforcement. If Claude forgets, run `/wrapup` yourself.
- No automatic end-of-session hook is included on purpose: a Stop hook fires after every reply, not just at the end of a session, and gets annoying. If you want one, we can set it up separately.

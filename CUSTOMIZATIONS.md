# Customizations

Personal fork of [tamaratran/fast-jev-compaction](https://github.com/tamaratran/fast-jev-compaction), tracking upstream, not contributing back. My changes live on the `mattb/main` branch; `main` stays clean for upstream comparison.

Adopted 2026-10-04. Security vetted at upstream commit `e3f262a7f4d42bd8dd32ced30d26176f7cb545b0`. Later upstream commits are NOT vetted.

## Changes

- 2026-10-04: `CUSTOMIZATIONS.md`, `.github/workflows/sync-upstream.yml`: added by repo-adopt. Sync is fetch only (see below).

## Syncing upstream

The weekly Action only reports new upstream commits and the files they touch. It never merges or pushes. To take an update, review the upstream diff first, then:

```bash
git fetch upstream
git diff e3f262a7f4d42bd8dd32ced30d26176f7cb545b0..upstream/main --stat
git checkout main && git merge --ff-only upstream/main && git push origin main
git checkout mattb/main && git merge main
```

## License reminder

Upstream license: **MIT**. Permissive, adapt freely. Attribution required if you redistribute.

## Vetting conditions

Verdict: **CONDITIONAL** (4 stage scan, 2026-10-04: no malicious code or prompt injection found).

- The hook automatically sends your last 3 prompts, the full text of every message, and every tool call name and input (cut to 1,000 chars) to api.typesafe.ai once context passes 60%. No redaction, no prompt. Tool outputs are not sent.
- Never enable it in sessions touching Yardi, AppFolio, tenant, lease, owner, deal or financial data, or credentials. Enable per project, never in user wide settings. Blocked for UCPM data until TypeSafe is named in writing (ucpm-data-privacy).
- Register THIS fork, never upstream, as the plugin marketplace: `claude plugin marketplace add WanderingStardust79/fast-jev-compaction`.
- Never merge upstream devin/* branches or open PRs 124 and 113 (endpoint override via env var) without a fresh review. After any sync check for new uses of $.process, $.fs, $.mcp, changes to the URL in src/request.ts, and new files under hooks/ or .claude-plugin/.
- Function hooks are an early access Claude Code feature (CLAUDE_CODE_ENABLE_FUNCTION_HOOKS=1, types pinned to 2.1.274). Regenerate types and re run tests after every Claude Code upgrade.
- Read upstream issues 99 (Jev may not beat head and tail), 98, 102 and 107 before investing customization time.
- Check TypeSafe retention and training terms for the key you use.

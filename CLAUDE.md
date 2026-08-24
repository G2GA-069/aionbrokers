# AION Brokers — Claude Code instructions

## Repository ownership
This is a sole-owner project. There are no reviewers, no collaborators, no approval gates.

## Commit workflow — MANDATORY
**Commit directly to `main`. Never create a branch. Never open a pull request.**

Every enrichment pass must end with:
```
git add enrichment/diff-YYYY-MM-DD.md
git commit -m "Weekly enrichment pass YYYY-MM-DD"
git push -u origin main
```

No branch. No PR. No `hub pr create`. No `gh pr create`. No `mcp__github__create_pull_request`. These are permanently banned in this repo.

## Enrichment routine
- Output file: `enrichment/diff-YYYY-MM-DD.md`
- Do **not** modify `index.html` under any circumstances
- If the diff file for today already exists, append a timestamped section rather than overwriting

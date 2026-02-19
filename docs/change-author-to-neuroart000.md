# Change commit author to neuroart000

Run these in the repo root (`intelligent-trading-bot`).

## 1. Set Git identity for this repo (future commits)

```bash
git config user.name "neuroart000"
git config user.email "neuroart000@users.noreply.github.com"
```

(Use your real email if you prefer; the no-reply address is from GitHub: Profile → Settings → Emails.)

---

## 2. Change author on existing commit(s)

### Option A: Only the last commit

```bash
git commit --amend --author="neuroart000 <neuroart000@users.noreply.github.com>" --no-edit
```

### Option B: Last 5 commits (or any number)

Replace `5` with how many commits to rewrite:

```bash
git rebase -i HEAD~5 --exec 'git commit --amend --author="neuroart000 <neuroart000@users.noreply.github.com>" --no-edit'
```

When the editor opens, save and close (e.g. in vim: `:wq`). Git will re-apply each commit with the new author.

### Option C: All commits on this branch (from root)

```bash
git rebase -i --root --exec 'git commit --amend --author="neuroart000 <neuroart000@users.noreply.github.com>" --no-edit'
```

---

## 3. If you already pushed

History was rewritten, so you must force push:

```bash
git push --force-with-lease
```

Only do this on a branch you own (e.g. your branch or `main` on neuroart000’s repo). Don’t force push on shared branches others use.

---

## Quick copy-paste (last commit only)

```bash
cd C:/Workspace/vscode/intelligent-trading-bot
git config user.name "neuroart000"
git config user.email "neuroart000@users.noreply.github.com"
git commit --amend --author="neuroart000 <neuroart000@users.noreply.github.com>" --no-edit
git push --force-with-lease
```

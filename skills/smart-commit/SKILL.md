---
name: smart-commit
description: Stage all git changes, inspect staged files and diffs, generate a meaningful commit message, commit, and push to remote. Use when a user asks to commit and push current worktree changes with a high-quality commit message.
---

# Smart Commit and Push Workflow

Follow this workflow in order.

## Steps

1. **Stage all changes**

```bash
git add .
```

2. **Check staged files**

```bash
git diff --cached --name-status
```

Stop and report if no files are staged.

3. **Review staged changes**

```bash
git diff --cached
```

4. **Generate a meaningful commit message**

Write a subject line that:
- Is concise and descriptive (50-72 characters)
- Uses imperative mood
- Groups related changes clearly
- Mentions specific components/files when the change is focused
- Uses conventional commit prefixes when the repository uses them (`feat:`, `fix:`, `refactor:`, `docs:`, `style:`, `test:`, `chore:`)

Example patterns:
- `feat: Add user profile validation`
- `fix: Resolve navigation inconsistency in org form`
- `refactor: Replace any types with proper interfaces`
- `docs: Update README with setup instructions`
- `style: Fix text color in feature cards`

5. **Commit with the generated message**

```bash
git commit -m "<meaningful commit message>"
```

6. **Push to remote**

```bash
git push
```

If pushing a new branch for the first time:

```bash
git push -u origin <branch-name>
```

## Notes

- If push fails because remote has new commits, rebase and push again:

```bash
git pull --rebase origin <branch-name>
git push
```

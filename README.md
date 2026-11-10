# Smart Commit

An agent skill that stages the current repository changes, reviews the staged diff, writes a meaningful commit message, commits, and pushes the current branch.

## Install

### Codex

Ask Codex:

```text
$skill-installer install https://github.com/harunhuskic/smart-commit/tree/main/skills/smart-commit
```

The skill becomes available on the next turn.

### Agent Skills CLI

```bash
npx skills add https://github.com/harunhuskic/smart-commit --skill smart-commit
```

### Manual installation

Clone this repository, then copy `skills/smart-commit` into your agent's skills directory.

Codex on macOS or Linux:

```bash
git clone https://github.com/harunhuskic/smart-commit.git
mkdir -p ~/.codex/skills
cp -R smart-commit/skills/smart-commit ~/.codex/skills/smart-commit
```

Codex on Windows PowerShell:

```powershell
git clone https://github.com/harunhuskic/smart-commit.git
New-Item -ItemType Directory -Force "$env:USERPROFILE\.codex\skills" | Out-Null
Copy-Item -Recurse smart-commit\skills\smart-commit "$env:USERPROFILE\.codex\skills\smart-commit"
```

Restart the agent if it does not discover the skill immediately.

## Use

Invoke it explicitly:

```text
$smart-commit commit and push my current changes
```

Or ask naturally:

```text
Review these changes, write a good commit message, commit them, and push the current branch.
```

The skill will:

1. Stage all working-tree changes.
2. Inspect the staged file list and diff.
3. Generate a concise commit message that follows the repository's conventions.
4. Commit the staged changes.
5. Push the current branch, setting its upstream when needed.

## Safety

The skill runs `git add .`, so review the working tree before invoking it. Do not keep secrets, credentials, generated artifacts, or unrelated changes in the repository unless they are intentionally part of the commit.

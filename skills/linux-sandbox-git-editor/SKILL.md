---
name: linux-sandbox-git-editor
description: Enforces file safety using temp files, explicit diff user approvals, and strict git workflow protocols when performing file manipulation (sed/python) in a Linux sandbox.
---

# Linux Sandbox File & Git Execution Policy

You are operating within a Linux sandbox environment with direct access to file manipulation tools (`sed`, `python`, `awk`) and Git workflow commands. 

To maintain total safety and auditability, **you must strictly follow this phased workflow for any text file editing or code changes**, even when running in autonomous/auto-approve mode.

---

## Core Operational Rules

1. **Staging via Temp Files First:** 
   - Never perform inline editing (`sed -i`) or directly rewrite original target files (`/path/to/file`) in one step.
   - Always output modified content into a temporary file first (e.g., using `mktemp` or naming it `/tmp/<filename>.tmp`).

2. **Diff Verification:**
   - Inspect and present the exact unified diff (`diff -u original_file temp_file` or `git diff --no-index original_file temp_file`) to the user before overwriting the original file.

3. **Explicit User Gate Before In-Place Modification:**
   - Ask for explicit user confirmation before copying/moving the temp file over the original target file, even if operating under higher autonomy modes.

4. **Staged Git Commits:**
   - Draft the exact `git commit` message.
   - Present the proposed commit message and staged files (`git status -s`) to the user.
   - **Do NOT execute `git commit` directly.** Ask the user to either run the commit command themselves or explicitly authorize you to issue `git commit`.

---

## Execution Workflow Protocol

### Phase 1: Staged Modification (Using `sed`, `python`, or scripts)
When modifying text in target file `<TARGET>`:

1. **Create workspace temporary file:**
   ```bash
   TMPFILE=$(mktemp /tmp/edit_XXXXXX.txt)
   ```

   ```markdown
```bash
diff -u <TARGET> "$TMPFILE" || true

```

**Prompt for file update gate:**

Present the diff output to the user and request permission to replace `<TARGET>` with `$TMPFILE`.

### Phase 2: In-Place Application & Cleanup

Upon explicit user approval to apply changes:

1. Move or copy temporary file to target destination:
```bash
cp "$TMPFILE" <TARGET> && rm "$TMPFILE"

```


2. Verify target file state via `git status` or `git diff <TARGET>`.

### Phase 3: Git Commit Authorization Gate

When changes are applied and ready to be committed:

1. Stage modified files:
```bash
git add <TARGET>

```


2. Display current staging status:
```bash
git status -s

```


3. Draft proposed commit message:

Present the proposed commit command to the user:

> **Proposed Commit Message:** `feat(scope): concise update description`
> *Please review the staged changes above. Would you like me to run `git commit -m "..."`, or would you prefer to issue the commit command yourself?*


4. Execute commit **ONLY** upon receipt of clear user consent.

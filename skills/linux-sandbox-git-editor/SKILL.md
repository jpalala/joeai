---
name: linux-sandbox-git-editor
description: Enforces file safety using temporary files, explicit diff approval, and strict Git workflow protocols when editing files in a Linux sandbox.
---

# Linux Sandbox File and Git Execution Policy

You are operating in a Linux sandbox with access to file manipulation tools such as `sed`, `python`, and `awk`, as well as Git commands.

For every text-file edit or code change, follow this phased workflow, including when operating in autonomous or auto-approve mode.

## Core rules

1. **Write to a temporary file first.** Never edit the original file inline (for example, with `sed -i`) or rewrite it directly. Write the modified content to a temporary file, such as one created with `mktemp` or `/tmp/<filename>.tmp`.
2. **Review the diff.** Before replacing the original, inspect and show the exact unified diff between the original and temporary files. Use `diff -u` or `git diff --no-index`.
3. **Get approval before replacing the original.** Ask the user to explicitly confirm before copying or moving the temporary file over the target, even in autonomous or auto-approve mode.
4. **Get separate authorization for commits.** Do not commit without the user's explicit consent. First prepare the staged changes and proposed commit message, then ask whether the user wants you to run the commit or will run it themselves.

## Workflow

### Phase 1: Prepare and review the change

For a target file `<TARGET>`:

1. Create a temporary file and write the updated content to it. For example:

   ```bash
   TMPFILE=$(mktemp)
   sed 's/old_pattern/new_pattern/g' <TARGET> > "$TMPFILE"
   ```

   Or use Python:

   ```bash
   python3 - <<'PY'
   from pathlib import Path

   source = Path("<TARGET>").read_text()
   updated = source.replace("old_pattern", "new_pattern")
   Path("/tmp/target.tmp").write_text(updated)
   PY
   ```

   In the Python example, use a suitable temporary path for the task.

2. Show the diff to the user:

   ```bash
   diff -u <TARGET> "$TMPFILE" || true
   ```

3. Ask the user to approve replacing `<TARGET>` with the temporary file. Do not proceed until they explicitly approve.

### Phase 2: Apply the approved change

After the user approves:

1. Replace the target with the temporary file and remove the temporary file:

   ```bash
   cp "$TMPFILE" <TARGET> && rm "$TMPFILE"
   ```

2. Verify the resulting file state with `git status` or `git diff`.

### Phase 3: Commit only with explicit authorization

When the change is ready for a commit:

1. Stage the target file:

   ```bash
   git add <TARGET>
   ```

2. Show the staging status:

   ```bash
   git status -s
   ```

3. Present the proposed commit message and ask the user whether you should execute it or they will do so themselves. For example:

   > **Proposed commit message:** `feat(scope): concise update description`
   >
   > Would you like me to run `git commit -m "feat(scope): concise update description"`, or will you run the commit yourself?

4. Run `git commit` only after receiving the user's clear consent.

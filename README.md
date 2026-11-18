# Repo Archaeology

**Understand the code you built. Clear the knowledge debt you left behind.**

Repo Archaeology is a shared skill for **Claude Code and Codex**. It helps you explain a repository's purpose, trace a feature across files, understand documented decisions, and check what you can explain independently.

Knowledge debt is the gap between code you have built and code you understand. This skill turns that gap into a guided reading route, worked examples, and focused practice.

It is an instruction-based skill. There is no server, custom installer, or package dependency to run. You need Git and an existing Claude Code or Codex installation with access to the repository you want to study.

## Install

Choose your tool below. These commands install the skill for your user account; they do not install it into the repository you want to study. You can install it for both tools.

Run installation commands in a terminal. If the destination already exists, inspect it first. Update an existing Repo Archaeology installation using the instructions below, or move an unrelated folder aside yourself. Do not overwrite it blindly.

### Claude Code

```bash
mkdir -p "$HOME/.claude/skills"
git clone https://github.com/Rick-Clinton-jpg/Repo-Archaeology.git "$HOME/.claude/skills/repo-archaeology"
```

Claude Code normally detects skill changes automatically. If this is your first skills directory, use `/reload-skills` in Claude Code or start a fresh session. Look for `/repo-archaeology` in the command menu.

These instructions target **Claude Code**. Installing this local folder does not upload the skill to Claude web or Cowork; those use separate skill-management settings. See the [Claude Code skills documentation](https://code.claude.com/docs/en/skills).

### Codex

```bash
mkdir -p "$HOME/.agents/skills"
git clone https://github.com/Rick-Clinton-jpg/Repo-Archaeology.git "$HOME/.agents/skills/repo-archaeology"
```

Codex normally detects skill changes automatically. Restart it if the skill does not appear. Select the skill in your skill picker; in Codex CLI or the IDE extension, use `/skills` or mention `$repo-archaeology` in a prompt. These paths follow the [current Codex skills documentation](https://learn.chatgpt.com/docs/build-skills#where-codex-loads-local-skills).

<details>
<summary>Windows PowerShell installation</summary>

For Claude Code:

```powershell
New-Item -ItemType Directory -Force -Path "$env:USERPROFILE\.claude\skills" | Out-Null
git clone https://github.com/Rick-Clinton-jpg/Repo-Archaeology.git "$env:USERPROFILE\.claude\skills\repo-archaeology"
```

For Codex:

```powershell
New-Item -ItemType Directory -Force -Path "$env:USERPROFILE\.agents\skills" | Out-Null
git clone https://github.com/Rick-Clinton-jpg/Repo-Archaeology.git "$env:USERPROFILE\.agents\skills\repo-archaeology"
```

The `-Force` option above creates the parent directory if needed. Git still refuses to clone over an existing non-empty destination. Use the same discovery and invocation steps as above.

</details>

## Start learning

Open **the repository you want to understand** in Claude Code or Codex. Do not start in the installed skill's folder unless you want to study Repo Archaeology itself. If using a terminal, change into your target repository before launching your coding agent.

Enter these prompts **inside the agent's chat, not in your terminal**.

Claude Code:

```text
/repo-archaeology study this repository. I built it with AI and want to understand how it works. Start with the main user journey and explain unfamiliar terms.
```

Codex CLI or IDE:

```text
$repo-archaeology study this repository. I built it with AI and want to understand how it works. Start with the main user journey and explain unfamiliar terms.
```

In a desktop skill picker, select `repo-archaeology` and send the same request without the command prefix. You can also provide a local repository path or a GitHub URL the agent can access.

### Choose how to learn

The words below describe learning modes, not terminal commands or a separate command-line program.

| Mode | What it does | Example request after the skill name |
| --- | --- | --- |
| `study` | Default: builds a guided study sheet with a reading route, a real flow, evidence, and practice. | `study this repo; explain the checkout flow first` |
| `teach` | Teaches one concept at a time and waits for your response. | `teach me how a request becomes a database change` |
| `check` | Uses questions and teach-back to find gaps in your understanding. | `check whether I understand the authentication flow; ask one question at a time` |
| `refresh` | Uses a previous sheet and its recorded commit to explain what changed and what needs relearning. | `refresh using /path/to/my-study-sheet.md and its recorded commit` |

Tell the agent what you already know, what feels unclear, and how much detail you want. For example:

```text
Focus on the core behavior and skim helpers. Use cooking examples. I understand Python, but I don't understand why this project uses a queue.
```

```text
Read exhaustively within this repository. Explain the major decisions and show which files support each explanation. Report anything you could not inspect.
```

The default is targeted reading of the important paths. An exhaustive request expands that scope. The skill should not explore unrelated repositories or every branch simply to fill a template.

## What you get

- A plain-language explanation of the problem the project solves.
- A reading route: which files to read, what to notice, and what question each file answers.
- A worked journey through the actual files and functions, with small code excerpts when useful.
- Source pointers and a distinction between documented intent, implementation, reported results, and inference.
- Questions that ask you to explain a decision or predict the effect of a change.
- A clear account of limitations, unread areas, and missing explanations.

The format adapts to the project. Research results and statistics belong in research repositories; app behavior, interfaces, and failure paths matter in application repositories. See the [study-sheet guide](references/study-sheet.md) and the [illustrative sample session](examples/sample-session.md).

### Save progress when you want it

Answers appear **in chat by default**. To keep a study sheet or learning record, explicitly request a destination outside the repository being studied:

```text
Save the study sheet to /path/to/my-learning-notes/project-study.md and a learning record beside it. Keep the studied repository unchanged.
```

The optional [learning record](templates/learning-record.md) distinguishes:

- **Explained:** the agent covered the concept; your understanding has not yet been demonstrated.
- **Demonstrated:** you explained or applied it successfully in a specific exercise.
- **Unclear:** a gap or misconception still needs work.
- **Not assessed:** no exercise has checked this concept yet.

A saved record includes the repository revision so a future `refresh` can identify outdated explanations. A demonstration is evidence from that exercise, not a permanent mastery score.

## Read-only study and evidence

The skill inspects source files, documentation, existing results, and relevant history. It does **not** run the studied project's code, tests, installers, or build commands, and does not edit, commit, or push changes to that project. File-reading and Git inspection tools are allowed. Producing requested learning notes outside the target repository is separate from changing its code.

Reading a test shows what it checks; it does not establish that the test passes. Code inspection does not establish runtime correctness. Reported results retain their provenance, and undocumented motivations remain unknown or explicitly labelled as inference.

## Update or remove

Update the installed copy for your tool:

```bash
# Claude Code
git -C "$HOME/.claude/skills/repo-archaeology" pull --ff-only

# Codex
git -C "$HOME/.agents/skills/repo-archaeology" pull --ff-only
```

In PowerShell, use `$env:USERPROFILE` instead of `$HOME` if needed. If Git reports local changes or a non-fast-forward update, inspect and preserve your edits before resolving the conflict. The update commands intentionally do not reset or discard them. If you installed both copies, update both.

To uninstall, delete the `repo-archaeology` folder from the appropriate skills directory after preserving any edits you want to keep. This does not delete separately saved study sheets or learning records. Reload or restart the agent if the skill remains listed.

## Repository contents

| File | Purpose |
| --- | --- |
| [SKILL.md](SKILL.md) | Shared instructions loaded by Claude Code and Codex. |
| [references/study-sheet.md](references/study-sheet.md) | Guidance for adapting a full study sheet to the project. |
| [templates/learning-record.md](templates/learning-record.md) | Optional record for evidence, exercises, and remaining gaps. |
| [examples/sample-session.md](examples/sample-session.md) | An illustrative learning exchange showing the intended experience. |
| [agents/openai.yaml](agents/openai.yaml) | Optional Codex display metadata. |

## Contributing

Useful contributions improve an observed learning failure: a confusing explanation, an unsupported claim, a missing connection between files, or an installation problem. Include the prompt, expected behavior, and a small non-sensitive example. Keep the shared skill portable and avoid adding mandatory steps for cases that only some repositories need.

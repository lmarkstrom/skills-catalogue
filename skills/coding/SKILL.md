---
name: coding
description: >-
  Governs how the agent writes, edits, and presents code. Use this skill for
  any task involving writing new code, modifying existing code, reviewing diffs,
  or explaining code. Covers language style, comments, context presentation,
  and editing behaviour.
---

# Coding

## Language

Primary language is **Python**. Apply Python-specific rules by default unless
the file or project clearly uses another language.

---

## Style

- **Follow the project's existing conventions first.** Check for a `pyproject.toml`,
  `setup.cfg`, `.flake8`, `ruff.toml`, or `.editorconfig` and honour whatever
  is configured there (line length, quote style, import order, etc.).
- If no config exists, use sensible modern defaults:
  - [PEP 8](https://peps.python.org/pep-0008/) formatting
  - Double quotes for strings
  - Type hints on all new function signatures
  - `ruff`-compatible style (no unused imports, no shadowed builtins)
- Use **TODO:** on places where code is missing or needs to be implemented
- Reuse existing helpers and minimize duplication.
- Always optimize for **clarity** and **simplicity** over cleverness or brevity.

---

## Comments

- **Minimal** — only comment non-obvious logic, algorithms, or gotchas.
- Keep comments **short** and **to the point**. Avoid long paragraphs.
- Do **not** add comments that restate what the code does:
  ```python
  # ❌ Increment counter by 1
  counter += 1

  # ✅ Wrap at 80 chars to match terminal width
  line = textwrap.fill(text, width=80)
  ```
- Use **docstrings** on public functions and classes (Google style):
  ```python
  def parse_config(path: str) -> dict:
      """Load and validate a YAML config file.

      Args:
          path: Absolute path to the config file.

      Returns:
          Parsed config as a dictionary.

      Raises:
          FileNotFoundError: If the file does not exist.
      """
  ```
- Private/internal helpers do not need docstrings unless the logic is tricky.

---

## Editing Existing Code

- **Show only the changed lines plus a few lines of surrounding context** — never
  dump an entire file when only one function changed.
- Never silently rewrite unrelated parts of a file.

---

## Context Awareness

- Before writing or editing, **read the relevant file(s)** to understand naming
  conventions, imports already in use, and existing patterns — do not introduce
  a new style that clashes with what's already there.
- Reuse existing helpers and utilities rather than reimplementing them.
- If a change requires touching multiple files, state which files are affected
  before making edits.

---

## What to Avoid

- Boilerplate or placeholder code (`pass`, `TODO`, `# implement me`) unless
  the user explicitly asks for a skeleton.
- Wrapping every single line in a comment.
- Changing formatting or style in lines that weren't part of the requested edit.
- Printing the full file contents when only a section changed.
- Using deprecated APIs or patterns when a modern equivalent exists.
- Making large unnecessary changes to a file when a small surgical change is requested.
- Complicate or make refactoring changes without a clear reason or user request.

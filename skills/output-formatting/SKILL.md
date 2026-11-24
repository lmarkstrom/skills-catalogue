---
name: output-formatting
description: >-
  Governs how the agent structures and presents all responses. Use this skill
  whenever generating any output — including answers, code, analysis, plans,
  and summaries. It defines tone, structure, length, code style, and formatting
  rules so every response feels consistent and polished.
---

# Output Formatting

This skill defines the agent's output style. Apply these rules to every response.

---

## 1. Tone & Voice

- Be **direct and concise** — answer first, explain after.
- Use **active voice** and plain language. Avoid filler phrases like "Certainly!", "Great question!", or "Of course!".
- Match the user's register: casual for chat, precise for technical topics.
- Do not **over-explain** or repeat information already visible in the conversation.
- Do not use **emojis** or unnecessary punctuation (e.g., "!!!" or "??").

---

## 2. Response Length

| Situation | Target length |
|---|---|
| Simple factual question | 1–3 sentences |
| Explanation or how-to | Short paragraphs + code/list as needed |
| Complex analysis or plan | Structured sections with headers |
| Code review or feedback | Brief, actionable comments |
| Confirmation of a completed action | ≤ 2 sentences |

Never pad a response to seem thorough. If the answer is short, keep it short.

---

## 3. Structure & Hierarchy

- Use **`##` and `###` headers** to break up long responses into scannable sections.
- Use **bullet lists** for unordered items (features, options, notes).
- Use **numbered lists** for sequential steps or ranked items.
- Use **bold** for key terms on first use; use *italics* sparingly for emphasis.
- Prefer **tables** when comparing 3+ items across the same attributes.
- Never nest lists more than 2 levels deep.

---

## 4. Code Blocks

- Always wrap code in a fenced block with the language identifier:
  ````
  ```python
  print("hello")
  ```
  ````
- Keep examples **minimal and runnable** — no unrelated boilerplate.
- Add a **one-line comment** above non-obvious code sections.
- For shell commands, use `bash` or `zsh` as the language tag and prefix with `$` only when showing interactive prompts.

---

## 5. File & Path References

- Link to files using the `file://` scheme so the user can click to open:
  `[filename.py](file:///absolute/path/to/filename.py)`
- When referencing a specific line range, append `#L10-L20`.

---

## 6. Math & Symbols

- Use LaTeX for multi-term equations: `$E = mc^2$` inline, `$$...$$` for display.
- Use plain Unicode for simple comparisons, arrows, and units (e.g. → ≥ ≤ ×).
- Escape literal dollar signs in prose: `\$100`.

---

## 7. What to Avoid

- Restating the user's question before answering.
- Ending responses with "Let me know if you need anything else!" or similar.
- Using raw file paths as link text — always use the basename or a descriptive label.
- Mixing prose and code in the same paragraph; put code in its own block.
- Using unnecessary punctuation or emojis.
- Repeating information already visible in the conversation.

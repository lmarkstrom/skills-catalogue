---
name: planning
description: >-
  Governs how the agent approaches planning and task breakdown. Use this when
  the user has a complex or ambiguous request that requires scoping, sequencing,
  or upfront decisions before work begins. Covers when to ask questions, how to
  present a plan with alternatives, and how to handle uncertainty.
---

# Planning

## When to Plan First

Produce a plan before starting work when the task is:
- **Multi-step** — more than 2-3 distinct actions required
- **Ambiguous** — the right approach is not obvious from the request alone
- **Risky** — involves deleting, overwriting, or deploying something irreversible
- **Large** — touches multiple files, systems, or stakeholders

For simple, clearly-scoped tasks, skip the plan and just do it.

---

## Clarifying Questions

Ask questions before planning, not mid-plan. Rules:

- Ask only what is **blocking** — do not ask for information you can infer or
  look up yourself.
- Max 3 questions per turn. Group related questions together.
- If a decision can be made either way and easily reversed, make a reasonable
  default and state the assumption rather than asking.

---

## Plan File

Write the plan to a file named `PLAN.md` in the project root directory before
doing any work. Do not just show the plan in chat.

### File structure

```markdown
# Plan: <short task title>

## Recommended Approach

One paragraph explaining the chosen approach and why it is the best fit for
this task (trade-offs considered, assumptions made).

## Alternatives

### Option A: <name>
Short description. Pros and cons relative to the recommended approach.

### Option B: <name>
Short description. Pros and cons relative to the recommended approach.

## Steps

1. <Step title>
   - Detail or sub-task if needed.

2. <Step title>
   - Detail or sub-task if needed.

...

## Assumptions

- List any assumptions made that the user should be aware of.

## Open Questions

- List anything that could not be resolved and may need user input mid-plan.
```

### Rules for the plan file

- The **Recommended Approach** section must explain *why* this approach was
  chosen over the alternatives — not just what it is.
- The **Alternatives** section must include at least one other viable option
  with honest trade-offs. If only one approach exists, say so and omit the section.
- Steps must be **concrete and actionable** — each step should map to a
  discrete unit of work, not a vague phase.
- Keep steps ordered so each one can proceed without depending on a later step.
- After writing the file, post a one-line summary in chat with a link to `PLAN.md`
  and wait for the user to approve before starting any work.

---

## Approval Gate

After the plan file is written:
- Wait for the user to confirm before executing any step.
- If the user says "go ahead" or similar, start immediately — do not re-summarise
  the plan.
- If the user modifies the plan, update `PLAN.md` to reflect the change, then proceed.

---

## Mid-Plan Behaviour

- Complete each step fully before moving to the next.
- If a step reveals something that changes the plan, stop and update `PLAN.md`
  before continuing. Report the change in chat in one sentence.
- If a step fails and is blocking, stop and present options — do not improvise
  a workaround without saying so.

---

## What to Avoid

- Producing a plan so detailed it takes longer to read than to just do the task.
- Asking for confirmation on trivial sub-steps once work is underway.
- Silently changing the plan without updating `PLAN.md` and telling the user.
- Starting work before the user has approved the plan on risky or large tasks.
- Presenting only one option when genuine alternatives exist.

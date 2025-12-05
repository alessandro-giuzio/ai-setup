# Copilot Instructions for AI Agents

## Project Overview

- **Purpose:** Centralized docs for AI-assisted dev, code org, and workflow tips.
- **Stack:** Astro (static site), Vue 3 (`<script setup lang="ts">`), TailwindCSS, Supabase, ShadCN UI.
- **TypeScript everywhere**; avoid `any`.

## Key Patterns & Conventions

- **Vue Components:**
  - Use `<script setup lang="ts">` (script first, then template).
  - Composition API only; type all emits/props.
  - Example:
    ```vue
    <script setup lang="ts">
    import { ref } from 'vue';
    const count = ref(0);
    function increment() {
      count.value++;
    }
    </script>
    <template>
      <button @click="increment">Count: {{ count }}</button>
    </template>
    ```
- **Astro:**
  - Use Vue islands for interactivity; keep pages minimal.
  - Example:
    ```astro
    ---
    const { title } = Astro.props
    ---
    <h2>{title}</h2>
    ```
- **Styling:**
  - Tailwind utility classes; no inline styles.
  - Use tokens from `src/styles/global.css`.
- **Supabase:**
  - Centralize client; use typed, narrow selects.
  - Handle loading/error states; never log secrets.
- **Testing:**
  - Use Vitest + Vue Test Utils if tests are requested.

## Developer Workflows

- **Install:** `pnpm install`
- **Dev server:** `pnpm dev`
- **Build:** `pnpm build`
- **Debug:** See `Debug Notes.md` for common issues/fixes.
- **Docs:** See `Dev Notes.md` for recent changes and known issues.

## File Structure

- `src/components` – UI components
- `src/pages` – Route/page components
- `src/styles/global.css` – Tailwind tokens
- `src/services` – API/Supabase logic
- `src/hooks` – Custom hooks
- `tests` – Test files

## Output & File Ops

- Prefer concise diffs/patches.
- List new files as `path/filename` with minimal stub.
- Explain risky changes in 1–2 bullets.

## Constraints

- No legacy Vue Options API.
- No inline styles (unless required).
- Descriptive, camelCase names.
- Avoid hardcoded values; use props/config.
- DRY & KISS principles.

## When Unsure

- Ask one clarifying question only if blocking; otherwise, make a reasonable default and proceed.

## Tailwind

- Write Tailwind like a senior dev who's mass-deleting classes in code review.
- Assume sensible defaults; never add responsive variants unless explicit breakpoint behavior is described.
- Prefer fewer classes that do more (e.g., `space-y`, `divide-x`) over manual margin/padding on children.
- If you're about to write more than 5 utilities on one element, reconsider the markup.
- Consolidate classes; avoid duplicates.
- Suggest reusable patterns (variants/util classes) based on existing tokens.

# Copilot Instructions for AI Agents

## Project Overview

- **Purpose:** Centralized docs for AI-assisted dev, code organization, and workflow tips.
- **Stack:** Astro (static site), Vue 3 (`<script setup lang="ts">`), TailwindCSS, Supabase, ShadCN UI.
- **TypeScript everywhere**; avoid `any` unless absolutely necessary.

---

## Communication

- Default explanations and comments in **English**.
- Short UI copy (labels, placeholders, helper text) can be in **Spanish** when appropriate.
- Prefer concise answers; avoid over-explaining basic JS/TS/Vue unless explicitly requested.
- When suggesting non-trivial changes, include a brief summary (1–3 bullets) of what was done and why.

---

## Key Patterns & Conventions

### Vue Components

- Use `<script setup lang="ts">` (script first, then template).
- Composition API only; **no Options API**.
- Type all props and emits.
- Keep components focused and small; extract reusable parts into separate components or composables.

Example:

```vue
<script setup lang="ts">
import { ref } from 'vue';

const count = ref(0);

function increment() {
  count.value++;
}
</script>

<template>
  <button @click="increment">Count: {{ count }}</button>
</template>
```

### Astro

- Use **Vue islands** for interactivity; keep Astro pages minimal and mostly presentational.
- Do not duplicate logic between Astro and Vue; shared logic belongs in composables/services.

Example:

```astro
---
const { title } = Astro.props;
---
<h2>{title}</h2>
```

### Styling

- Use **Tailwind utility classes**; avoid inline styles unless strictly required by a third-party integration.
- Prefer semantic, utility-based styling over ad‑hoc custom CSS.
- Use tokens and utilities defined in `src/styles/global.css` whenever possible.

### Supabase

- Centralize the Supabase client in a single module.
- Use **typed, narrow selects** instead of `select('*')`.
- Always handle **loading**, **error**, and **empty** states explicitly.
- Never log secrets, tokens, or sensitive data.

### Testing

- When tests are needed or requested, prefer **Vitest** and **Vue Test Utils**.
- Co‑locate tests near the implementation or place them in a `tests/` directory, following existing patterns in the repo.

---

## Developer Workflows

- **Install:** `pnpm install`
- **Dev server:** `pnpm dev`
- **Build:** `pnpm build`
- **Tests:** If a test setup exists, suggest `pnpm test` (or match existing scripts in `package.json`).
- **Lint:** If linting is configured, suggest `pnpm lint` (or match existing scripts).
- **Debug:** See `Debug Notes.md` for common issues and fixes (if present).
- **Docs:** See `Dev Notes.md` for recent changes and known issues (if present).

When proposing commands, prefer **existing npm scripts** from `package.json` over inventing new ones.

---

## File Structure

- `src/components` – UI components
- `src/pages` – Route/page components
- `src/styles/global.css` – Tailwind tokens and global styles
- `src/services` – API and Supabase logic
- `src/hooks` – Custom hooks/composables
- `tests` – Test files

When creating new files, follow this structure unless explicitly instructed otherwise.

---

## Copilot Behavior (Plan & Agent)

- For **large tasks** (multiple files or new features), first propose a short **plan**:
  - Goal
  - Steps
  - Files to be created/modified
- Keep changes in **small, reviewable chunks**.
- When suggesting cross‑file edits (Agent‑style work):
  - List which files will be changed.
  - After proposing changes, summarize them in 1–3 bullets.
  - If tests/typecheck commands exist, recommend running them (do not assume they passed).

---

## Output & File Operations

- Prefer **concise diffs/patches**.
- When suggesting new files, list them as `path/filename` with a minimal but complete stub.
- Explain **risky or breaking changes** in 1–2 bullets, including any migrations or manual steps required.
- Avoid renaming or moving many files at once unless explicitly asked.

---

## Constraints

- No legacy Vue Options API.
- No inline styles (unless required by a specific constraint).
- Use descriptive, `camelCase` names for variables and functions.
- Avoid hardcoded values; use props, configuration, or environment variables where appropriate.
- Follow **DRY** and **KISS** principles.
- Prefer explicit types and strict TypeScript patterns over convenience.

---

## When Unsure

- If something is **blocking** (e.g. missing critical context or conflicting requirements), ask **one** clear clarifying question.
- Otherwise, make a **reasonable default choice**, document it briefly, and proceed.
- Prefer conservative, backwards‑compatible changes when behavior is ambiguous.

---

## Tailwind Guidelines

- Write Tailwind like a senior dev cleaning up over‑engineered UIs.
- Assume sensible defaults; do **not** add responsive variants unless specific breakpoint behavior is described or clearly implied by surrounding code.
- Prefer fewer utilities that do more:
  - Use `space-y-*`, `gap-*`, `divide-*`, and layout utilities instead of manually adding margins/padding to each child.
- If you are about to write **more than 5–6 utilities** on one element, reconsider the markup or introduce a wrapper.
- Consolidate classes; avoid duplicates and conflicting utilities.
- When patterns repeat, suggest **reusable abstractions**:
  - Variants
  - Utility classes
  - Reusable components that follow existing design tokens.

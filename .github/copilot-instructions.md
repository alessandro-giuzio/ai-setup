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

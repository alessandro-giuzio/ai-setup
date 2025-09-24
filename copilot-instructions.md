# Copilot Instructions (Project Style Guide)

## Goals
- Help me ship fast with **Astro + Vue 3 `<script setup lang="ts">` + TailwindCSS + Supabase**.
- Prefer **small, safe, diff-style edits** over big rewrites.

## Stack & Conventions
- **Language:** TypeScript everywhere; no `any`.

- **Vue:** Always use `<script setup lang="ts">` followed by a `<template>`  Composition API, emits/props typed.
-   Script block comes **first**, template comes **after**.
  -  ✅ Example  Vue 3 Component 

```vue
<script setup lang="ts">
import { ref } from "vue"

const count = ref(0)
function increment() {
  count.value++
}
</script>

<template>
  <button
    class="px-4 py-2 bg-blue-500 text-white rounded"
    @click="increment"
  >
    Count is: {{ count }}
  </button>
</template>
<style scoped>
button {
  background-color: #42b983;
  color: white;
  padding: 8px 16px;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}
</style>
```
- **Astro:** Vue islands for interactivity; keep pages lean.
- ✅ Example 2: Astro Component with Props


```astro
---
const { title, description } = Astro.props
---

<section>
  <h2>{title}</h2>
  <p>{description}</p>
</section>

<style>
h2 {
  color: #42b983;
}

p {
  font-size: 16px;
}
</style>
```

- **Styling:** Tailwind utilities with tokens from `src/styles/global.css`. No inline styles.
- **Data/Auth:** Supabase JS client. Assume RLS on. Use typed queries and narrow selects.
- **Testing:** Vitest + Vue Test Utils when asked.

## Output Rules
- Be **concise**: bullets over prose, max one short paragraph before code.
- Prefer **patches/diffs** or **minimal code blocks**. Explain risky changes in 1–2 bullets.
- If assumptions are needed, **state them in one line**, then proceed.

## Accessibility & UX
- Label form controls, manage focus, and provide keyboard support.
- Use semantic HTML; avoid div soup.

## Performance
- Avoid heavy deps; propose lightweight first.
- Tree-shakable imports; defer non-critical JS.

## Tailwind
- Consolidate classes; avoid duplicates.
- Suggest reusable patterns (variants/util classes) based on existing tokens.

## Supabase
- Centralize client; avoid scattering queries.
- Handle loading/error states explicitly.
- Never log secrets; never suggest committing `.env`.

## When Unsure
- Ask one clarifying question **only if blocking**; otherwise, make a reasonable default and continue.

## Examples Preference
- Show **final version first**, then a **very short** rationale.
- When refactoring, show **before/after** or a unified diff.

## File Ops
- When adding files, list the **path + filename** and a minimal stub.
- Keep paths consistent with: `src/components`, `src/pages`, `src/styles/global.css`, `src/composables`, `tests`.

## 🚫 Constraints
- Do not use legacy Vue options API.
- Avoid inline styles unless necessary.
- Keep function and component names **descriptive** and **camelCase**.
- Avoid hardcoded values; use props or config instead.
- Code should follow **DRY (Don't Repeat Yourself)** and **KISS (Keep It Simple, Stupid)** principles.
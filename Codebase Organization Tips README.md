
# Project Name

## 🚀 Tech Stack
- 🌟 **Astro** – Static site generator.
- 🔥 **Vue.js** – JavaScript framework for building UI.
- 🎨 **TailwindCSS** – Utility-first CSS framework.
- 🧱 **ShadCN** – Component library for building consistent UIs.
- 🌍 **Supabase** – Backend-as-a-service (auth, database, etc.).

## 📦 Installation
Make sure you have **Node.js** and **pnpm** installed.

```bash
pnpm install
```

## 🚀 Running the Project
Start the development server:
```bash
pnpm dev
```

Build the project:
```bash
pnpm build
```

## 🏗️ Project Structure
```
/src
├── components      # UI components (e.g., Button, Card)
├── layouts         # Layout components (e.g., MainLayout)
├── pages           # Route components (e.g., Home, About)
├── styles          # Global styles (e.g., Tailwind config)
├── hooks           # Custom hooks (e.g., useAuth)
├── services        # API calls (e.g., fetch from Supabase)
├── utils           # Helper functions
└── types           # TypeScript types
```

## 🌐 Environment Variables
Create a `.env` file in the root directory:
```
SUPABASE_URL=
SUPABASE_KEY=
NEXT_PUBLIC_SITE_URL=
```

## ✅ Git Best Practices
- Use clear commit messages:
    - ✅ `feat: added new login component`
    - ✅ `fix: corrected routing error`
- Create branches for features and fixes.

## 🎯 To-Do
- [ ] Connect to Supabase
- [ ] Add authentication
- [ ] Set up Tailwind components with ShadCN

---

## 💡 Notes
This project uses the following:
- TypeScript for type safety
- `@types/vue` for better developer experience
- Auto-imports enabled for Vue components


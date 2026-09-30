---
status: pending
title: Minimal "Hello, World!" App
---

1. Scaffold project config at the repo root.
   - Create `package.json` (name `hello-world`, private, ESM, npm scripts: `dev`, `build`, `preview`) with dependencies: react, react-dom, @tanstack/react-router; devDependencies: vite, @vitejs/plugin-react, @tanstack/router-plugin, typescript, tailwindcss, @tailwindcss/vite.
   - Create `vite.config.ts` registering `@tanstack/router-plugin/vite` (before the React plugin) and `@tailwindcss/vite`.
   - Create `tsconfig.json` (strict, bundler moduleResolution, jsx: react-jsx) and `index.html` mounting `<div id="root">` and loading `/src/main.tsx`.
   - Expected outcome: `npm install` then `npm run dev` serves a blank page without errors.

2. Add the single global stylesheet.
   - Create `src/styles/global.css` whose first line is exactly `@import "tailwindcss";` — no other global rules needed beyond Tailwind defaults.
   - Expected outcome: Tailwind utilities are available app-wide.

3. Create the app entry point.
   - Create `src/main.tsx`: import `src/styles/global.css` once, create the TanStack Router instance from the generated route tree, and render `<RouterProvider>` into `#root` via `createRoot`.
   - Expected outcome: the app boots and the router plugin generates `src/routeTree.gen.ts` (never hand-edited).

4. Create the root layout route.
   - Create `src/routes/__root.tsx` with `createRootRoute`, rendering `<Outlet />` inside a full-viewport wrapper (`min-h-screen`) that centers its children both axes (flex, items-center, justify-center) with a plain white background and default text color.
   - Expected outcome: every route renders centered on a clean white page.

5. Create the home route with the "Hello, World!" message.
   - Create `src/routes/index.tsx` (path `/`) rendering a single `<h1>` with the text `Hello, World!`, styled minimally: large but restrained type (e.g. `text-4xl md:text-5xl font-semibold tracking-tight text-gray-900`) surrounded by generous whitespace; no buttons, inputs, images, or animations.
   - Expected outcome: visiting `/` shows only a centered "Hello, World!" message with a clean, minimal look.

6. Verify the result.
   - Run the dev server, confirm `/` renders the centered message with no console errors, and confirm the production build (`npm run build`) succeeds.
   - Expected outcome: working tiny app matching the requirements exactly — one message, nothing else.

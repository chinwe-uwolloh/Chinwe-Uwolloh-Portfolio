# Copilot Instructions

## Project Overview

This is the personal portfolio website of Chinwe Uwolloh, showcasing work across AI, product, systems, and technical project leadership. The live site is deployed at [chinwes-portfolio.com](https://chinwes-portfolio.com/) via GitHub Pages.

## Tech Stack

- **Framework**: React 18 with TypeScript
- **Build tool**: Vite (dev server on port 8080)
- **Styling**: Tailwind CSS with custom design tokens (CSS variables)
- **Component library**: shadcn/ui (built on Radix UI primitives)
- **Routing**: react-router-dom v6
- **Data fetching**: TanStack Query (React Query v5)
- **Forms**: react-hook-form + zod validation
- **Backend/DB**: Supabase
- **Animation**: Framer Motion, GSAP, React Three Fiber + Drei (3D)
- **Fonts**: Space Grotesk (`font-space`), JetBrains Mono (`font-mono`)

## Project Structure

```
src/
  components/       # Reusable UI components (Hero, Navigation, Projects, etc.)
    ui/             # shadcn/ui base components
  pages/            # Route-level page components (Index, ProjectDetail, NotFound)
  data/             # Static data files (projects.ts, experiences.ts)
  hooks/            # Custom React hooks
  integrations/     # Third-party integrations (Supabase client, etc.)
  lib/              # Utility functions (cn helper, etc.)
.github/
  workflows/        # CI/CD: deploy-pages.yml deploys to GitHub Pages on push to main
```

## Path Aliases

Use `@/` to import from the `src/` directory root:

```ts
import { Button } from "@/components/ui/button";
import { projects } from "@/data/projects";
```

## Common Commands

```bash
npm install --legacy-peer-deps  # Required: some packages (e.g. react-day-picker, framer-motion-3d) have peer dep constraints that conflict with React 18 under npm v7+ strict mode
npm run dev                     # Start dev server at http://localhost:8080
npm run build                   # Production build to dist/
npm run lint                    # Run ESLint
npm run preview                 # Preview production build locally
```

## Coding Conventions

- **TypeScript**: Strict mode; always type props and data structures explicitly.
- **Components**: Functional components with named exports. One component per file, matching the filename.
- **Styling**: Use Tailwind CSS utility classes. Use the `cn()` helper from `@/lib/utils` to merge conditional classes.
- **shadcn/ui**: Prefer shadcn/ui components from `@/components/ui/` over raw HTML elements for interactive UI (buttons, dialogs, forms, etc.).
- **Animations**: Use Framer Motion for page/element transitions; GSAP for timeline-based effects; React Three Fiber for 3D scenes.
- **Data**: Static content (projects, experiences) lives in `src/data/`. Keep components free of hardcoded data.
- **No test suite**: There are no automated tests in this project. Manual verification and linting are the primary quality gates.

## Deployment

Merging to `main` triggers `.github/workflows/deploy-pages.yml`, which builds the site and deploys the `dist/` folder to GitHub Pages. The site is served from the root path (`base: "/"`).

## Environment Variables

Supabase credentials and any other secrets are expected as environment variables (not committed to the repo). See `src/integrations/` for usage patterns.

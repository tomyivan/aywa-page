# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Commands

| Command | Action |
| :--- | :--- |
| `pnpm dev` | Start dev server at `localhost:4321` |
| `pnpm build` | Build production site to `./dist/` |
| `pnpm preview` | Preview the production build locally |
| `pnpm astro check` | Run TypeScript diagnostics |

## Development

Use background mode when starting the dev server so the terminal stays free:

```
pnpm astro dev --background
```

Manage it with `pnpm astro dev stop`, `pnpm astro dev status`, and `pnpm astro dev logs`.

## Architecture

This is an **Astro + Tailwind CSS v4** site for the Aywa product, built from the Astro "basics" starter. Package manager is **pnpm**.

**Styling:** Tailwind v4 is wired in via the `@tailwindcss/vite` Vite plugin (configured in `astro.config.mjs`). Tailwind is activated globally through `src/styles/global.css` with `@import "tailwindcss"` — there is no `tailwind.config.*` file; all customization goes in that CSS file using `@theme`. Components mix Tailwind utility classes (in `Navbar.astro`) with scoped `<style>` blocks (in `Welcome.astro`).

**Page composition:** `src/pages/index.astro` composes the page by nesting `<Navbar />` and `<Welcome />` inside `<Layout />`. Adding a new page means creating a new `.astro` file under `src/pages/` — Astro uses file-based routing.

**Layout:** `src/layouts/Layout.astro` is the base HTML shell. It renders children via a single `<slot />`. The `<title>` and meta tags are hardcoded here and should be updated for the product.

**Components:** `src/components/Navbar.astro` has the product navigation (Spanish labels: Inicio, Características, Cómo Funciona, Descargar) and imports `src/assets/logo.png`. `src/components/Welcome.astro` is still the default Astro starter placeholder — it is the main content area to replace with actual product content.

**Assets:** `src/assets/` holds logo files (`logo.png`, `logo.svg`) and the placeholder `astro.svg` / `background.svg` from the starter template. Static files that don't need processing (like `favicon.ico`) go in `public/`.

## Documentation

- [Routing & pages](https://docs.astro.build/en/guides/routing/)
- [Astro components](https://docs.astro.build/en/basics/astro-components/)
- [Tailwind v4 in Astro](https://docs.astro.build/en/guides/styling/)
- [Content collections](https://docs.astro.build/en/guides/content-collections/)

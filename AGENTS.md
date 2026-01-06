# Repository Guidelines

## Project Structure
- `src/pages/`: route-backed pages (`.astro`, `.md(x)`, and endpoint files like `rss.xml.js`).
- `src/components/`: reusable UI components (`*.astro`).
- `src/layouts/`: shared page layouts (e.g., blog post layout).
- `src/content/`: content collections (blog posts live in `src/content/blog/`).
- `src/styles/`: global styles (see `src/styles/global.css`).
- `src/assets/`: source-controlled images used by the site.
- `public/`: static files served as-is (e.g., `public/favicon.svg`, `public/fonts/`).

## Build, Test, and Development Commands
This repo uses Bun (see `bun.lock`).
- `bun install`: install dependencies.
- `bun dev`: start the dev server (default `http://localhost:4321`).
- `bun build`: build the production site to `dist/`.
- `bun preview`: serve the production build locally.
- `bun astro ...`: run Astro CLI commands (e.g., `bun astro add`).

## Coding Style & Naming Conventions
- Indentation: follow existing files (tabs are used in `.astro` and config files).
- TypeScript: strict config via `tsconfig.json` (`astro/tsconfigs/strict` + `strictNullChecks`).
- Naming: use PascalCase for components (`src/components/HeaderLink.astro`) and kebab-case for content files in `src/content/blog/`.
- Formatting/linting: no formatter/linter is configured; keep changes small and consistent with nearby code.

## Testing Guidelines
- No dedicated test framework is set up yet. Validate changes by running `bun build` and spot-checking routes via `bun preview`.
- Content is schema-validated via `src/content.config.ts`; keep blog frontmatter aligned with the `blog` collection schema.

## Commit & Pull Request Guidelines
- Commits in history are short, imperative summaries (e.g., “Initial commit…”, “update package name…”). Keep subjects concise and focused.
- PRs: include a clear description, link relevant issues, and attach screenshots for UI changes (especially pages/layouts).
- Releases: pushing a `v*` tag triggers `.github/workflows/docker-publish.yml` to publish a Docker image to GHCR.

## Configuration Notes
- Update `site` in `astro.config.mjs` from `https://example.com` to the real production URL to ensure correct sitemap/canonical URLs.

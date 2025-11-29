# Astro Biome Project Context

## Project Overview
This is an **Astro** web application project that utilizes **Biome** for high-performance linting and formatting. The project is configured for a strict TypeScript environment and manages dependencies using **pnpm**.

The primary documentation (`README.md`) is written in Japanese.

## Tech Stack
- **Framework:** [Astro](https://astro.build/)
- **Language:** TypeScript / JavaScript
- **Linter & Formatter:** [Biome](https://biomejs.dev/)
- **Package Manager:** pnpm

## Development Workflow & Commands

All commands should be executed using `pnpm`.

| Command | Description |
| :--- | :--- |
| `pnpm dev` | Starts the local development server (default: `http://localhost:4321`). |
| `pnpm build` | Builds the project for production. |
| `pnpm preview` | Previews the production build locally. |
| `pnpm check` | Runs `astro check` for type checking. |
| `pnpm lint` | Runs `biome lint --write` to check and fix linting issues. |
| `pnpm format` | Runs `biome format --write` to format code. |

## Configuration Files

- **`astro.config.mjs`**: Main Astro configuration file. Currently uses default settings.
- **`biome.json`**: Configuration for Biome linter and formatter.
  - **Formatting:** 2 spaces indentation, single quotes for JS, double quotes for JSX, no semicolons where possible (`asNeeded`).
  - **Linting:** Recommended rules enabled.
- **`tsconfig.json`**: TypeScript configuration, extending `astro/tsconfigs/strict`.
- **`package.json`**: Project dependencies and scripts.

## Directory Structure

```
/
├── .astro/          # Astro generated types and cache
├── public/          # Static assets served at root (e.g., favicon)
├── src/
│   ├── assets/      # Source assets (images, svgs)
│   ├── components/  # Reusable Astro components
│   ├── layouts/     # Page layouts
│   └── pages/       # File-based routing (index.astro)
├── astro.config.mjs
├── biome.json
├── package.json
└── tsconfig.json
```

## Development Conventions

- **Code Style:** Strictly adhere to the rules defined in `biome.json`.
  - Run `pnpm format` before committing to ensure consistency.
  - Use **Single Quotes** for JavaScript strings.
  - Use **Double Quotes** for JSX attributes.
  - **No Semicolons** unless required.
- **Type Safety:** The project uses strict TypeScript settings. Ensure all new code is properly typed.
- **Component Structure:** Follow the Astro standard of placing reusable UI in `src/components` and page roots in `src/pages`.

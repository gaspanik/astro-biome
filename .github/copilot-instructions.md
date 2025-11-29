# Copilot Instructions for astro-biome

## Project Overview
Astro 5.x web application using **Biome** (not ESLint/Prettier) for linting and formatting. TypeScript strict mode enabled. Documentation and codebase comments are in Japanese.

## Critical Tooling

### Package Manager: pnpm ONLY
- Always use `pnpm` commands, never `npm` or `yarn`
- Workspace configured in `pnpm-workspace.yaml` with selective dependency builds (esbuild, sharp)

### Code Quality: Biome (NOT ESLint/Prettier)
- **Never suggest ESLint or Prettier** - this project uses Biome exclusively
- Config: `biome.json` with strict formatting rules
- Always run `pnpm lint` and `pnpm format` before suggesting code is complete

### Task Runner: mise (Optional)
- `mise.toml` defines tasks like `mise run astro:dev`, `mise run biome:format`
- Several tasks have confirmation prompts (build, format, lint)
- Mise manages Node.js version (24) - respect this when suggesting environment setup

## Code Style Rules (from biome.json)

JavaScript/TypeScript:
```typescript
// Single quotes, no semicolons (asNeeded), trailing commas
const example = {
  name: 'value',
  items: [1, 2, 3],
}
```

JSX/TSX:
```tsx
// Double quotes in JSX, arrow parentheses always
<Component attr="value" />
const Component = (props) => <div>{props.content}</div>
```

HTML (in .astro files):
```html
<!-- Self-closing void elements always, indentScriptAndStyle: false -->
<meta charset="UTF-8" />
<img src={logo.src} alt="Logo" />
```

Line width: 80 characters, 2 space indentation, LF line endings

## Astro-Specific Conventions

### File Structure
- `src/pages/` - File-based routing (e.g., `index.astro`)
- `src/layouts/` - Page layouts (e.g., `Layout.astro` base template)
- `src/components/` - Reusable components (e.g., `Welcome.astro`)
- `src/assets/` - Source assets imported in components (use `.src` property)
- `public/` - Static files served at root (e.g., `favicon.svg`)

### Component Patterns
```astro
---
// Frontmatter: TypeScript logic, imports
import Layout from '../layouts/Layout.astro'
import logo from '../assets/astro.svg'
---
<!-- Template: HTML with islands -->
<Layout>
  <img src={logo.src} alt="Logo" />
</Layout>
```

Assets from `src/assets/` must use `.src` property: `<img src={astroLogo.src} />`

## Development Workflow

1. **Start dev server**: `pnpm dev` (http://localhost:4321)
2. **Type checking**: `pnpm check` (runs `astro check`)
3. **Before commit**: `pnpm lint` and `pnpm format`
4. **Build**: `pnpm build` → `dist/` directory
5. **Preview build**: `pnpm preview` (depends on build)

## TypeScript Configuration
- Extends `astro/tsconfigs/strict` - enforce strict type checking
- Includes `.astro/types.d.ts` for Astro-generated types
- When suggesting code, maintain strict TypeScript compatibility

## Key Files to Reference
- `biome.json` - Source of truth for all formatting/linting rules
- `astro.config.mjs` - Currently minimal, but check before suggesting integrations
- `mise.toml` - Task definitions with confirmation prompts
- `GEMINI.md` - English project context (mirrors README.md in Japanese)

## Common Pitfalls to Avoid
1. Don't suggest ESLint/Prettier configurations
2. Don't use `npm`/`yarn` commands
3. Don't add semicolons where Biome omits them (`asNeeded` mode)
4. Don't suggest formatOnSave configs - Biome handles this
5. Don't forget `.src` when accessing imported assets from `src/assets/`
6. Don't ignore the 80 character line width limit

# AGENTS.md — ryuk_port

Simple Astro CV site forked from [astro-cv-esquelete](https://github.com/mmouzo/astro-cv-esquelete), deployed on Vercel.

## Quick start

```sh
nvm use           # node 22 required (.nvmrc)
npm install
npm run dev       # dev server at localhost:4321
npm run build     # output → dist/
npm run preview   # preview production build
```

No tests, lint, or typecheck configured. `npm run build` is the only verification step.

## Content model

All content lives in Markdown under `src/pages/` by section directory:
`about/`, `works/`, `studies/`, `certificates/`, `contact/`. Each directory is auto-discovered by `import.meta.glob` in `src/components/Container.astro:23-28`.

Frontmatter drives rendering. The standard keys found across sections: `title`, `date`, `tags`, `url`, `org`, `location`, `institute`, `url_name`, `icon`. See `MarkdownInstance` type in `Container.astro:8-21`.

The `about/about.md` frontmatter (`name`, `designation`, `location`, `pronouns`, `website`) is imported in multiple components as the single source of personal metadata.

**Projects** and **Blogs** markdown files exist but their `<AccordionLayout>` entries in `Container.astro:73-90` and `108-124` are HTML-commented out. Uncomment to restore.

## Key config

- **SSR mode** (`output: "server"` in `astro.config.mjs`) — uses Vercel adapter
- **daisyUI v4** (not v5) with two custom themes (`lofi`/`black`), toggled via `data-toggle-theme` in `index.astro`
- **Tailwind CSS v3**, daisyUI as Tailwind plugin in `tailwind.config.mjs`

## Deployment

Configured for Vercel (`@astrojs/vercel`, `vercel.json`). Build command: `npm run build`.

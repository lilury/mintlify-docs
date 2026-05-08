# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this repo is

A documentation site built on [Mintlify](https://mintlify.com). All pages are MDX files. Configuration lives in `docs.json`. The site is deployed automatically when changes are pushed to the default branch via the Mintlify GitHub app.

## Development commands

```bash
# Install CLI (once)
npm i -g mint

# Local preview at http://localhost:3000
mint dev

# Check for broken links
mint broken-links

# Update CLI to latest
mint update
```

## Architecture

- **`docs.json`** — single source of truth for site config: theme, colors, logo, navigation tabs/groups, navbar, footer, contextual menu options. Every page must be listed here under `navigation` to appear in the site.
- **`.mdx` files** — pages, each with YAML frontmatter (`title`, `description`, optional `icon`). MDX allows JSX components inline.
- **`snippets/`** — shared content fragments. Files here are **not** rendered as standalone pages; import them into pages with `import Foo from '/snippets/foo.mdx'`. Supports content snippets, variable exports, and arrow-function components (not `function` keyword).
- **`api-reference/openapi.json`** — OpenAPI spec used to auto-generate API reference pages.
- **`images/`**, **`logo/`** — static assets referenced from MDX and `docs.json`.

## Adding a page

1. Create the `.mdx` file at the desired path.
2. Add that path (without extension) to `docs.json` under the appropriate `navigation.tabs[].groups[].pages` array.
3. Missing from `docs.json` = page won't appear in nav (but won't 404 if navigated to directly).

## Reusable snippets

- Place snippet files in `snippets/`.
- Import with root-relative (`/snippets/foo.mdx`) or relative (`../snippets/foo.mdx`) paths.
- Arrow-function components only — `export const Foo = ({ prop }) => <p>{prop}</p>`. Plain `function` keyword is not supported inside snippet files.
- Inside arrow function bodies use plain HTML tags, not MDX syntax.

## Draft content

Files matching `drafts/` or `*.draft.mdx` are ignored by Mintlify (see `.mintignore`).

## Writing style

- Active voice, second person ("you").
- Sentence case for headings.
- Bold for UI elements: **Settings**.
- Code formatting for file names, commands, paths, and inline code references.
- One idea per sentence; lead with what the user wants to accomplish.

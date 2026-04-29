# Claude Instructions for scoutaloud

## Project

Zola static site. Templates use Tera (Zola's templating engine). Styles live in `static/base.css`. Content is Markdown in `content/`.

## Principles

- **Modern CSS over JS**: reach for CSS (custom properties, container queries, `:has()`, `@starting-style`, scroll-driven animations, anchor positioning) before writing any JavaScript.
- **Avoid JS where possible**: if a behaviour can be achieved in pure CSS or via semantic HTML (e.g. `<details>`, `<dialog>`, `<input type="checkbox">` toggle tricks), do that instead.
- **Semantic HTML**: use the most meaningful element for the job — `<nav>`, `<main>`, `<article>`, `<aside>`, `<section>`, `<header>`, `<footer>`, `<time>`, `<figure>`, `<address>`, etc. Avoid `<div>` and `<span>` when a semantic element fits.
- **BEM class names**: Block__Element--Modifier convention. Block names should be short and descriptive (e.g. `post-card`, `site-header`). Don't add BEM classes to elements that don't need them — let semantic HTML carry the meaning where possible.
- **Accessibility**: correct ARIA roles only when native semantics are insufficient. Always include alt text, label form controls, ensure focus is visible.

## Zola specifics

- Use Context7 MCP to look up Zola docs when uncertain about template syntax, config options, or built-in functions.
- Templates: Tera syntax — `{{ variable }}`, `{% block %}`, `{% for %}`, `{% if %}`. Filters: `| safe`, `| truncate`, `| date`.
- Front matter is TOML (between `+++` delimiters).
- Taxonomy, section, and page variables follow Zola's data model — check the docs rather than guessing.

## What to avoid

- Don't add JavaScript for things CSS handles: smooth scroll (`scroll-behavior: smooth`), sticky headers (`position: sticky`), simple show/hide (`:checked` + sibling selector or `@starting-style` transitions), dropdown menus.
- Don't use utility-class frameworks (Tailwind, Bootstrap) — this project uses hand-written CSS.
- Don't add `<div class="wrapper">` soup. Flatten the markup and use CSS layout directly.
- Don't introduce build tools, bundlers, or npm dependencies.

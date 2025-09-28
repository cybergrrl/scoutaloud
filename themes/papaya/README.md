# Papaya Theme (Vendored)

Papaya: A clean [Zola](https://getzola.org) theme for blogging and projects, forked from [Anpu](https://github.com/zbrox/anpu-zola-theme).

This folder contains the Papaya Zola theme, vendored directly into the repository.

## Notes

- **Vendored, not a submodule:** Only the files actually needed by the site are included:
  - `templates/` – HTML templates used by the site
  - `sass/` or `css/` – stylesheets
  - `static/` – assets referenced by templates
  - `theme.toml` – theme metadata
  - `LICENSE` - papaya license document

- **Removed unnecessary/demo files:**
  - `pics/`, `.github/`, example markdown, generated `public/`, `static/processed_images/`

- The theme can be updated manually by copying new files from a fresh Papaya release.

- There is **no nested `.git`**; this folder is fully tracked by the main repository.

### Editing theme templates

- For normal templates, i copied the theme's template into my template folder in root and edited it there.
- This does not work for macros which would have to be edited in place if/where necessary. 
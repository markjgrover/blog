# Mark Grover's Blog

Personal blog built with [Hugo](https://gohugo.io/) and the [Blowfish](https://blowfish.page/) theme, deployed via GitHub Pages.

🌐 **Live site:** [markjgrover.github.io/blog](https://markjgrover.github.io/blog/)

---

## Tech Stack

- **Static site generator:** Hugo v0.141.0 (extended)
- **Theme:** Blowfish
- **Hosting:** GitHub Pages
- **CI/CD:** GitHub Actions

---

## Project Structure

```
blog/
├── assets/          # Images, logos, and background files
├── config/_default/ # Site configuration files
│   ├── hugo.toml        # Main Hugo config
│   ├── params.toml      # Blowfish theme parameters
│   ├── languages.en.toml # Language and author settings
│   ├── menus.en.toml    # Navigation menu
│   └── markup.toml      # Markdown rendering settings
├── content/posts/   # Blog posts (each in own folder)
├── static/          # Favicons and static assets
├── themes/blowfish/ # Blowfish theme (git submodule)
└── .github/workflows/hugo.yml  # GitHub Actions deployment
```

---

## Local Development

### Prerequisites
- [Hugo Extended](https://gohugo.io/installation/) v0.141.0+
- [Git](https://git-scm.com/)

### Run locally

```powershell
git clone https://github.com/markjgrover/blog.git
cd blog
hugo server
```

Site will be available at `http://localhost:1313/blog/`

---

## Writing a New Post

Create a new folder under `content/posts/` with an `index.md` file:

```
content/posts/my-new-post/
├── index.md
└── featured.png   # optional thumbnail
```

Front matter template:

```yaml
---
title: "My Post Title"
date: 2026-01-01
draft: false
summary: "A short description of the post"
tags: ["AI", "Learning"]
showTableOfContents: false
---
```

---

## Deployment

Every push to `main` triggers a GitHub Actions workflow that:
1. Checks out the repo including the Blowfish submodule
2. Patches the Blowfish theme for Hugo v0.141 compatibility
3. Builds the site with `hugo --minify`
4. Deploys to GitHub Pages

---

## Theme Notes

This repo uses a patched version of Blowfish to fix compatibility issues with Hugo v0.141+. The patches are applied automatically in the GitHub Actions workflow (`hugo.yml`) and fix:

- `site.Language.Locale` → `site.Language.Lang`
- `hugo.Data.authors` → `site.Data.authors`

---

## Configuration

Key settings are in `config/_default/`:

| File | Purpose |
|------|---------|
| `hugo.toml` | Base URL, pagination, taxonomies |
| `params.toml` | Theme layout, colors, article display |
| `languages.en.toml` | Author name, bio, profile image, logo |
| `menus.en.toml` | Navigation links |

---

## License

Content © 2026 Mark J Grover. All rights reserved.

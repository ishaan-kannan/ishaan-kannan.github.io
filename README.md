# ishaan-kannan.github.io

Academic homepage for Ishaan Kannan.

## Replace the placeholders

- `assets/header-placeholder.svg` → replace with a wide header image. If you use a JPG, rename it `header.jpg` and change the `background-image` URL in `assets/style.css`.
- `assets/profile-placeholder.svg` → replace with your square-ish profile photo. Rename to `profile.jpg` and update the `<img>` in `index.html`.
- `assets/Ishaan_Kannan_CV.pdf` → upload your CV using exactly this filename (or change the links).
- Replace email, Scholar, arXiv, publication, bio, and Recent placeholders in `index.html`.

## Blog

GitHub Pages will render Markdown automatically with Jekyll.

To add a post, create a file like:

`_posts/2026-08-17-post-title.md`

with:

```yaml
---
layout: post
title: "Post title"
description: "Optional one-line description"
---
```

Then write ordinary Markdown below the front matter. The blog index automatically lists posts.

## Deployment

Repository name: `ishaan-kannan.github.io`

Push the contents of this folder to the repository root and enable GitHub Pages from the `main` branch in Settings → Pages.

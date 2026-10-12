# Classical Mechanics with Geometric Algebra

A web-first book draft written in MyST Markdown.

## Preview locally

With MyST installed, run:

```sh
myst start
```

## Build the static website

```sh
myst build --html
```

The generated website is written to `_build/html/`.

## Publish with GitHub Pages

This project is intended to live in a public GitHub repository. The workflow in `.github/workflows/pages.yml` builds the book for pull requests and deploys it to GitHub Pages whenever a change reaches `main`. You can also start a build manually from the **Actions** tab.

After creating the repository, enable **Settings → Pages → Build and deployment → GitHub Actions** once. The workflow reads the Pages base path automatically, so links work for both project sites and user or organization sites. The source repository and published website are public.

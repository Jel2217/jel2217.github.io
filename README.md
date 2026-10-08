# jmansor.com

My portfolio site. It's a plain Jekyll site (no theme), served by a Cloudflare Worker as static files. Every push to `main` builds and deploys to jmansor.com.

Cloudflare build settings: build command `bundle exec jekyll build`, deploy command `npx wrangler deploy`. Wrangler reads `wrangler.jsonc`, which points it at `_site`. The Ruby version comes from `.ruby-version`.

The design is styled like a schematic drawing sheet: the home page is sheet 1, each project is a hierarchical sheet after it, and the footer is the drawing title block.

## Where things live

| To change | Edit |
| --- | --- |
| A project page | `_projects/<name>.md` |
| The "Right now" list | `_data/now.yml` |
| Work experience | `_data/experience.yml` |
| Leadership and music | `_data/leadership.yml` |
| Smaller projects | `_data/other_projects.yml` |
| Skills | `_data/skills.yml` |
| Intro, About and Education text | `index.html` |
| Email, GitHub and LinkedIn | `_config.yml` |
| Styles | `assets/css/sheet.css` |

## Adding a project

Make a new file in `_projects/`. The file name becomes the URL, so `_projects/my-thing.md` ends up at `/projects/my-thing/`.

```yaml
---
title: My thing
description: One or two sentences for the project card and the top of the page.
order: 7                 # position on the home page, and its sheet number
when: 2026
context: Personal project
role: What I did         # optional
status: In progress      # optional
tags: [STM32, Altium]
image: /assets/img/projects/my-thing.jpg   # optional main photo, shown at the top
image_alt: Describe the photo
image_caption: A short caption   # optional
gallery:                 # optional extra photos, shown under the write-up
  - src: /assets/img/projects/my-thing-2.jpg
    alt: Describe the photo
    caption: A short caption
parts:                   # optional "Key parts" table
  - part: STM32
    role: Microcontroller
---

The write-up goes here, in Markdown.
```

Photos go in `assets/img/projects/`.

## Running it locally

You need Ruby (the version in `.ruby-version`) and Bundler.

```sh
bundle install
bundle exec jekyll serve
```

Then open http://localhost:4000.

# Blastsoft Studios Website

Static site for [blastsoftstudios.com](https://blastsoftstudios.com), built with Jekyll and hosted on GitHub Pages.
Replaces the old Django site ([blastsoftstudios-www](https://github.com/blastsoftstudios/blastsoftstudios-www)).

Pushing to `master` publishes the site.

## Editing content

| What | Where |
|------|-------|
| Downloads | `_downloads/<url-key>.html` — front matter holds the card data, the body is the description HTML |
| Web apps (nav dropdown) | `_webapps/<url-key>.html` — `layout: webapp` embeds `link` in an iframe; `layout: default` for a custom page |
| Home page carousel | `index.html` |
| About / Downloads list | `about.html` / `downloads.html` |
| Privacy policy / terms | `_includes/legal/privacy.html` / `_includes/legal/terms.html` (bump `last_updated` in `legal.html`) |
| Shared header, nav, footer | `_layouts/default.html` |
| Ad block | `_includes/ad.html` |
| CSS, JS, images | `static/` |

### Adding a download

Create `_downloads/my-thing.html` (served at `/downloads/my-thing`):

```html
---
layout: download
name: "My Thing"
title: "My Thing"
order: 0                 # lower sorts first on /downloads/
updated: 2026-11-19
image_link: "https://cdn.blastsoftstudios.com/images/my-thing.png"
short_description: "One line for the card and link previews."
downloadable: true
link: "https://cdn.blastsoftstudios.com/downloads/my-thing.zip"
og_title: "Blastsoft Studios - My Thing"
og_image: "https://cdn.blastsoftstudios.com/images/my-thing.png"
og_description: "One line for the card and link previews."
# alternate_side: |      # optional HTML to show instead of the image
#   <p>...</p>
---
<p>Description HTML.</p>
```

## Local preview

```sh
docker run --rm -it -p 4000:4000 -v "$PWD":/site -w /site ruby:3.3 \
  sh -c 'bundle install && bundle exec jekyll serve --host 0.0.0.0'
```

Then open http://localhost:4000.

# Francisca Vasconcelos — minimalist Jekyll website

This is a lightweight, self-contained replacement for the al-folio-based site. It keeps the academic structure of the current website while avoiding theme updates, Bootstrap, external fonts, and large plugin stacks.

## What is included

- Home page with bio, portrait, email, recent news, major fellowships, compact affiliations, and selected publications.
- Dedicated pages for publications and news; teaching and non-academic pages are included but hidden by default.
- Local copies of the current profile photo, CV PDF, and publication thumbnails.
- Content stored in `_data/*.yml` so most updates do not require editing HTML.
- A small amount of Liquid templating in `_includes/` and `_layouts/`.
- A GitHub Actions workflow that builds Jekyll and deploys to GitHub Pages.

## Editing content

Most edits happen in these files:

```text
_data/profile.yml       # name, email, links, bio
_data/news.yml          # timeline items
_data/publications.yml  # publication cards, venues, links, selected flag
_data/teaching.yml      # courses, outreach, talks
_data/personal.yml      # athletics/art/other blurbs and images
```

Pages live at the top level:

```text
index.md
publications.html
news.md
teaching.md
beyond.md
```

The publications page is intentionally written as HTML rather than Markdown. This avoids Markdown treating indented Liquid/HTML blocks as code snippets.

### Re-enabling hidden pages

The Teaching and Beyond pages are currently hidden. They are omitted from `_data/navigation.yml`, marked `published: false` in `teaching.md` and `beyond.md`, and excluded in `_config.yml`. To make them public later, remove `teaching.md` and `beyond.md` from `_config.yml`, delete the `published: false` lines, and add their entries back to `_data/navigation.yml`.


Shared HTML snippets live in `_includes/`; the global page shell is `_layouts/default.html`; styling is in `assets/css/main.scss`.

## Adding a news item

Add a new item to the top of `_data/news.yml`:

```yaml
- date: "2026-05-01"
  text: "I gave a talk at ..."
  links:
    - label: "Slides"
      url: "https://..."
```

## Adding a publication

Add a new item to `_data/publications.yml`:

```yaml
- title: "Paper title"
  authors: "Author A and <strong>Francisca Vasconcelos</strong>"
  author_links:              # optional: turns matching author names into underlined links
    - name: "Author A"
      url: "https://author-homepage.example"
  venue: "Conference or journal"
  year: 2026
  sort_date: "2026-05-01"  # controls the reverse-chronological view
  category: "conference"   # preprint, conference, journal, article, thesis
  selected: true            # appears on the home page if true
  image: "/assets/img/publications/example.png"
  presentations:            # optional: talk/conference chips below the main venue
    - name: "QIP 2026"
      url: "https://..."  # optional, but recommended
    - name: "QTML 2024"
      url: "https://..."
  featured:                 # optional: press/news chips below the talks row
    - name: "MIT News"
      url: "https://news.mit.edu/..."
  links:
    - label: "arXiv"
      url: "https://arxiv.org/abs/..."
    - label: "Proceedings"
      url: "https://..."
```

Author links are optional. The `name` field should exactly match the text in the `authors` string, excluding symbols like `*` unless you want the symbol to be part of the clickable text. The URL can be a personal homepage, lab/institution profile, or scholar page.

For conference-proceedings links, use `label: "Proceedings"` rather than publisher names such as DROPS/PMLR/DOI. This keeps the link buttons visually clean and consistent.

Use `presentations` for QIP/QTML/QSim/workshop talks that you want to show after the main publication venue. Use `featured` for press coverage such as MIT News. Both rows use subtle pale-red chips so they do not compete visually with the main non-preprint venue, which remains red, bold, and italic.

## Adding personal photos

Drop photos into `assets/img/personal/` and edit `_data/personal.yml` so the `image` field points to the new file, for example:

```yaml
image: "/assets/img/personal/lacrosse.jpg"
alt: "Francisca playing lacrosse"
```

## Local preview

Install Ruby, then run:

```bash
gem install bundler
bundle install
bundle exec jekyll serve
```

Open the local URL that Jekyll prints, usually `http://127.0.0.1:4000/`.

## Deploying on GitHub Pages

For the existing `franciscavasconcelos.github.io` repository:

1. Back up the current al-folio repo or create a branch.
2. Replace the repository contents with the contents of this folder.
3. Commit and push to `main` or `master`.
4. In GitHub, go to **Settings → Pages**.
5. Set the source to **GitHub Actions**.
6. Push a commit or manually run the `Build and deploy Jekyll site` workflow.

The workflow builds the site with Jekyll and deploys the generated `_site` folder to GitHub Pages.

## Design notes

The design intentionally uses:

- system fonts only;
- local CSS only;
- no theme gem;
- no Bootstrap;
- no external JavaScript;
- a tiny inline script for switching the publications page between category and date views;

This should make the website easy to maintain for years without following upstream template changes.

### Homepage selected publications

The homepage shows every publication in `_data/publications.yml` with `selected: true`, sorted by `sort_date` from newest to oldest. To add or remove a paper from the homepage, edit only the `selected:` field.


### Editing the homepage affiliations section

The homepage affiliations section is data-driven. Edit:

```text
_data/affiliations.yml
```

Each item supports `name`, `url`, `dates`, `role`, and `detail`. To hide the whole section temporarily, remove this line from `index.md`:

```liquid
{% include affiliations.html groups=site.data.affiliations %}
```


### Homepage fellowships and affiliations

Edit `_data/fellowships.yml` to update the compact Major fellowships strip. Edit `_data/affiliations.yml` to update the homepage Affiliations section. The first card is intentionally compact: each school can list associated labs and PIs using `schools: ... labs: ...`. The Experience card uses short dated `items:` entries. To hide these sections, remove the relevant include lines from `index.md`.

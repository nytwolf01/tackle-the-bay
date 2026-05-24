# Tackle the Bay

[tacklethebay.com](https://tacklethebay.com) — a [MkDocs](https://www.mkdocs.org/)
site built with [Material for MkDocs](https://squidfunk.github.io/mkdocs-material/).
It hosts **species guides** for Chesapeake & Mid-Atlantic gamefish and a
**fishing log** (blog) of trip reports.

## Project layout

```
fishing-guide-website/
├── mkdocs.yml              # Site configuration & navigation
├── requirements.txt        # Python dependencies
├── docs/
│   ├── index.md            # Home page
│   ├── guides/             # Species guides
│   │   ├── index.md
│   │   ├── striped-bass.md
│   │   ├── summer-flounder.md
│   │   ├── bluefish.md
│   │   ├── tautog.md
│   │   ├── red-drum.md
│   │   └── smallmouth-bass.md
│   └── blog/               # Fishing log (Material blog plugin)
│       ├── index.md
│       ├── .authors.yml
│       └── posts/
│           └── welcome.md
└── venv/                   # Local virtual environment (git-ignored)
```

## Local development

The project ships with a virtual environment in `venv/`. To run the live-reload
dev server:

```bash
source venv/bin/activate        # activate the venv
mkdocs serve                    # serve at http://127.0.0.1:8000
```

Or without activating:

```bash
./venv/bin/mkdocs serve
```

If you ever need to rebuild the environment from scratch:

```bash
python3 -m venv venv
./venv/bin/pip install -r requirements.txt
```

## Building the static site

```bash
./venv/bin/mkdocs build          # outputs to site/
```

## Adding content

### A new species guide

1. Create `docs/guides/<species>.md`.
2. Add it to the `nav:` list under **Species Guides** in `mkdocs.yml`.

### A new fishing report

1. Create a Markdown file in `docs/blog/posts/`.
2. Add front matter at the top:

   ```yaml
   ---
   date: 2026-06-01
   authors:
     - bronson
   categories:
     - Striped Bass
   ---
   ```

3. Write the report. Put `<!-- more -->` after the intro to control the
   excerpt shown on the blog index.

Categories must come from the `categories_allowed` list in `mkdocs.yml` — add
new ones there first.

# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project overview

Documentation site for the Chr. Michelsen Institute (CMI) — research data management guidance organised around three lifecycle phases: **before**, **during**, and **after**. Built with [Zensical](https://zensical.org/) (static site generator by the creators of Material for MkDocs). Content is Markdown in `docs/`; configuration is TOML in `zensical.toml`.

## Build and development commands

Requires [uv](https://docs.astral.sh/uv/) and Python 3.13+.

```bash
uv sync                    # Install dependencies
uv run zensical serve      # Dev server with live reload
uv run zensical build      # Build static site to site/
```

## Architecture

- `docs/` — Markdown content organised by lifecycle phase (`before/`, `during/`, `after/`), each with an `index.md` overview and topic pages.
- `zensical.toml` — Site configuration (TOML, not YAML). Equivalent to `mkdocs.yml` in MkDocs projects.
- `site/` — Build output (not committed).
- Zensical uses the same Markdown extension ecosystem as Material for MkDocs (Python Markdown + pymdownx): admonitions, content tabs, task lists, etc.

## Content conventions

- **Audience:** CMI researchers and project managers — domain experts, not data managers. Assume no library-science or IT background.
- **Tone:** Plain language, action-oriented, concise. Each page should be scannable in a few minutes.
- **Context-sensitive:** CMI research involves fieldwork in the Global South, cross-border partnerships, sensitive populations, and Norwegian privacy law (GDPR/personopplysningsloven). Offer pragmatic alternatives alongside ideal recommendations.
- **Page structure:** (1) short intro paragraph, (2) practical steps, (3) links to CMI policies/templates/external resources, (4) cross-references to related pages in other lifecycle phases.
- **Headings:** Prefer imperative ("Create a data management plan") over noun phrases ("Data management plans").
- **Admonitions:** Use `!!! warning`, `!!! tip`, etc. for callouts — especially CMI-specific policy notes.
- **Page length:** If a page exceeds ~800 words of body text, consider splitting.
- **Examples:** Prefer concrete social-science fieldwork examples (interviews, surveys, ethnographic notes) over abstract guidance.
- **Tools/services:** Note whether CMI-provided, freely available, or licensed.

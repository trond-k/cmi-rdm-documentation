# RDM Hub

Research data management guidance for CMI researchers — organised around the project lifecycle: **before**, **during**, and **after**.

## About

The RDM Hub is a documentation site for the [Chr. Michelsen Institute (CMI)](https://www.cmi.no/). It provides practical guidance on managing research data throughout the research lifecycle, with attention to CMI's research context: fieldwork in the Global South, cross-border partnerships, and sensitive topics.

Built with [Zensical](https://zensical.org/), a modern static site generator by the creators of Material for MkDocs. Content is authored in Markdown and configured via `zensical.toml`.

## Audience

The primary readers are CMI researchers and project managers — people with deep domain expertise but varying levels of technical comfort. Many work across institutions and countries, often in settings with limited connectivity or heightened data-sensitivity requirements.

## Structure

The site is organised around three lifecycle phases. Each section is self-contained so that a researcher can jump directly to the phase they're in.

```
docs/
  index.md                  # Landing page — what this site is and how to use it
  before/                   # Planning phase
    index.md                #   Overview: getting started with RDM planning
    dmp.md                  #   Data management plans
    ethics.md               #   Ethics and approvals
    storage.md              #   Choosing storage solutions
    partnerships.md         #   Data sharing in cross-border partnerships
  during/                   # Active research
    index.md                #   Overview: managing data day-to-day
    file-organisation.md    #   Naming conventions, folder structure
    documentation.md        #   Codebooks, field notes, metadata
    security.md             #   Encryption, access control, fieldwork devices
  after/                    # Wrapping up
    index.md                #   Overview: closing out a project
    cleaning.md             #   Data cleaning and validation
    archiving.md            #   Long-term preservation
    sharing.md              #   Publishing and reuse
    deletion.md             #   Retention schedules and secure deletion
```

<!-- TODO: Decide whether to use explicit nav in zensical.toml or rely on
     directory-based auto-navigation. Explicit nav gives control over ordering
     and display names; auto-nav keeps things simpler as pages are added. -->

## Content conventions

### Tone and style

- **Plain language.** Avoid jargon where possible; define terms on first use. Readers may not have a library-science or IT background.
- **Action-oriented.** Lead with what the researcher should *do*, then explain why. Prefer imperative headings ("Create a data management plan") over noun phrases ("Data management plans").
- **Concise.** Each page should be scannable in a few minutes. Use admonitions for warnings, tips, and CMI-specific policy notes rather than burying them in prose.
- **Sensitive to context.** Acknowledge that "best practice" often looks different in resource-constrained or politically sensitive fieldwork environments. Offer pragmatic alternatives alongside ideal recommendations.

### Markdown patterns

Zensical supports a rich set of Markdown extensions inherited from Material for MkDocs. Prefer these patterns for consistency across the site:

- **Admonitions** for callouts:
  ```markdown
  !!! warning "Personal data"
      If your dataset contains personal identifiers, Norwegian privacy
      regulations (personopplysningsloven) apply regardless of where
      the data was collected.
  ```
- **Content tabs** when guidance differs by scenario (e.g., quantitative vs. qualitative data, NSD vs. other archives).
- **Checklists** for step-by-step procedures — use standard Markdown task lists.
- **Links between sections** — cross-reference freely between phases. A researcher reading about ethics approvals (before) should be pointed to secure deletion (after) and vice versa.

<!-- TODO: List the specific Markdown extensions enabled in zensical.toml
     (e.g., admonition, pymdownx.details, pymdownx.tabbed, etc.) -->

### What each page should include

1. A short introductory paragraph explaining what and why.
2. Practical steps or guidance (the main body).
3. Links to relevant CMI policies, templates, or external resources.
4. Cross-references to related pages in other lifecycle phases.

## Configuration

The site is configured in `zensical.toml` at the project root. Key settings:

```toml
[project]
site_name = "RDM Hub"
site_description = "Research data management guidance for CMI researchers"
site_url = "https://..."          # Set when deployment target is known
docs_dir = "docs"

# copyright = """
# &copy; Chr. Michelsen Institute
# """

# Navigation — explicit example (remove if using auto-nav):
# nav = [
#   { "Home" = "index.md" },
#   { "Before" = [
#     { "Overview" = "before/index.md" },
#     { "Data management plans" = "before/dmp.md" },
#     { "Ethics and approvals" = "before/ethics.md" },
#     { "Storage" = "before/storage.md" },
#     { "Partnerships" = "before/partnerships.md" },
#   ]},
#   { "During" = [
#     { "Overview" = "during/index.md" },
#     { "File organisation" = "during/file-organisation.md" },
#     { "Documentation" = "during/documentation.md" },
#     { "Security" = "during/security.md" },
#   ]},
#   { "After" = [
#     { "Overview" = "after/index.md" },
#     { "Cleaning" = "after/cleaning.md" },
#     { "Archiving" = "after/archiving.md" },
#     { "Sharing" = "after/sharing.md" },
#     { "Deletion" = "after/deletion.md" },
#   ]},
# ]
```

See the [Zensical setup docs](https://zensical.org/docs/setup/basics/) for the full set of configuration options.

## Development

Requires [uv](https://docs.astral.sh/uv/) and Python 3.13+.

```bash
# Install dependencies
uv sync

# Start local dev server (auto-rebuilds on changes)
uv run zensical serve

# Build the static site
uv run zensical build
```

The built site is written to the `site/` directory by default.

## For AI assistants

This section provides context for Claude or other AI tools helping to write, review, or restructure content in this project.

### Project context

- **Organisation:** Chr. Michelsen Institute (CMI) — an independent research institute in Bergen, Norway, focused on development, human rights, and governance.
- **Research context:** CMI researchers frequently conduct fieldwork in the Global South, work with sensitive populations, partner across institutional and national boundaries, and handle data subject to Norwegian privacy law and international ethics frameworks.
- **Regulatory environment:** Norwegian law (personopplysningsloven / GDPR), NSD (Sikt) data services for archiving, institutional ethics review. Some projects also fall under host-country regulations.

### Writing guidance

When creating or editing pages:

- Write for researchers, not data managers. Assume the reader is expert in their field but new to formal RDM practices.
- Keep pages focused on one topic. If a page grows beyond ~800 words of body text, consider splitting it.
- Use Zensical/Material for MkDocs admonition syntax for tips, warnings, and CMI-specific policy notes.
- Prefer concrete examples drawn from social-science fieldwork (interviews, surveys, ethnographic notes) over abstract guidance.
- When referencing tools or services, note whether they are CMI-provided, freely available, or require licensing.
- Always cross-reference related pages in other lifecycle phases.

### Technical notes

- This is a Zensical project. Configuration lives in `zensical.toml` (TOML format), not `mkdocs.yml`.
- Content is Markdown in the `docs/` directory. Zensical renders it to static HTML.
- The dev server is started with `uv run zensical serve`; the site is built with `uv run zensical build`.
- Zensical uses the same Markdown extension ecosystem as Material for MkDocs (Python Markdown + pymdownx).

## License

Content is intended for CMI internal use. See institutional policies for reuse terms.
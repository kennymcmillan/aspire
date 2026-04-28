# Aspire Academy Quarto Extension

A Quarto **format extension** that brands HTML reports in the Aspire Academy
visual identity. Mirrors the [`aspire_dash`](https://github.com/kennymcmillan/aspire_dash)
palette so Dash apps and Quarto reports look like siblings.

> 🎨 White / black / blue. Soft, crisp, modern. Branded gradient title banner,
> alternating table bands, accent bars on every `##` heading, soft callouts.

## Installation

From any Quarto project folder:

```bash
quarto add kennymcmillan/aspire-quarto-template
```

This drops the extension into `_extensions/kennymcmillan/aspire-quarto-template/`.
Commit that folder so the extension travels with the report — Posit Connect
will pick it up at deploy time.

## Use it in a `.qmd`

```yaml
---
title: "My Aspire Report"
subtitle: "One-line description"
date: today
author: "Aspire Performance Analytics"
format:
  aspire-html: default
execute:
  echo: false
  warning: false
jupyter: python3
---
```

Or pass overrides:

```yaml
format:
  aspire-html:
    toc-depth: 3
    fig-width: 12
```

## What you get

| Element | Style |
|---|---|
| Title block | Navy → blue gradient banner with the Aspire logo top-right |
| Headings | h2 has an accent bar (Aspire blue → gold) on the left |
| Tables | Navy header, alternating Aspire-50 / white rows, hover highlight |
| Callouts | Soft tint per type — `note`, `tip`, `warning`, `important` |
| Code blocks | Left-accent strip in Aspire blue, JetBrains Mono font |
| Links | Aspire blue, smooth underline on hover |
| TOC | Left sidebar, blue accent on active section |
| Footer | Logo + "Internal use only" tagline |
| Print | Color-adjust forced so banners survive PDF export |

## Quarto features the theme styles

```markdown
::: {.callout-tip}
## Recommendation
Athletes outranking the lowest Target should be reviewed for pathway upgrade.
:::

::: {.callout-warning}
Source data refresh paused — last update: 2026-04-25.
:::

::: {.panel-tabset}
## Boys
table here

## Girls
table here
:::
```

Cross-references work too:

- `@fig-rankings` for figures
- `@tbl-targets` for tables
- `@sec-methodology` for sections

## Brand palette

The SCSS exposes these as variables. Override them in your own `.scss` if you
need to (e.g. for a slightly different sport-specific accent).

| Token | Hex | Usage |
|-------|-----|-------|
| `$aspire-900` | `#001d3d` | Deep navy — title block, headings |
| `$aspire-700` | `#003566` | h3 colour, secondary accents |
| `$aspire-600` | `#004185` | **PRIMARY** — buttons, accents |
| `$aspire-500` | `#0059b3` | Links, code-block accent |
| `$aspire-50`  | `#eff6ff` | Soft blue wash — code bg, table bands |
| `$gold`       | `#fbb800` | Awards, emphasis (accent bar gradient) |

Source: `aspire_dash/brand.yml` and `aspire.qa`.

## Project structure

```
_extension.yml      ← Quarto extension manifest (declares aspire-html format)
aspire.scss         ← SCSS theme (Bootstrap variable overrides + custom rules)
aspire-footer.html  ← Branded footer partial (include-after-body)
aspire-logo.png     ← Aspire Academy mark
README.md
LICENSE
```

## Updating

If the extension upstream changes:

```bash
quarto update kennymcmillan/aspire-quarto-template
```

## First report using this extension

[`squash-target-rankings`](https://posit.aspire.qa/content/4ef1b561-5bec-4cc0-864f-dffc65fe9e47/) —
Squash Target Athletes vs ESF Rankings (live SAMS roster + Hetzner ESF scrape).

## Sister project

[`aspire_dash`](https://github.com/kennymcmillan/aspire_dash) — same palette
applied to Plotly Dash apps. Same colour tokens, same fonts, same logo.

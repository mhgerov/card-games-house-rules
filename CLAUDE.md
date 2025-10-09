# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a Jekyll-based static documentation site for card game rules and house rules. The site uses the Just the Docs theme and is published to GitHub Pages at https://mhgerov.github.io/card-games-house-rules.

## Development Commands

**Install dependencies:**
```bash
bundle install
```
(Requires ruby+devkit installed)

**Run local development server:**
```bash
bundle exec jekyll server
```

**Build the site:**
```bash
bundle exec jekyll build
```

## Site Architecture

### Content Structure

The site is organized into two main sections with hierarchical navigation:

1. **Games** (`games/` directory)
   - `games/games.md` is the parent page with `has_children: true`
   - Individual game files (e.g., `bourre.md`, `tichu.md`) have `parent: Games` in their front matter

2. **Recommendations** (`recommendations/` directory)
   - `recommendations/recommendations.md` is the parent page with `has_children: true`
   - Child pages like `beginner-friendly.md` and `player-count.md` have `parent: Recommendations`

### Page Front Matter

All pages require Jekyll front matter with:
- `title`: The page title
- `layout`: Typically `default` for content pages, `home` for index
- `parent`: For child pages, references the parent page title
- `has_children`: Set to `true` for parent pages that have child pages
- `permalink`: For parent pages, defines the URL path

### Internal Links

Use Jekyll's `site.baseurl` for internal links:
```markdown
[Link Text]({{ site.baseurl }}/games/game-name.html)
```

## Site Configuration

Site settings are in `_config.yml`:
- Theme: just-the-docs (version 0.10.0)
- Color scheme: dark
- Jekyll version: ~> 4.3.4

## Deployment

The site uses GitHub Actions for deployment (`.github/workflows/pages.yml`). Changes pushed to the main branch are automatically built and deployed to GitHub Pages.

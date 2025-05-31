# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is the "Black Flag" campaign documentation repository - a grassroots political campaign focused on preserving two-way traffic on Shore Road in Swanage. The project contains strategic planning documents, analysis, and actionable items for the campaign against proposed traffic management changes.

## Project Structure

The repository consists of strategic markdown documents organized by theme:

- **pyproject.toml** - Project configuration file for uv package manager
- **init-prd.md** - Product Requirements Document for creating a campaign wiki using MkDocs
- **initial-debrief.md** - Comprehensive briefing document with campaign strategy and analysis
- **actionables.md** - Specific next steps and tactical implementation items
- **core-issue.md** - Detailed analysis of the Shore Road traffic management issue
- **tactics-strategy.md** - Campaign strategy, messaging, and target audience analysis
- **authority.md, balanced-pragmatism.md, broader-themes.md, critique.md, time.md, tools-resources.md** - Additional strategic documents

## Development Commands

According to the PRD, the planned development workflow includes:

```bash
# Install MkDocs with UV package manager
uv add mkdocs mkdocs-material mkdocs-material-extensions

# Local development
mkdocs serve

# Test with curl requests
curl http://localhost:8000

# Deploy to GitHub Pages
mkdocs gh-deploy
```

## Planned Architecture

The project is designed to become a MkDocs-based wiki with:

- **Material for MkDocs theme** for clean, professional appearance
- **GitHub Pages deployment** for free hosting
- **Private repository** with selective public access
- **Markdown content** organized hierarchically by campaign themes
- **Search functionality** and cross-linking between documents
- **Version control** through Git for audit trail

## File Naming Convention

Documents should follow: `black-flag--<section-number>-<filename>.md`

## Key Campaign Elements

- **Survey Analysis** - Focus on the 3 mandatory questions "hack" (20 seconds vs 20 minutes)
- **Target Demographics** - Young population, De Moulham Road residents, beach hut owners
- **Messaging** - Freedom, democratic rights, community impact
- **Tactics** - Flyers with QR codes, social media, direct canvassing
- **Timeline** - June 29th survey deadline creates urgency

## Content Guidelines

- Maintain political neutrality in technical documentation
- Focus on factual analysis and strategic planning
- Preserve the grassroots, community-focused tone
- Document evidence-based arguments and data analysis
- Track actionable items and campaign progress
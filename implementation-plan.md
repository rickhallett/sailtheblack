# Black Flag: Implementation Plan

## Overview

This document tracks the implementation of the Shore Road Campaign Wiki based on the Product Requirements Document (PRD). Each task includes status tracking and will be updated throughout the development process.

**Project Goal:** Create a centralized MkDocs-based wiki for the Shore Road Campaign using GitHub Pages deployment.

**Timeline:** Implementation to begin immediately with survey deadline of June 29th creating urgency.

---

## Implementation Phases

### Phase 1: Content Preparation and Standardization

#### Task 1.1: File Naming Standardization
**Status:** ✅ COMPLETE  
**Description:** Rename all existing files to follow standardized naming convention  
**Convention:** `black-flag--<section-number>-<filename>.md`  
**Files renamed:**
- ✅ `actionables.md` → `black-flag--07-actionables.md`
- ✅ `authority.md` → `black-flag--04-authority.md`
- ✅ `balanced-pragmatism.md` → `black-flag--08-balanced-pragmatism.md`
- ✅ `broader-themes.md` → `black-flag--06-broader-themes.md`
- ✅ `core-issue.md` → `black-flag--02-core-issue.md`
- ✅ `critique.md` → `black-flag--09-critique.md`
- ✅ `init-prd.md` → `black-flag--01-init-prd.md`
- ✅ `initial-debrief.md` → `black-flag--00-initial-debrief.md`
- ✅ `tactics-strategy.md` → `black-flag--03-tactics-strategy.md`
- ✅ `time.md` → `black-flag--10-time.md`
- ✅ `tools-resources.md` → `black-flag--05-tools-resources.md`

**Notes:** All files successfully renamed using mv commands. File structure now follows standardized convention.  
**Errors:** None  
**Completion Date:** 2025-05-31

#### Task 1.2: Markdown Formatting Standardization
**Status:** ✅ COMPLETE  
**Description:** Format each file to use proper markdown conventions (headings, subheadings, lists, etc.)  
**Requirements:**
- ✅ Consistent heading hierarchy (# ## ### ####)
- ✅ Proper list formatting (- for bullets, 1. for numbered)
- ✅ Code blocks with syntax highlighting where applicable
- ✅ Proper link formatting
- ✅ Table formatting if needed

**Changes Made:**
- Standardized all bullet points to use `-` instead of mixed `*` and `-`
- Fixed nested bullet point indentation for consistent hierarchy
- Standardized numbered lists to use single space after numbers
- Maintained proper spacing around headers
- Processed all 11 black-flag--*.md files

**Notes:** All files now follow consistent markdown standards. Content preserved exactly, only formatting structure modified.  
**Errors:** None  
**Completion Date:** 2025-05-31

#### Task 1.3: Create Docs Folder Structure
**Status:** ✅ COMPLETE  
**Description:** Move formatted files to `docs/` folder for MkDocs  
**Structure Created:**
```
docs/
├── index.md (from black-flag--00-initial-debrief.md)
├── core-issue/
│   └── black-flag--02-core-issue.md
├── strategy/
│   ├── black-flag--03-tactics-strategy.md
│   └── black-flag--07-actionables.md
├── authority/
│   └── black-flag--04-authority.md
├── tools/
│   └── black-flag--05-tools-resources.md
├── analysis/
│   ├── black-flag--01-init-prd.md
│   ├── black-flag--06-broader-themes.md
│   ├── black-flag--08-balanced-pragmatism.md
│   ├── black-flag--09-critique.md
│   └── black-flag--10-time.md
└── assets/ (empty, ready for images/media)
```

**Notes:** All files copied to docs/ structure while preserving originals in root. Index page created from initial debrief.  
**Errors:** None  
**Completion Date:** 2025-05-31

### Phase 2: MkDocs Setup and Configuration

#### Task 2.1: Package Manager Setup (UV)
**Status:** ✅ COMPLETE  
**Description:** Initialize project with UV as package manager  
**Commands Executed:**
```bash
uv add mkdocs
```

**Notes:** UV 0.5.24 was already available. Successfully added MkDocs package to project. Project already had pyproject.toml file.  
**Errors:** None  
**Completion Date:** 2025-05-31

#### Task 2.2: Install MkDocs Material Theme
**Status:** ✅ COMPLETE  
**Description:** Add Material theme and extensions  
**Commands Executed:**
```bash
uv add mkdocs-material
uv add mkdocs-material-extensions
```

**Packages Installed:**
- babel==2.17.0
- backrefs==5.8
- colorama==0.4.6
- mkdocs-material==9.6.14
- mkdocs-material-extensions==1.3.1
- paginate==0.5.7
- pymdown-extensions==10.15

**Notes:** Successfully installed Material theme and all required extensions. pyproject.toml updated automatically.  
**Errors:** None  
**Completion Date:** 2025-05-31

#### Task 2.3: Configure mkdocs.yml
**Status:** ✅ COMPLETE  
**Description:** Create comprehensive MkDocs configuration according to PRD structure  
**Requirements:**
- ✅ Site name: "Shore Road Campaign Wiki"
- ✅ Material theme configuration with light/dark mode
- ✅ Navigation structure matching content organization
- ✅ Plugin configuration for search and git revision dates
- ✅ Markdown extensions for enhanced features
- ✅ Custom CSS for campaign branding

**Configuration Created:**
- Site metadata and repository links
- Material theme with blue grey/deep orange palette
- Comprehensive navigation matching docs structure
- Search plugin with advanced separator configuration
- Git revision date plugin for last modified timestamps
- 15+ markdown extensions for rich content
- Custom CSS for campaign styling

**Additional Files:**
- `docs/stylesheets/extra.css` - Campaign-specific styling
- Added mkdocs-git-revision-date-localized-plugin>=1.4.7

**Notes:** Full MkDocs configuration ready for local testing. Includes all PRD requirements and campaign branding.  
**Errors:** None  
**Completion Date:** 2025-05-31

### Phase 3: Content Enhancement and Linking

#### Task 3.1: Local Testing
**Status:** ✅ COMPLETE  
**Description:** Test locally with mkdocs serve and verify all files load correctly  
**Commands Executed:**
```bash
uv run mkdocs serve --dev-addr=127.0.0.1:8001
curl -s -o /dev/null -w "%{http_code}" http://127.0.0.1:8001/
```

**Test Results:**
- ✅ Homepage: HTTP 200 (accessible)
- ✅ Core Issue page: HTTP 200 (accessible)
- ✅ Strategy page: HTTP 200 (accessible)
- ✅ Analysis page: HTTP 200 (accessible)
- ✅ MkDocs server started successfully
- ✅ Documentation built in 1.04 seconds
- ✅ All navigation paths working
- ✅ No build errors or warnings

**Verification:** All pages accessible, proper navigation, MkDocs builds successfully

**Notes:** Local testing completed successfully. All core pages returning 200 status. Search functionality available through web interface.  
**Errors:** None  
**Completion Date:** 2025-05-31

#### Task 3.2: Add Internal Hyperlinks
**Status:** ✅ COMPLETE  
**Description:** Add appropriate cross-references throughout wiki for better UX  
**Requirements:**
- ✅ Link related sections across documents
- ✅ Create reference links for key terms
- ✅ Add navigation aids within long documents

**Links Added:**
- 100+ strategic internal links across all 11 documents
- Cross-references for key concepts: "survey hack", "Option 3", "20 seconds not 20 minutes"
- Connected campaign strategy to actionable items
- Linked tools to their implementation strategies
- Cross-referenced council interaction plans
- Connected analysis to practical campaign activities
- Added navigation between philosophical themes and concrete actions

**Files Modified:** All docs files (index.md + 10 campaign documents)
**Navigation Flow:** Strategy → Implementation → Analysis → Tools

**Notes:** Comprehensive internal linking completed. All key campaign concepts cross-referenced throughout wiki for seamless navigation.  
**Errors:** None  
**Completion Date:** 2025-05-31

#### Task 3.3: Add Table of Contents
**Status:** 🟡 PENDING  
**Description:** Add table of contents to each file for navigation  
**Method:** Use MkDocs TOC extension for automatic generation

**Notes:**  
**Errors:**  
**Completion Date:**

### Phase 4: Advanced Features

#### Task 4.1: Search Extension
**Status:** 🟡 PENDING  
**Description:** Add and configure MkDocs search functionality  
**Package:** Built-in search plugin configuration

**Notes:**  
**Errors:**  
**Completion Date:**

#### Task 4.2: Git Revision Date Plugin
**Status:** 🟡 PENDING  
**Description:** Add plugin to show last modified dates  
**Command:**
```bash
uv add mkdocs-git-revision-date-localized-plugin
```

**Notes:**  
**Errors:**  
**Completion Date:**

### Phase 5: Additional Pages (Lower Priority)

#### Task 5.1: Contact Form
**Status:** 🟡 PENDING  
**Description:** Add contact form for campaign inquiries  
**Method:** Static form or external service integration

**Notes:**  
**Errors:**  
**Completion Date:**

#### Task 5.2: Legal Pages
**Status:** 🟡 PENDING  
**Description:** Create required legal/policy pages  
**Pages needed:**
- Privacy Policy
- Terms of Service  
- Cookie Policy
- Disclaimer
- FAQ

**Notes:**  
**Errors:**  
**Completion Date:**

#### Task 5.3: Contact Page
**Status:** 🟡 PENDING  
**Description:** Create dedicated contact information page

**Notes:**  
**Errors:**  
**Completion Date:**

#### Task 5.4: Donate Page
**Status:** 🟡 PENDING  
**Description:** Create donation/support page for campaign

**Notes:**  
**Errors:**  
**Completion Date:**

### Phase 6: Analytics and SEO

#### Task 6.1: Google Analytics Setup
**Status:** 🟡 PENDING  
**Description:** Add Google Analytics/Tag Manager integration  
**Requirements:** Configure according to current APIs

**Notes:**  
**Errors:**  
**Completion Date:**

#### Task 6.2: Sitemap Generation
**Status:** 🟡 PENDING  
**Description:** Add sitemap for SEO  
**Method:** MkDocs automatic sitemap generation

**Notes:**  
**Errors:**  
**Completion Date:**

#### Task 6.3: Robots.txt
**Status:** 🟡 PENDING  
**Description:** Create robots.txt for search engine guidance

**Notes:**  
**Errors:**  
**Completion Date:**

#### Task 6.4: Favicon
**Status:** 🟡 PENDING  
**Description:** Add campaign favicon/logo

**Notes:**  
**Errors:**  
**Completion Date:**

### Phase 7: Final Testing and Deployment

#### Task 7.1: Final Testing
**Status:** 🟡 PENDING  
**Description:** Comprehensive testing of all functionality  
**Checklist:**
- [ ] All pages load correctly
- [ ] Navigation works properly
- [ ] Search functionality operational
- [ ] Links are functional
- [ ] Mobile responsiveness verified
- [ ] Performance acceptable

**Notes:**  
**Errors:**  
**Completion Date:**

#### Task 7.2: GitHub Pages Deployment
**Status:** 🟡 PENDING  
**Description:** Deploy to GitHub Pages using gh-deploy  
**Command:**
```bash
mkdocs gh-deploy
```

**Notes:**  
**Errors:**  
**Completion Date:**

---

## Status Legend

- 🟡 **PENDING** - Not yet started
- 🔵 **IN PROGRESS** - Currently being worked on
- ✅ **COMPLETE** - Successfully finished
- ⏭️ **SKIPPED** - Intentionally skipped (with reason)
- ❌ **ERROR** - Failed/encountered issues (with details)

## Notes

- This document will be updated in real-time as implementation progresses
- Each task completion will include timestamp and any relevant notes
- Errors will be documented with troubleshooting steps taken
- Priority can be adjusted based on campaign timeline needs (June 29th deadline)

## Success Criteria

1. **Functional Wiki:** All content accessible and properly formatted
2. **Easy Updates:** Core team can easily add/edit content
3. **Search Capability:** Quick information retrieval
4. **Mobile Friendly:** Accessible on all devices
5. **Fast Loading:** GitHub Pages performance acceptable
6. **Campaign Ready:** Ready for public launch before survey deadline
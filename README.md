# Cilantro Site Changelog

The changelog collection for **Cilantro Site** - the Lossless Group marketing and documentation website.

## Purpose

This git submodule contains all changelog entries for Cilantro Site releases, features, design updates, and content changes. Each entry documents changes in a structured markdown format that gets automatically aggregated into the unified changelog system.

## Frontmatter Schema

All changelog entries must include the following YAML frontmatter:

```yaml
---
version: '0.1.0'                    # Semver version (required)
title: 'Neo Landing Page Release'  # Human-readable title (required)
lede: 'Initial release of...'       # Short description/hook (required)
slug: 'v0.1.0'                      # URL-safe identifier (required)
date_created: '2025-10-12'          # YYYY-MM-DD - When work started (required)
date_modified: '2025-10-14'         # YYYY-MM-DD - Last updated (required)
date_started: '2025-10-06'          # YYYY-MM-DD - Development start (required)
date_shipped: '2025-10-13'          # YYYY-MM-DD - Release date (required)
product: 'Cilantro-Site'            # Product name (required - must be 'Cilantro-Site')
type: 'Minor'                       # Major|Minor|Patch (required)
is_release: false                   # Boolean - official release? (required)
publish: true                       # Boolean - show publicly? (required)
summary: 'This documents...'        # SEO/meta description (required)
why_care: 'We now communicate...'   # User benefit statement (optional)
authors:                            # List of primary authors (required)
  - 'Michael Staton'
contributors:                       # Additional contributors (optional)
  - 'Team Member'
signed_off:                         # Approvers/reviewers (optional)
  - 'Nicholas Cooper'
tags:                               # Categorization tags (optional)
  - 'Landing-Pages'
  - 'Design-System'
  - 'Content'
---
```

## Field Descriptions

### Core Metadata
- **`version`** *(string, required)* - Semantic version number (e.g., '0.1.0', '1.0.0')
- **`title`** *(string, required)* - Display title for the changelog entry
- **`lede`** *(string, required)* - Short hook/summary (1-2 sentences)
- **`slug`** *(string, required)* - URL-safe identifier (typically matches version)

### Dates
All dates use `YYYY-MM-DD` format:
- **`date_created`** *(date, required)* - When the changelog entry was first created
- **`date_modified`** *(date, required)* - Last modification date
- **`date_started`** *(date, required)* - When development/work began
- **`date_shipped`** *(date, required)* - Official release/ship date

### Classification
- **`product`** *(string, required)* - Must be `'Cilantro-Site'` for this collection
- **`type`** *(string, required)* - One of: `'Major'`, `'Minor'`, `'Patch'`
- **`is_release`** *(boolean, required)* - `true` for major site releases, `false` for incremental updates
- **`publish`** *(boolean, required)* - `true` to show publicly, `false` for drafts

### Content
- **`summary`** *(string, required)* - Brief summary for SEO and meta tags
- **`why_care`** *(string, optional)* - Why users should care about this update

### Attribution
- **`authors`** *(array, required)* - Primary authors who created the changes
- **`contributors`** *(array, optional)* - Additional contributors
- **`signed_off`** *(array, optional)* - Reviewers/approvers

### Organization
- **`tags`** *(array, optional)* - Categorization tags for filtering and search

Common tags for Cilantro Site:
- `Landing-Pages` - New landing pages
- `Design-System` - Design system updates
- `Content` - Content additions/updates
- `Performance` - Performance improvements
- `Accessibility` - A11y enhancements
- `SEO` - SEO optimizations
- `Navigation` - Site structure/navigation
- `Components` - New UI components

## File Naming Convention

Use version-based naming for major releases:
```
v0.1.0.md
v1.0.0.md
```

For feature updates and changes, use date-based naming:
```
2025-10-15_Neo-Landing-Page.md
2025-11-01_Design-System-Refresh.md
2025-11-15_Navigation-Redesign.md
```

## Content Structure

After frontmatter, organize content using these sections:

### Standard Sections
- **🎉 New Features** - New pages, sections, or capabilities
- **🐛 Bug Fixes** - Visual bugs, broken links, layout issues
- **💥 Breaking Changes** - URL changes, removed pages
- **🔧 Improvements** - Design refinements, UX enhancements
- **📚 Documentation** - New content, guides, articles
- **🔒 Security** - Security-related updates
- **⚡ Performance** - Speed optimizations, bundle size
- **♿ Accessibility** - A11y improvements
- **🎨 Design System** - Component library updates

### Example Structure

```markdown
## 🎉 New Features

### Neo Landing Page at `/jam-with/neo`

Full-featured marketing landing page with Matrix-inspired design...

**Visual Design System:**
\`\`\`css
.neo-landing {
  --neo-green: #00ff9c;
  --neo-bg-dark: #070a08;
}
\`\`\`

**Location:** \`src/pages/jam-with/neo.astro\`

## 🔧 Improvements

### Hero Animation Performance

Optimized hero section animations reducing CPU usage by 40%...

**Before:** 60fps drops during scroll
**After:** Consistent 60fps
```

## Writing Guidelines

### Do:
- ✅ Include code snippets showing implementation
- ✅ Reference file paths with line numbers
- ✅ Show before/after comparisons for visual changes
- ✅ Include screenshots or design system specs
- ✅ Link to deployed pages and related PRs
- ✅ Document technical patterns established

### Don't:
- ❌ Assume readers know the site structure
- ❌ Skip technical details in favor of marketing copy
- ❌ Forget to document design system additions
- ❌ Leave out accessibility considerations
- ❌ Ignore performance impact of changes

### Site-Specific Guidelines

**For Landing Pages:**
- Document section architecture
- Include CSS variable definitions
- Show component hierarchy
- Reference design inspirations
- Note responsive breakpoints

**For Design System:**
- Show component API/props
- Include usage examples
- Document color tokens
- Specify typography scales
- List accessibility features

**For Performance:**
- Include metrics (Lighthouse scores, bundle sizes)
- Show before/after comparisons
- Document optimization techniques
- Note any trade-offs made

## Git Workflow

This is a git submodule. To add a new changelog entry:

```bash
# 1. Create new changelog file
echo "---
version: '0.2.0'
title: 'Design System Update'
# ... rest of frontmatter
---

## 🎨 Design System
..." > v0.2.0.md

# 2. Commit and push
git add v0.2.0.md
git commit -m "Add changelog for v0.2.0"
git push origin main
```

The main site build will pull updates automatically.

## Integration

These changelog entries are consumed by:
- **Main Site:** `/changelog/cilantro-site` - Site-specific timeline
- **Unified Timeline:** `/changelog` - All products
- **RSS Feed:** `/changelog/cilantro-site/rss` - Site-specific feed

## Technical Documentation

Since Cilantro Site changelog entries often serve as **technical documentation**, they should:

1. **Document Patterns** - Explain reusable patterns for future development
2. **Show Implementation** - Include actual code from the site
3. **Reference Architecture** - Link to architectural decisions
4. **Capture Context** - Explain why decisions were made
5. **Guide Future Work** - Suggest improvements and next steps

Think of each entry as both a changelog AND a technical reference document.

## Questions?

Contact the site team or refer to:
- Main changelog spec: `/CHANGELOG_SPEC.md`
- Site documentation: `/CLAUDE.md`
- Design system: `/src/components/basics/`

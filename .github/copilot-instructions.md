# CNCF Artwork Repository - Copilot Instructions

## Repository Overview

This is the official CNCF artwork repository containing logos and branding assets for 200+ cloud native projects in standardized formats (PNG & SVG). This is a static asset repository with no build system, tests, or compilation. Changes are manually reviewed by CNCF staff and project maintainers. Strict adherence to file naming and organizational conventions is critical.

## Repository Structure

```
artwork/
├── projects/          # Active CNCF project logos (200+ directories)
│   └── [project-name]/
│       ├── horizontal/  # Landscape format logos
│       │   ├── color/
│       │   ├── black/
│       │   └── white/
│       ├── stacked/     # Square-ish format logos
│       │   ├── color/
│       │   ├── black/
│       │   └── white/
│       ├── icon/        # Icon only (no project name)
│       │   ├── color/
│       │   ├── black/
│       │   └── white/
│       └── README.md    # Optional project-specific documentation
├── archived/          # Archived/retired project logos
├── other/             # CNCF branding, certifications, events, etc.
├── examples/          # Documentation showing all logos
│   ├── graduated.md
│   ├── incubating.md
│   ├── sandbox_*.md
│   ├── other.md
│   └── archived.md
├── README.md          # Main documentation
└── .github/
    └── pull_request_template.md
```

## Standard File Organization

Every project MUST have **3 layouts** × **3 colors** × **2 formats** = **minimum 18 files**:

**Layouts**: `horizontal/`, `stacked/`, `icon/`
**Colors**: `color/`, `black/`, `white/`
**Formats**: `.png`, `.svg`

**File naming**: `[project-name]-[layout]-[color].[extension]` (lowercase, kebab-case)

Example: `projects/prometheus/horizontal/color/prometheus-horizontal-color.svg`

**Special cases**: 
- Some projects (Kubernetes) have additional color variations (all-blue-color, white-text)
- Some projects have `print/` versions (e.g., KEDA, SlimFaas) which may or may not be documented in examples/*.md
- Projects can have sub-components in `sub-projects/` directories (e.g., kubernetes/sub-projects/)

## Adding New Project Artwork

1. **Prepare files**: Ensure the minimum number of files are present (18+), test/optimize SVGs at https://autocrop.cncf.io
2. **Create structure**: `mkdir -p projects/[name]/{horizontal,stacked,icon}/{color,black,white}`
3. **Update documentation**:
   - Add HTML table section to appropriate `examples/*.md` (graduated.md, incubating.md, sandbox_*.md, or other.md)
   - Add link to main README.md
   - Maintain alphabetical (A-Z) order in both files
   - Follow exact table format from existing entries

## Approval & Workflow

- **PRs require TWO approvals**: CNCF staff + project maintainer
- No CI/CD pipelines or automated tests
- Manual verification using `file` command, markdown preview, and link checking
- PR template in `.github/pull_request_template.md` has full checklist

## Common Tasks

**Moving to archived**: Move `projects/[name]` → `archived/[name]`, update examples/archived.md and README.md links

**Updating logos**: Replace files, keep same names, re-optimize SVGs at https://autocrop.cncf.io

**Sub-components**: Create `sub-projects/` directory within project, follow same structure

## Verification & Tools

**SVG validation**: `file projects/[project]/horizontal/color/[project]-horizontal-color.svg` (should show "SVG Scalable Vector Graphics")

**Count files**: `find projects/[project] -type f | wc -l` (should be ≥18)

**External tools**:
- https://autocrop.cncf.io - Test and optimize SVGs before submission
- https://www.cncf.io/brand-guidelines/ - Brand guidelines
- https://github.com/cncf/foundation/blob/master/style-guide.md - Style guide

**Trademark**: All artwork subject to Linux Foundation trademark usage (https://www.linuxfoundation.org/trademark-usage). Certified Kubernetes marks require conformance.

## Common Pitfalls

1. Incorrect naming (must be `[project]-[layout]-[color].[ext]`)
2. Missing PNG or SVG for any variation
3. Non-vector SVGs (embedded rasters)
4. Breaking alphabetical order in documentation
5. Forgetting to update both examples/*.md AND README.md
6. Incomplete directory structure (need all 9 subdirectories)
7. Wrong examples file for project status (graduated/incubating/sandbox)

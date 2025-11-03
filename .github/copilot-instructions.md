# CNCF Artwork Repository - Copilot Instructions

## Repository Overview

This is the official CNCF artwork repository containing logos and branding assets for CNCF projects and programs. The repository hosts artwork for 200+ cloud native projects in standardized formats.

**Primary Purpose**: Centralized storage and distribution of official CNCF project logos in multiple formats, layouts, and color variations.

**Key Characteristics**:
- This is primarily a static asset repository (images and documentation)
- No build system, tests, or compilation required
- Changes are manually reviewed by CNCF staff and project maintainers
- Strict adherence to file naming and organizational conventions is critical

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

## Standard File Organization Requirements

### For Each Project

Every project MUST have:

1. **Three layouts** (directories):
   - `horizontal/` - Landscape format (wider than tall)
   - `stacked/` - Square-ish format (closer to square ratio)
   - `icon/` - Icon only without project name (square)

2. **Three color versions** (subdirectories):
   - `color/` - Full color version
   - `black/` - Black version
   - `white/` - White version (for dark backgrounds)

3. **Two file formats** in each color directory:
   - PNG format: `[project-name]-[layout]-[color].png`
   - SVG format: `[project-name]-[layout]-[color].svg`

**Example file paths**:
- `projects/prometheus/horizontal/color/prometheus-horizontal-color.png`
- `projects/prometheus/horizontal/color/prometheus-horizontal-color.svg`
- `projects/prometheus/stacked/black/prometheus-stacked-black.png`
- `projects/prometheus/icon/white/prometheus-icon-white.svg`

**Total files per project**: Minimum 18 files (3 layouts × 3 colors × 2 formats)

**Special cases**: Some projects like Kubernetes have additional variations (all-blue-color, white-text).

## File Naming Conventions

**Format**: `[project-name]-[layout]-[color].[extension]`

- Use lowercase project names with hyphens (kebab-case)
- Layout: `horizontal`, `stacked`, or `icon`
- Color: `color`, `black`, or `white`
- Extension: `.png` or `.svg`

**Examples**:
- ✅ `kubernetes-horizontal-color.svg`
- ✅ `open-policy-agent-stacked-black.png`
- ❌ `Kubernetes_Horizontal_Color.svg` (wrong case and separator)
- ❌ `k8s-logo.png` (missing layout and color in name)

## Adding New Project Artwork

When adding a new project to the repository, follow these steps:

### 1. Prepare Artwork Files

- Ensure all 18+ files exist (3 layouts × 3 colors × 2 formats)
- Verify SVGs are true vector files (not embedded rasters)
- **Test and optimize SVGs** at https://autocrop.cncf.io
- Follow exact naming conventions

### 2. Create Directory Structure

```bash
mkdir -p projects/[project-name]/{horizontal,stacked,icon}/{color,black,white}
```

### 3. Place Files in Correct Locations

Organize files according to the standard structure above.

### 4. Update Documentation

**Required updates**:

a. **Add section to appropriate examples/*.md file**:
   - `examples/graduated.md` - For graduated projects
   - `examples/incubating.md` - For incubating projects
   - `examples/sandbox_*.md` - For sandbox projects (alphabetically organized)
   - `examples/other.md` - For CNCF branding/programs

   Add a new section with HTML table showing all logo variations. Follow the format of existing entries.

b. **Update main README.md**:
   - Add link to the new logo section in the appropriate category
   - Maintain alphabetical ordering within each category

### 5. PR Checklist

Before submitting, verify:
- [ ] Artwork supplied in both PNG and SVG formats
- [ ] SVGs are real vector-based files (tested at https://autocrop.cncf.io)
- [ ] Artwork includes 3 layouts: horizontal, stacked, and icon
- [ ] At least 3 versions provided: color, black, and white
- [ ] Files follow existing folder and naming conventions
- [ ] Correct examples/*.md file updated with logo section (A-Z order)
- [ ] Link to new logo section added to main README.md (A-Z order)

## Approval Process

**All PRs require TWO approvals**:
1. One from a CNCF staff member
2. One from the project maintainer whose artwork is being updated

**Note**: Branch protections can be bypassed for PRs made by maintainers.

## Common Tasks

### Moving a Project to Archived

1. Move the project directory from `projects/[name]` to `archived/[name]`
2. Remove the section from the current examples file
3. Add section to `examples/archived.md`
4. Update all links in README.md

### Updating Existing Logos

1. Replace files in the existing directory structure
2. Maintain exact same file names
3. Ensure SVGs remain optimized (test at https://autocrop.cncf.io)
4. Get approval from both CNCF staff and project maintainer

### Adding Project Sub-components

Some projects have sub-projects (e.g., kubernetes/sub-projects/, fluentd with fluentbit).
- Create a `sub-projects/` directory within the main project
- Follow the same structure as main projects
- Update documentation accordingly

## Trademark and Licensing

**Critical**: All artwork is subject to:
- Linux Foundation trademark usage guidelines: https://www.linuxfoundation.org/trademark-usage
- See LICENSE.md for details
- Certified Kubernetes marks require conformance: https://www.cncf.io/certification/software-conformance/

**Key principle**: Usage must be accurate, avoid confusion about CNCF association, and cannot imply CNCF sponsorship or endorsement.

## Tools and Resources

### External Tools
- **SVG Optimization**: https://autocrop.cncf.io - Test and optimize SVG files before submission
- **CNCF Brand Guidelines**: https://www.cncf.io/brand-guidelines/
- **CNCF Style Guide**: https://github.com/cncf/foundation/blob/master/style-guide.md
- **CNCF Store**: https://store.cncf.io/ - Official merchandise

### Verification Commands

```bash
# Verify SVG is true vector (should show "SVG Scalable Vector Graphics")
file projects/[project]/horizontal/color/[project]-horizontal-color.svg

# Count files in a project (should be at least 18)
find projects/[project] -type f | wc -l

# Check file naming consistency
find projects/[project] -type f -name "*.svg" -o -name "*.png" | sort
```

## Image Format Guidelines

### SVG Files
- **Preferred format** for most use cases
- Smaller file sizes than PNG
- High resolution suitable for print and screens
- Supported in all modern browsers
- Must be true vector graphics (not embedded raster images)

### PNG Files
- More universally compatible
- Good for quick embedding in documents
- Larger file sizes than SVG

**Recommendation**: Use SVG when possible, PNG for broader compatibility.

## Documentation Structure

The `examples/` directory contains comprehensive visual documentation:
- Each project has a table showing all logo variations
- Tables use HTML for better layout control in GitHub markdown
- White logos displayed on light grey table backgrounds (markdown limitation)
- Follow exact table format from existing entries

## Common Pitfalls to Avoid

1. **Incorrect file naming**: Must follow exact `[project]-[layout]-[color].[ext]` format
2. **Missing file formats**: Both PNG and SVG required for each variation
3. **Non-vector SVGs**: SVGs with embedded rasters will be rejected
4. **Breaking alphabetical order**: Documentation must maintain A-Z ordering
5. **Forgetting documentation updates**: Both examples/*.md AND README.md must be updated
6. **Wrong examples file**: Ensure graduated/incubating/sandbox projects go in correct file
7. **Incomplete directory structure**: All 9 subdirectories required (3 layouts × 3 colors)
8. **Missing approvals**: Need both CNCF staff and project maintainer approval

## Testing Changes

Since this is a static asset repository:
- No build system to run
- No automated tests to execute
- Manual verification is primary validation method

**Manual verification checklist**:
1. ✅ All files exist in correct locations
2. ✅ File names follow conventions exactly
3. ✅ SVGs are true vector files (check with `file` command)
4. ✅ Documentation renders correctly in markdown preview
5. ✅ Links work correctly
6. ✅ Alphabetical ordering maintained
7. ✅ Images display properly in examples/*.md preview

## Special Project Considerations

### Projects with Multiple Components
- Kubernetes has sub-projects and certified-kubernetes directories
- Envoy has Envoy Gateway as a sub-component
- Fluentd has Fluentbit
- Handle these with sub-directories within the main project

### Brand Variations
- Some projects (e.g., Kubernetes) have special color variations beyond standard color/black/white
- Document these clearly in the project's README.md
- Maintain consistency with standard naming patterns

## GitHub Workflow

This repository uses:
- Pull request template in `.github/pull_request_template.md`
- Standard GitHub PR review process
- No CI/CD pipelines or automated checks
- Manual review by CNCF staff and project maintainers

## Getting Help

- **Questions about trademark usage**: info@cncf.io
- **Brand guidelines**: https://www.cncf.io/brand-guidelines/
- **Style guide for text**: https://github.com/cncf/foundation/blob/master/style-guide.md

## Quick Reference: Adding a New Project

```bash
# 1. Create directory structure
mkdir -p projects/newproject/{horizontal,stacked,icon}/{color,black,white}

# 2. Add files (18 minimum)
# - 6 files in horizontal/ (color, black, white × PNG, SVG)
# - 6 files in stacked/ (color, black, white × PNG, SVG)
# - 6 files in icon/ (color, black, white × PNG, SVG)

# 3. Verify SVGs
file projects/newproject/horizontal/color/newproject-horizontal-color.svg

# 4. Update documentation
# - Add section to appropriate examples/*.md
# - Add link in README.md
# - Maintain A-Z order

# 5. Submit PR with checklist from pull_request_template.md
```

## Summary

This repository is a carefully organized collection of CNCF project artwork with strict conventions. Success requires:
- **Precision**: Exact adherence to naming and structure conventions
- **Completeness**: All required files, formats, and documentation
- **Quality**: Vector-based SVGs, optimized files
- **Process**: Proper approvals from CNCF staff and project maintainers

The repository prioritizes consistency and maintainability to serve the cloud native community with high-quality, properly licensed artwork assets.

# Copilot Instructions for Architecture/ADU Design Portfolio

## Project Overview
**PRIMARY GOAL**: Transform the Minimal Mistakes Jekyll theme into a professional architecture/data engineering portfolio website for a husband-wife team specializing in:
- Home remodels (interior/exterior)
- ADU (Accessory Dwelling Unit) design for rental income
- Cost estimation & ROI visualization dashboards

**DESIGN INSPIRATION**: https://big.dk/ (Bjarke Ingels Group) - photography-first, minimalist grids, project metadata, clean typography.

**TARGET MARKET**: California homeowners and small businesses seeking professional design with transparent financial projections.

**EXISTING CODEBASE**: Minimal Mistakes Jekyll theme with:
- Core theme files (`_includes/`, `_layouts/`, `_sass/`)
- Documentation site (`docs/`) built with the theme itself
- Test site (`test/`) for development and validation
- Theme gem (`minimal-mistakes-jekyll.gemspec`)

## Architecture & Data Flow

### New Collections (TO BE CREATED)
- **`_projects/`**: Portfolio projects (remodels, ADUs, transformations)
- **`_case_studies/`**: Detailed before/after narratives with financial breakdown
- **`_team/`**: Team member profiles with credentials (architect + data engineer)

### New Layouts (TO BE CREATED)
- **`home-portfolio.html`**: Hero-driven homepage with featured projects showcase
- **`project-single.html`**: Rich project detail with gallery, ROI breakdown, testimonial, before/after slider
- **`services.html`**: Service category showcase (Remodels, ADU Design, Dashboards)
- **`about.html`**: Team member bios showing complementary expertise
- **`dashboard.html`**: Interactive cost calculators and ROI tools

### New Pages (TO BE CREATED)
- **`services/`**: Services landing and sub-pages (remodels.md, adu-design.md, dashboards.md)
- **`projects/`**: Full project grid with filtering/search
- **`about/`**: Team story and process
- **`contact/`**: Contact form

### New Components (TO BE CREATED)
- **Before/After Image Slider**: Interactive project transformation comparison (JavaScript)
- **ROI Calculator**: Interactive "What if" scenarios for ADU investment decisions
- **Project Gallery**: Lightbox for viewing full-resolution project images
- **Testimonial Carousel**: Client reviews with photos and attribution
- **Service Cards**: Preview cards for main service offerings

### Existing Directory Structure
- **`_includes/`**: Reusable HTML components and modular partials (masthead, footer, sidebar, etc.)
- **`_layouts/`**: Page templates (default, single, home, archive, splash, collection)
- **`_sass/`**: SCSS files organized by component (`_masthead.scss`, `_sidebar.scss`, etc.)
- **`assets/`**: CSS (compiled), JavaScript, images
- **`_data/`**: YAML configuration files (`navigation.yml`, `ui-text.yml`)
- **`docs/`**: Full documentation site (keep as reference)
- **`test/`**: Minimal test site (keep for validation)

### Key Configuration Files
- **`_config.yml`**: Root site configuration (excluded from builds; mostly placeholder)
- **`docs/_config.yml`**: Demo site configuration with collection definitions and defaults
- **`test/_config.yml`**: Test site configuration
- **`minimal-mistakes-jekyll.gemspec`**: Gem specification; uses `git ls-files` to package theme

### Collections Pattern
Collections are registered in `_config.yml` with output and permalink settings:
```yaml
collections:
  projects:
    output: true
    permalink: /:collection/:path/
  case_studies:
    output: true
    permalink: /case-studies/:path/
```

Front Matter defaults are set per collection type to control layout, sidebar, and sharing options.

### Project Front Matter Example
Each project should capture:
```yaml
---
title: "Modern ADU Conversion - Oakland, CA"
layout: project-single
typology: "ADU Design"
location: "Oakland, CA"
year: 2024
status: "completed"
budget: "$180,000"
roi_increase: "31%"
monthly_rental: "$2,400"
investment_payback_years: 6.25
categories: [adu, residential]
hero_image: /images/projects/oakland-hero.jpg
before_after:
  - before: /images/projects/oakland-before.jpg
    after: /images/projects/oakland-after.jpg
services: ["3D Design", "Cost Analysis", "ROI Dashboard", "Permit Support"]
testimonial:
  quote: "Within 6 months, the ADU generated positive cash flow..."
  author: "John & Sarah Martinez"
  image: /images/testimonials/martinez.jpg
---
```

## Build & Development Workflow

### Building & Previewing
- **`rake preview`**: Watches `_data/`, `_includes/`, `_layouts/`, `_sass/`, and test site; rebuilds on changes
- **Direct Jekyll**: `jekyll serve --source test --destination test/_site`
- **Build only**: `jekyll build --source test --destination test/_site`

### Rake Tasks
- **`rake default`**: Runs copyright, changelog, JavaScript minification, and version updates
- **`rake changelog`**: Generates changelog documentation
- **`rake copyright`**: Manages copyright headers

### Key Build Details
- **Theme gem building**: Spec file includes only theme assets/layouts/data; docs and test dirs excluded
- **jekyll-include-cache plugin**: Required; avoids `Unknown tag 'include_cached'` errors
- **Sass output**: Compressed (`style: compressed`)
- **Markdown**: Kramdown with GFM input; syntax highlighting via Rouge

## Conventions & Patterns

### Design Approach (Big.dk-Inspired)
- **Photography-First**: Large, bold project images dominate
- **Minimal Text**: Let imagery tell the story; copy is concise and impactful
- **Generous Whitespace**: Airy layouts with 3-4rem vertical spacing between sections
- **Typography**: Clean sans-serif (Inter or system stack), large headings (1.5-2.5rem)
- **Color Palette**: Deep charcoal primary, white backgrounds, warm accent for highlights
- **Project Metadata**: Visible tags showing typology, location, status, financials

### Homepage Structure
1. Full-height hero section with stunning project image + text overlay
2. Featured projects carousel (3-6 projects)
3. Services preview cards (Remodels, ADU Design, Dashboards)
4. "How It Works" process section
5. Client testimonials
6. CTA to projects/contact

### Project Detail Page Structure
1. Full-width hero image
2. Project metadata sidebar (status, location, budget, timeline, ROI)
3. Before/After interactive slider
4. Full project gallery (8-12 images with captions)
5. Design highlights section
6. Financial breakdown with ROI dashboard/chart
7. Services used
8. Client testimonial with photo
9. Related projects carousel
10. Strong CTA ("Start Your Project")

### Service Pages
- Hero section with service-specific image
- Overview and value proposition
- 3-5 example projects or case studies
- Features/benefits checklist
- Interactive tool (calculator, estimator, comparison)
- Pricing or ROI breakdown
- Client testimonials specific to that service
- Contact CTA

### Layout Hierarchy
- **`default.html`**: Base layout with skip-links, masthead, footer
- **`single.html`**: Post/page layout with sidebar and related content
- **`home-portfolio.html`**: Photography-focused homepage with featured projects
- **`project-single.html`**: Project detail with rich media, galleries, ROI data
- **`services.html`**: Service category showcase
- **`about.html`**: Team/process page
- **`dashboard.html`**: Interactive calculator tools
- **`collection.html`**: Generic collection document layout

### Front Matter Defaults
Front Matter defaults vary by type:
- **Posts**: `author_profile: true`, `read_time: true`, `comments: true`, `related: true`
- **Projects**: `author_profile: false`, `read_time: false`, `share: true`
- **Services**: `author_profile: false`, `comments: false`

### SCSS Architecture
- **`minimal-mistakes.scss`**: Main entry point
- **`_variables.scss`**: Theme colors, fonts, breakpoints
- **`_mixins.scss`**: Responsive and utility mixins
- **`skins/`**: Color theme variations (air, aqua, contrast, dark, etc.)

## Critical Patterns & Edge Cases

### Theme Customization
- Custom skin file overrides `_variables.scss` for color/typography
- New layouts extend `default.html` for consistent structure
- JavaScript components are organized in `assets/js/_*.js` files
- Include files are modular—create new includes for reusable components

### Custom Components for This Project
- **Before/After Slider**: Interactive image comparison with mouse/touch support
- **ROI Calculator**: Form with real-time calculation and result display
- **Project Gallery**: Lightbox integration for high-resolution images
- **Testimonial Carousel**: Auto-rotate or manual navigation
- **Service Cards**: Hover effects, image overlays, CTA buttons

### Financial Data Visualization
- Use Chart.js or Plotly for ROI charts and graphs
- Display key metrics prominently (investment, payback period, annual returns)
- Show property value increase vs. investment spent
- Calculate break-even analysis for ADU projects

### Project Filtering & Search
- Filter by: Typology (Remodel/ADU), Location, Status, Year
- Search by: Project name, location, service type
- Consider Lunr.js for client-side search (lightweight)

## Common Tasks

### Adding a New Skin
1. Create `_sass/minimal-mistakes/skins/_newname.scss`
2. Define color variables: `$primary-color`, `$border-color`, etc.
3. Update documentation references

### Modifying Core Includes
- Edit `_includes/*.html` directly
- Cached includes (`masthead`, `footer`) impact performance; test with `rake preview`
- Custom hooks (`_includes/head/custom.html`) allow users to override without forking

### Documentation Updates
- Source: `docs/_docs/` (Jekyll collection)
- Uses sidebar navigation from `docs/_data/navigation.yml`
- Default layout: `single` with `toc_sticky: true`

## Testing & Quality

- **Theme validation**: Use `test/` directory with test `_config.yml`
- **Preview command**: `rake preview` auto-rebuilds on file changes
- **Ruby/Bundler**: Dependencies defined in `Gemfile`; run `bundle install` after gem updates

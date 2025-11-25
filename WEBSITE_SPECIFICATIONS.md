# Minimal Mistakes Theme Customization for Architecture/ADU Design Portfolio

## Project Overview
Transform the Minimal Mistakes Jekyll theme into a professional portfolio website for an architect/data engineer couple specializing in home remodels, ADU (Accessory Dwelling Unit) design, and financial ROI visualization.

## Design Reference
This project is inspired by **https://big.dk/** (Bjarke Ingels Group) - emphasizing:
- Photography-first design approach
- Minimalist grid layouts
- Project metadata visibility
- Large-format imagery
- Clean, modern typography

## Business Focus
**Three Core Service Areas:**
1. **Home Remodels** - Interior/exterior renovation projects
2. **ADU Design** - Accessory dwelling units for rental income
3. **Cost & ROI Dashboards** - Data-driven project visualization

**Target Market:** California homeowners and small businesses seeking professional design with transparent financial projections.

---

## Key Architecture Modifications

### 1. **New Collections**
- `_projects/` - Portfolio projects (remodels, ADUs, case studies)
- `_case_studies/` - Detailed before/after narratives with financial data

### 2. **New Layouts**
- `home-portfolio.html` - Hero-driven homepage with featured projects
- `project-single.html` - Rich project detail with gallery, ROI breakdown, testimonial
- `services.html` - Service category showcase
- `about.html` - Team member bios with complementary expertise
- `dashboard.html` - Interactive cost calculators and ROI tools

### 3. **New Pages**
- `/services/` - Main services landing (remodels, ADUs, dashboards)
- `/projects/` - Full project grid with filtering
- `/about/` - Team story and process
- `/contact/` - Contact form

### 4. **Custom Components**
- **Before/After Slider** - Interactive project transformation comparison
- **ROI Calculator** - "What if" scenarios for ADU investment
- **Project Gallery** - Lightbox for project imagery
- **Testimonial Carousel** - Client reviews with photos

### 5. **Custom Styling** 
- New skin: `_sass/minimal-mistakes/skins/_architecture.scss`
- Deep charcoal (#1a1a1a) primary with warm accent (#d4a373)
- Large photography-focused project cards
- Generous whitespace following Big.dk aesthetic
- Modern sans-serif typography (Inter or system fonts)

---

## File Structure
```
/
├── _config.yml                          # Update with collections & defaults
├── _sass/minimal-mistakes/skins/
│   └── _architecture.scss               # NEW: Custom color scheme
├── _includes/
│   ├── project-gallery.html             # NEW: Lightbox gallery
│   ├── before-after-slider.html         # NEW: Image comparison
│   ├── roi-calculator.html              # NEW: Interactive calculator
│   ├── service-card.html                # NEW: Service preview card
│   └── testimonial.html                 # NEW: Client quote with photo
├── _layouts/
│   ├── home-portfolio.html              # NEW: Photography-focused home
│   ├── project-single.html              # NEW: Project detail page
│   ├── services.html                    # NEW: Service category
│   ├── about.html                       # NEW: Team page
│   └── dashboard.html                   # NEW: Calculator/tools
├── _pages/
│   ├── services.md                      # NEW
│   ├── projects.md                      # NEW
│   ├── about.md                         # NEW
│   ├── contact.md                       # NEW
│   └── services/
│       ├── remodels.md                  # NEW
│       ├── adu-design.md                # NEW
│       └── dashboards.md                # NEW
├── _projects/                           # NEW: Project collection
│   ├── 2024-01-modern-kitchen.md
│   ├── 2024-01-studio-adu.md
│   └── ... (15-20 examples)
├── assets/js/
│   ├── _before-after-slider.js          # NEW: Image slider logic
│   ├── _roi-calculator.js               # NEW: Calculator logic
│   └── _project-filter.js               # NEW: Filter/search projects
└── DESIGN_STRATEGY.md                   # NEW: Full specification
```

---

## Content Strategy

### Homepage (Hero-Driven)
```
┌─────────────────────────────────────────┐
│  Full-height hero with stunning project │
│  image + overlay text                   │
│                                         │
│  "Smart Remodels & ADU Design"         │
│  "Where Architecture Meets Data"       │
│                                         │
│  [View Our Work Button]                 │
└─────────────────────────────────────────┘

Featured Projects (3-item carousel or grid)
┌─────────┬─────────┬─────────┐
│Project 1│Project 2│Project 3│
└─────────┴─────────┴─────────┘

Services Preview (3 cards)
┌──────────┬───────────┬──────────┐
│ Remodels │ ADU Design│Dashboards│
└──────────┴───────────┴──────────┘

How It Works (4-step process)
```

### Projects Grid
```
Masonry/grid layout showing:
- Large project image (hero photo)
- Project overlay on hover:
  - Title
  - Typology (Remodel / ADU / Dashboard)
  - Location
  - Status (Completed / In Progress)
```

### Project Detail Page
```
┌────────────────────────────────┐
│ Full-width hero image          │
└────────────────────────────────┘

│ PROJECT METADATA SIDEBAR:      │
│ • Status: Completed            │
│ • Location: Oakland, CA        │
│ • Year: 2024                   │
│ • Budget: $180K                │
│ • ROI: +31% annually           │
└────────────────────────────────┘

│ BEFORE & AFTER SLIDER          │
│ [Interactive image comparison] │
└────────────────────────────────┘

│ PROJECT GALLERY                │
│ [Lightbox with 10-15 images]   │
└────────────────────────────────┘

│ DESIGN HIGHLIGHTS              │
│ - Feature 1                    │
│ - Feature 2                    │
│ - Feature 3                    │
└────────────────────────────────┘

│ FINANCIAL BREAKDOWN            │
│ [ROI Dashboard with charts]    │
│ Investment: $180K              │
│ Monthly Rental: $2,400         │
│ Payback Period: 6.25 years    │
└────────────────────────────────┘

│ CLIENT TESTIMONIAL             │
│ "Within 6 months..."           │
│ — John & Sarah Martinez        │
└────────────────────────────────┘

│ RELATED PROJECTS CAROUSEL      │
└────────────────────────────────┘
```

### ADU Service Page
```
Hero + Description
3-4 ADU project case studies
ADU ROI Calculator (interactive)
Features/Benefits list
Regulations by state/county
Financing options
Contact CTA
```

### Dashboard/Tools Page
```
ROI Calculator:
  • Initial Investment
  • Expected Monthly Rental
  • Holding Period
  → Shows: Total Income, Net Profit, Annual ROI

Cost Estimator:
  • Project Type (Kitchen / Bathroom / Full Remodel / ADU)
  • Square Footage
  • Style/Features
  → Shows: Estimated Budget Range

Before/After Comparison:
  • Photo selection
  • Interactive slider
  • Transformation narrative
```

---

## Development Checklist

### Phase 1: Foundation
- [ ] Create `_architecture.scss` skin
- [ ] Update `_config.yml` with new collections
- [ ] Create homepage template (`home-portfolio.html`)
- [ ] Create project collection structure
- [ ] Design project detail layout (`project-single.html`)
- [ ] Set up services layout

### Phase 2: Components
- [ ] Implement before/after slider JavaScript
- [ ] Build ROI calculator (HTML + JS)
- [ ] Create project gallery lightbox
- [ ] Add project filtering capability
- [ ] Build testimonial carousel

### Phase 3: Content
- [ ] Create 15-20 sample projects
- [ ] Write service descriptions
- [ ] Add team member profiles
- [ ] Gather/create project photography
- [ ] Write client testimonials (or create examples)
- [ ] Create case study narratives

### Phase 4: Refinement
- [ ] Optimize images for web
- [ ] Test responsive design (mobile, tablet, desktop)
- [ ] Implement SEO enhancements
- [ ] Add analytics tracking
- [ ] Performance testing
- [ ] Accessibility audit

---

## Key Design Decisions

### Typography
- **Primary Font**: Inter or system stack (Clean, modern, excellent readability)
- **Scale**: 16px base, 1.6 line height (generous, airy)
- **Hierarchy**: Large headings, generous spacing mimicking Big.dk

### Color Palette
- **Primary**: #1a1a1a (Deep charcoal, elegant)
- **Secondary**: #ffffff (Clean white backgrounds)
- **Border**: #e8e8e8 (Light gray dividers)
- **Accent**: #d4a373 (Warm gold for highlights - optional)
- **Success**: #2ecc71 (Green for ROI gains)

### Imagery
- **Photography-First**: Large, bold project images
- **Aspect Ratios**: Consistent 4:3 for project cards, full-width for details
- **Optimization**: WebP with fallbacks, lazy loading
- **Style**: Professional architectural photography, well-lit spaces

### Spacing
- **Large gaps between sections**: 3-4rem vertical rhythm
- **Generous padding**: Project cards, content areas
- **Whitespace**: Mimics luxury/premium feel

### Interactive Elements
- **Hover states**: Subtle scale transforms on cards
- **Sliders**: Smooth, intuitive interactions
- **Calculators**: Real-time results with clear visual feedback
- **CTAs**: Bold, prominent, action-oriented

---

## Integration with Minimal Mistakes

### What to Keep
- `_includes/masthead.html` - Navigation structure (customize styling)
- `_includes/footer.html` - Footer framework
- `_includes/seo.html` - SEO optimization
- `_sass/minimal-mistakes/_variables.scss` - Base variables (override as needed)
- `assets/css/main.css` - Compiled CSS (will extend)
- Jekyll plugins: `jekyll-paginate`, `jekyll-sitemap`, `jekyll-feed`

### What to Override
- `_sass/minimal-mistakes/skins/` - Add new `_architecture.scss`
- `_layouts/default.html` - Keep base, override specific sections
- `_includes/masthead.html` - Customize navigation styling
- Color variables in `_variables.scss` - Set new palette

### What to Add
- All new layouts, pages, components listed above
- New JavaScript files for interactive features
- New image assets for projects and team

---

## Example Project Front Matter

```yaml
---
title: "Modern Kitchen Remodel - Rockridge, Oakland"
layout: project-single
author: "Jane & John Doe Team"
date: 2024-01-15

# Project Details
typology: "Kitchen Remodel"
category: "Residential Remodel"
location: "Rockridge, Oakland, CA"
year: 2024
status: "Completed"
timeline: "4 months"

# Financial Data
investment: 185000
monthly_rental: null
annual_savings: 3200  # Energy efficiency
property_value_increase: 42000
roi_percent: 22.7

# Visual Assets
hero_image: "/assets/images/projects/rockridge-kitchen-hero.jpg"
featured_image: "/assets/images/projects/rockridge-kitchen-thumb.jpg"

# Before & After
before_after:
  - before: "/assets/images/projects/rockridge-before-01.jpg"
    after: "/assets/images/projects/rockridge-after-01.jpg"
    caption: "Kitchen renovation"

# Project Images
images:
  - image: "/assets/images/projects/rockridge-01.jpg"
    caption: "New custom cabinetry"
  - image: "/assets/images/projects/rockridge-02.jpg"
    caption: "Quartz countertops with waterfall edge"
  - image: "/assets/images/projects/rockridge-03.jpg"
    caption: "Energy-efficient appliances"

# Services Used
services:
  - "3D Visualization"
  - "Material Selection"
  - "Cost Estimation"
  - "Timeline Planning"

# Client Testimonial
testimonial:
  quote: "Jane's design vision combined with the ROI projections made this decision easy. Our kitchen is beautiful AND it's already paying for itself in energy savings."
  author: "The Martinez Family"
  image: "/assets/images/testimonials/martinez.jpg"

# Meta
excerpt: "Complete kitchen transformation with modern fixtures, custom cabinetry, and sustainable materials. 22.7% ROI through energy efficiency and market appeal."
---
```

---

## Success Metrics

| Metric | Target | Purpose |
|--------|--------|---------|
| Time to project details | < 3 clicks | Navigation efficiency |
| Mobile usability score | 90+ | Mobile experience |
| PageSpeed Insights | 85+ (Core Web Vitals) | Performance |
| Project load time | < 2s | Fast experience |
| ROI calculator usage | 20%+ of visitors | Tool engagement |
| Contact form conversion | 5%+ of project viewers | Lead generation |
| Return visitor rate | 30%+ | Sticky content |
| Gallery images per project | 8-12 | Rich content |

---

## Dependencies & Tools

**Required Jekyll Plugins** (already in Minimal Mistakes):
- jekyll-paginate
- jekyll-sitemap
- jekyll-feed
- jekyll-include-cache

**Optional Enhancements**:
- Before/After slider library (custom JS or lightweight library like `twentytwenty.js`)
- Chart.js (for ROI visualizations)
- Lightbox library (fancybox or custom)

---

## Maintenance & Content Calendar

**Weekly**:
- Monitor contact form submissions
- Update project status if in-progress work

**Monthly**:
- Review analytics
- Publish case study or design tips
- Update ROI calculator assumptions if rates change

**Quarterly**:
- Add 1-2 new completed projects
- Review and refresh testimonials
- Update team bios/credentials

**Annually**:
- Comprehensive content audit
- Redesign refresh (minor CSS updates)
- SEO optimization review

---

## Questions & Next Steps

1. **Business Name**: What should we call the venture?
2. **Geographic Focus**: California, specific regions, or national?
3. **Pricing Model**: Hourly, project-based, or subscription for dashboards?
4. **Existing Content**: Do you have project photos/descriptions ready?
5. **Timeline**: When should this go live?
6. **Team Photos**: Professional photos for team bios?
7. **Analytics Goals**: What KPIs matter most?

---

**Document Version**: 1.0  
**Created**: November 2024  
**Status**: Ready for Phase 1 Development  
**Estimated Timeline**: 6-8 weeks to full launch

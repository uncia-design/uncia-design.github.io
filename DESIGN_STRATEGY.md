# Design Strategy: Transforming Minimal Mistakes to Big.dk-Inspired Architecture Website

## Executive Summary
This document outlines the transformation of the Minimal Mistakes Jekyll theme into a professional architecture/data engineering portfolio website, inspired by the design aesthetics and user experience of Big.dk (Bjarke Ingels Group's website).

**Target Users:** Homeowners and small businesses seeking remodels, ADU (Accessory Dwelling Unit) designs, and ROI/cost visualization dashboards.

**Core Team:** Husband-wife team - 1 Architect + 1 Data Engineer

---

## Big.dk Design Analysis

### Visual Characteristics
- **Hero Pattern**: Large-format project photography with minimal text overlay
- **Typography**: Clean, sans-serif, generous whitespace
- **Color Palette**: Primarily black, white, grays with minimal accent color
- **Grid System**: Masonry-style project grid with metadata tags (TYPOLOGY, STATUS, SIZE)
- **Navigation**: Sticky top nav, minimal visual hierarchy, emphasis on projects
- **Imagery**: Photography-first approach, bold compositions, consistent aspect ratios

### User Experience Flow
1. **Hero Section**: Immediate project showcase
2. **Project Grid**: Filterable by category (typology), searchable
3. **Project Detail Pages**: Rich imagery, project metadata, client info, sharing options
4. **Team/About**: Minimal bios with professional credibility

### Key Differentiators for This Project
- **Add financial visualization**: Cost estimation dashboards
- **Add ROI calculator**: Data-driven decision tools
- **Add before/after galleries**: Transformation documentation
- **Emphasize ADU expertise**: Dedicated section with case studies
- **Team positioning**: Show complementary skillsets (design + data)

---

## Recommended Modifications to Minimal Mistakes

### 1. Homepage Redesign

**Current State**: Blog-focused post listing
**Target**: Project-focused portfolio hero with immediate portfolio showcase

```yaml
layout: home-portfolio
hero:
  title: "Smart Remodels & ADU Design"
  subtitle: "Where Architecture Meets Data-Driven ROI"
  cta: "View Our Work"
  background_image: path/to/hero.jpg
featured_projects: 3
services_preview: true
```

**Changes Required**:
- Create new `_layouts/home-portfolio.html` (replacing current home.html usage)
- Add hero section with background image, centered text overlay
- Feature 3-6 recent/featured projects in grid
- Add "Services" preview cards
- Add "How It Works" explainer section

### 2. Portfolio/Projects Collection

**Create new collection**: `_projects/`

```yaml
# _config.yml additions
collections:
  projects:
    output: true
    permalink: /:collection/:path/
  case_studies:
    output: true
    permalink: /case-studies/:path/
```

**Project Front Matter**:
```yaml
---
title: "Eastside Remodel - Berkeley, CA"
layout: project-single
typology: "Residential Remodel"
status: "completed"
location: "Berkeley, CA"
year: 2023
budget: "$450,000"
roi_increase: "23%"
rental_ready: true
categories: [remodel, residential]
images:
  - path: /images/projects/eastside-before.jpg
    caption: "Before"
  - path: /images/projects/eastside-after.jpg
    caption: "After"
gallery:
  - image: /images/projects/eastside-01.jpg
  - image: /images/projects/eastside-02.jpg
---
```

### 3. New Layouts Needed

#### a. `_layouts/project-single.html`
- Large hero image (project's primary photo)
- Project metadata sidebar (typology, status, location, budget, timeline)
- Before/After slider component
- Full project gallery (lightbox)
- ROI/Financial breakdown visualization
- Services used section
- CTA: "Start Your Project"
- Related projects carousel

#### b. `_layouts/services.html`
- Hero section
- 3-4 main service cards (full width with imagery)
- Detailed descriptions
- Features checklist
- Client testimonials for each service
- Pricing or estimation tools

#### c. `_layouts/about.html`
- Team member profiles with photos
- Credentials and specialties
- How they work together
- Process overview
- Why hire them (value proposition)

#### d. `_layouts/dashboard.html`
- Interactive cost calculator
- ROI estimation tool
- Before/after photo comparison slider
- Project timeline visualization

### 4. New Pages to Create

```
_pages/
├── services.md              # Main services landing
├── services/
│   ├── remodels.md         # Interior/exterior remodels
│   ├── adu-design.md       # ADU specialist page
│   └── cost-analysis.md    # Dashboard & ROI tools
├── about.md                # Team story
├── projects.md             # Projects grid/filter
├── contact.md              # Contact form
└── testimonials.md         # Client reviews

_projects/
├── 2024-modern-kitchen.md
├── 2023-studio-adu.md
├── 2024-backyard-remodel.md
└── ... (20-30 examples)
```

### 5. Styling Approach

#### New Skin: `_sass/minimal-mistakes/skins/_architecture.scss`

Key colors:
```scss
$primary-color: #1a1a1a;              // Deep charcoal
$secondary-color: #ffffff;             // Clean white
$border-color: #e8e8e8;               // Light gray
$accent-color: #d4a373;               // Warm accent (optional)
$success-color: #2ecc71;              // For ROI indicators

$font-family-sans-serif: "Inter", -apple-system, BlinkMacSystemFont, "Segoe UI", "Helvetica Neue", sans-serif;
$base-font-size: 16px;
$line-height-computed: 1.6;
```

#### Custom Component Styles

```scss
// Project grid
.projects-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(400px, 1fr));
  gap: 2rem;
  
  .project-card {
    position: relative;
    overflow: hidden;
    aspect-ratio: 4 / 3;
    
    img {
      width: 100%;
      height: 100%;
      object-fit: cover;
      transition: transform 0.3s ease;
    }
    
    &:hover img {
      transform: scale(1.05);
    }
    
    .project-meta {
      position: absolute;
      bottom: 0;
      left: 0;
      right: 0;
      background: linear-gradient(transparent, rgba(0,0,0,0.8));
      color: white;
      padding: 2rem 1.5rem;
      
      .typology {
        font-size: 0.875rem;
        text-transform: uppercase;
        opacity: 0.8;
      }
      
      .title {
        font-size: 1.5rem;
        font-weight: 600;
        margin-top: 0.5rem;
      }
    }
  }
}

// Before/After Slider
.before-after-slider {
  position: relative;
  max-width: 100%;
  overflow: hidden;
  
  .before-image,
  .after-image {
    display: block;
    width: 100%;
  }
  
  .before-label,
  .after-label {
    position: absolute;
    top: 1rem;
    background: rgba(0,0,0,0.6);
    color: white;
    padding: 0.5rem 1rem;
    font-size: 0.875rem;
    text-transform: uppercase;
    font-weight: 600;
  }
  
  .before-label { left: 1rem; }
  .after-label { right: 1rem; }
  
  .slider-handle {
    position: absolute;
    top: 0;
    left: 50%;
    width: 2px;
    height: 100%;
    background: white;
    cursor: ew-resize;
    
    &::before {
      content: '';
      position: absolute;
      top: 50%;
      left: 50%;
      transform: translate(-50%, -50%);
      width: 40px;
      height: 40px;
      background: white;
      border-radius: 50%;
      box-shadow: 0 2px 8px rgba(0,0,0,0.3);
    }
  }
}

// ROI Dashboard
.roi-calculator {
  background: $border-color;
  padding: 2rem;
  border-radius: 8px;
  
  .input-group {
    margin-bottom: 1.5rem;
    
    label {
      display: block;
      margin-bottom: 0.5rem;
      font-weight: 600;
    }
    
    input {
      width: 100%;
      padding: 0.75rem;
      border: 1px solid $border-color;
      border-radius: 4px;
      font-size: 1rem;
    }
  }
  
  .results {
    margin-top: 2rem;
    padding-top: 2rem;
    border-top: 2px solid $primary-color;
    
    .result-item {
      display: flex;
      justify-content: space-between;
      margin-bottom: 1rem;
      font-size: 1.125rem;
      
      .label { font-weight: 600; }
      .value {
        font-weight: 700;
        color: $success-color;
      }
    }
  }
}

// Service Cards
.services-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 3rem;
  margin: 3rem 0;
  
  .service-card {
    .service-image {
      width: 100%;
      height: 250px;
      object-fit: cover;
      border-radius: 8px;
      margin-bottom: 1.5rem;
    }
    
    h3 {
      font-size: 1.5rem;
      margin-bottom: 1rem;
    }
    
    .features {
      list-style: none;
      margin: 1.5rem 0;
      
      li {
        padding-left: 1.5rem;
        margin-bottom: 0.75rem;
        position: relative;
        
        &::before {
          content: '✓';
          position: absolute;
          left: 0;
          color: $success-color;
          font-weight: bold;
        }
      }
    }
  }
}
```

### 6. JavaScript Components Needed

#### a. Before/After Slider (`assets/js/_before-after-slider.js`)
```javascript
class BeforeAfterSlider {
  constructor(element) {
    this.slider = element;
    this.handle = element.querySelector('.slider-handle');
    this.before = element.querySelector('.before-image');
    this.isDragging = false;
    
    this.handle.addEventListener('mousedown', () => this.isDragging = true);
    document.addEventListener('mouseup', () => this.isDragging = false);
    document.addEventListener('mousemove', (e) => this.handleMove(e));
  }
  
  handleMove(e) {
    if (!this.isDragging) return;
    
    const rect = this.slider.getBoundingClientRect();
    const x = e.clientX - rect.left;
    const percentage = (x / rect.width) * 100;
    
    this.before.style.width = percentage + '%';
    this.handle.style.left = percentage + '%';
  }
}

document.querySelectorAll('.before-after-slider').forEach(el => {
  new BeforeAfterSlider(el);
});
```

#### b. ROI Calculator (`assets/js/_roi-calculator.js`)
```javascript
class ROICalculator {
  constructor(element) {
    this.form = element.querySelector('form');
    this.results = element.querySelector('.results');
    this.inputs = this.form.querySelectorAll('input');
    
    this.inputs.forEach(input => {
      input.addEventListener('change', () => this.calculate());
    });
  }
  
  calculate() {
    const investment = parseFloat(document.getElementById('investment').value) || 0;
    const rentalIncome = parseFloat(document.getElementById('rental-income').value) || 0;
    const yearsToROI = parseInt(document.getElementById('years').value) || 1;
    
    const totalIncome = rentalIncome * 12 * yearsToROI;
    const roiPercent = ((totalIncome - investment) / investment * 100).toFixed(1);
    
    this.updateResults({
      totalIncome: totalIncome.toLocaleString('en-US', {
        style: 'currency',
        currency: 'USD',
        minimumFractionDigits: 0
      }),
      roiPercent: roiPercent + '%',
      roi: Math.max(0, totalIncome - investment).toLocaleString('en-US', {
        style: 'currency',
        currency: 'USD',
        minimumFractionDigits: 0
      })
    });
  }
  
  updateResults(data) {
    // Update result display elements
  }
}

document.querySelectorAll('.roi-calculator').forEach(el => {
  new ROICalculator(el);
});
```

### 7. Data Structure Example

**Front Matter defaults** in `_config.yml`:
```yaml
defaults:
  # Projects
  - scope:
      path: ""
      type: projects
    values:
      layout: project-single
      author_profile: false
      read_time: false
      comments: false
      share: true
      related: true
  # Case Studies
  - scope:
      path: ""
      type: case_studies
    values:
      layout: case-study-single
      author_profile: false
      comments: false
      share: true
```

---

## Implementation Roadmap

### Phase 1: Foundation (Week 1-2)
- [ ] Create new skin (`_architecture.scss`)
- [ ] Design homepage template (`home-portfolio.html`)
- [ ] Set up collections (projects, case_studies)
- [ ] Create basic project and services layouts
- [ ] Update copilot instructions

### Phase 2: Core Features (Week 3-4)
- [ ] Build project detail page with gallery
- [ ] Implement before/after slider
- [ ] Create services pages
- [ ] Build about/team page
- [ ] Add ROI calculator

### Phase 3: Content & Polish (Week 5-6)
- [ ] Create 15-20 example projects
- [ ] Add team member profiles
- [ ] Create service detail pages
- [ ] Add testimonials
- [ ] Test responsiveness

### Phase 4: Enhanced Features (Optional)
- [ ] Add project filtering/search
- [ ] Implement contact form with email integration
- [ ] Add blog for design tips
- [ ] Create downloadable guides (ADU checklist, ROI templates)
- [ ] Add appointment booking integration

---

## Content Strategy

### Project Showcase Structure
Each project should highlight:
1. **Before/After imagery**: Primary visual impact
2. **Key metrics**: Budget, timeline, square footage, ROI
3. **Challenges & solutions**: Design narrative
4. **Services provided**: Remodel, ADU, dashboard, etc.
5. **Client testimonial**: Social proof
6. **Financial impact**: How ADU increased property value, rental income

### Sample Project Template
```markdown
---
title: Modern ADU Conversion - Oakland
typology: ADU Design
location: Oakland, CA
status: completed
year: 2024
budget: "$180,000"
roi_increase: "31%"
monthly_rental: "$2,400"
images:
  hero: /images/projects/oakland-hero.jpg
---

## Project Overview
This Victorian backyard was transformed into a contemporary ADU...

## Before & After
![Before/After comparison slider]

## Design Highlights
- Passive solar orientation
- Flexible use space (studio + additional room)
- Low-maintenance xeriscaping

## Financial Breakdown
[ROI Dashboard/Chart]
- Initial investment: $180K
- Monthly rental income: $2,400
- ROI: 31% annually

## Client Testimonial
> "Within 6 months, we completely paid for the ADU..."
— John & Sarah Martinez
```

---

## Technical Considerations

### Performance
- Lazy load project images
- Optimize hero images (use WebP with fallbacks)
- Minify CSS/JS
- Consider image CDN for fast delivery

### SEO
- Add schema.org markup for projects and organization
- Meta descriptions for each project
- Open Graph tags with project imagery
- Sitemap.xml (auto-generated by jekyll-sitemap)

### Analytics
- Track popular projects (which types convert best)
- Track calculator usage
- Track contact form submissions
- Identify geographic interest patterns

### Mobile Responsiveness
- Touch-friendly slider controls
- Readable typography at all sizes
- Stacked grid layouts (1 column on mobile)
- Large, tappable CTA buttons

---

## Design Inspiration Sources

1. **Big.dk**: Overall layout, project grid, metadata approach
2. **Designgood.co**: Project showcase with compelling imagery
3. **Formfiftyeight.com**: Minimalist portfolio with custom components
4. **Pentagram.com**: Clean professional showcase
5. **Wearepipe.com**: Interactive project details

---

## Success Metrics

- Time to navigate to project details (< 3 clicks)
- ROI calculator usage rate
- Project comparison feature usage
- Contact form conversion rate
- Mobile usability score (90+)
- PageSpeed Insights (85+ Core Web Vitals)

---

## Future Enhancements

1. **AI-powered project recommendation**: "Similar projects to your situation"
2. **Virtual tours**: 360° project views or walkthrough videos
3. **Timeline estimator**: Interactive project duration calculator
4. **Material selector**: "See this kitchen with different countertops"
5. **Neighborhood analytics**: Show ADU rental market data by location
6. **Client portal**: Project updates, financing options, permit tracking
7. **Mobile app**: Native experience for project browsing and calculator

---

## Questions for Clarification

1. **Brand name**: What should we call the business?
2. **Location focus**: California-wide, specific region, or national?
3. **Specialty order**: Is ADU the lead offering or equal to remodels?
4. **Pricing model**: Hourly consulting, project-based, subscription dashboards?
5. **Social proof**: Do you have existing client testimonials/photos?
6. **Timeline**: When should this go live?
7. **Analytics**: What business metrics are most important to track?

---

**Document Version**: 1.0
**Last Updated**: November 2024
**Next Review**: After Phase 1 completion

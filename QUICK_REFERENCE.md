# Quick Reference: Architecture Portfolio Development

## File Locations Quick Map

### When Adding a New Project
1. Create: `_projects/YYYY-MM-DD-project-name.md`
2. Add images to: `assets/images/projects/project-name/`
3. Reference in front matter with relative paths
4. Leverage `project-single.html` layout

### When Creating a Service Page
1. Create: `_pages/services/service-name.md`
2. Use layout: `services.html`
3. Include example projects (cross-reference `_projects/`)
4. Add interactive calculator component

### When Customizing Styling
1. Primary: `_sass/minimal-mistakes/skins/_architecture.scss`
2. Component-specific: `_sass/minimal-mistakes/_*.scss` (e.g., `_page.scss`)
3. Variables: Override in `_architecture.scss` or update `_variables.scss`
4. Compile: `jekyll build` auto-compiles SCSS → CSS

### When Adding Interactive Features
1. JavaScript source: `assets/js/_feature-name.js`
2. Include in: `_includes/scripts.html` or `_includes/scripts.html`
3. Initialize in: HTML template or via `(function(){...})()` IIFE
4. Bundle: `main.js` imports all `_*.js` files

## Common Commands

```bash
# Local development with live reload
rake preview

# Build only
jekyll build --source test --destination test/_site

# Minify JavaScript (after editing assets/js/_main.js)
npm run uglify

# Run via bundler (if issues with rake)
bundle exec jekyll serve --source test
```

## Folder Structure for New Project

```
_projects/
└── 2024-01-studio-adu-oakland.md   # Project markdown

assets/images/projects/
└── studio-adu-oakland/
    ├── hero.jpg                     # Hero image (1200x800+)
    ├── before.jpg                   # Before photo
    ├── after.jpg                    # After photo
    ├── 01-bedroom.jpg               # Detail photos
    ├── 02-kitchen.jpg
    ├── 03-living.jpg
    ├── 04-exterior.jpg
    ├── roi-dashboard.png            # ROI chart screenshot
    └── testimonial-client.jpg       # Client photo (optional)
```

## Front Matter Checklist

### Required Fields
- `title`: Project name
- `layout`: Always `project-single`
- `typology`: Remodel / ADU Design / Restoration / etc.
- `location`: City, State
- `year`: YYYY
- `status`: completed / in-progress / idea
- `hero_image`: Path to main project image

### Financial Fields (For ROI)
- `budget`: Total project cost
- `roi_increase`: Percentage or dollar amount
- `investment_payback_years`: Number of years
- `annual_return`: Optional, calculated from budget + roi
- `monthly_rental`: For ADU projects

### Visual Fields
- `images`: Array of project photos with captions
- `before_after`: Array with before/after pairs
- `featured_image`: Thumbnail for project grid

### Content Fields
- `testimonial`: Quote from client
- `services`: List of services provided
- `excerpt`: Short description for preview

## Component Include Examples

### Before/After Slider
```liquid
{% include before-after-slider.html 
  before="/images/projects/project/before.jpg"
  after="/images/projects/project/after.jpg"
  caption="Kitchen renovation"
%}
```

### ROI Calculator
```liquid
{% include roi-calculator.html
  project_title="Studio ADU"
  initial_investment=180000
  monthly_rental=2400
%}
```

### Project Gallery
```liquid
{% include project-gallery.html 
  images=page.images
  title=page.title
%}
```

### Testimonial Block
```liquid
{% include testimonial.html
  quote=page.testimonial.quote
  author=page.testimonial.author
  image=page.testimonial.image
%}
```

## Color System

**Primary Colors** (defined in `_architecture.scss`):
```scss
$primary-color: #1a1a1a;        // Deep charcoal (text, headings)
$secondary-color: #ffffff;       // White (backgrounds)
$background-color: #f5f5f5;      // Light gray (alternating sections)
$border-color: #e8e8e8;          // Very light gray (dividers)
$accent-color: #d4a373;          // Warm gold (highlights, optional)
$success-color: #2ecc71;         // Green (ROI gains, positive metrics)
$warning-color: #f39c12;         // Orange (cautions, warnings)
```

## Typography Scale

```scss
$base-font-size: 16px;
$line-height-computed: 1.6;

h1 { font-size: 2.5rem; }        // Page titles
h2 { font-size: 2rem; }          // Section headings
h3 { font-size: 1.5rem; }        // Subsections
h4 { font-size: 1.25rem; }
p  { font-size: 1rem; }          // Body text
small { font-size: 0.875rem; }
```

## Responsive Breakpoints

Used in `_variables.scss` and customizable:
```scss
$small: 600px;      // Phones
$medium: 768px;     // Tablets
$large: 1024px;     // Laptops
$x-large: 1280px;   // Desktops
```

## Navigation Structure

**Main Navigation** (update `_data/navigation.yml`):
```yaml
main:
  - title: "Projects"
    url: /projects/
  - title: "Services"
    url: /services/
    children:
      - title: "Remodels"
        url: /services/remodels/
      - title: "ADU Design"
        url: /services/adu-design/
      - title: "Cost Analysis"
        url: /services/cost-analysis/
  - title: "About"
    url: /about/
  - title: "Contact"
    url: /contact/
```

## Development Workflow

1. **Create Content**: Add project markdown + images
2. **Test Locally**: Run `rake preview`
3. **View Changes**: http://localhost:4000
4. **Iterate**: Edit markdown/SCSS, refresh browser
5. **Commit**: Git commit when feature complete
6. **Deploy**: Push to main branch → GitHub Pages auto-builds

## Common Customization Points

### Change Hero Height
Edit `_sass/minimal-mistakes/_page.scss`:
```scss
.page__hero {
  min-height: 500px;  // Change this value
}
```

### Adjust Project Grid
Edit `_sass/minimal-mistakes/skins/_architecture.scss`:
```scss
.projects-grid {
  grid-template-columns: repeat(auto-fill, minmax(350px, 1fr));  // Card width
  gap: 2rem;  // Space between cards
}
```

### Change Button Styling
Edit `_sass/minimal-mistakes/_buttons.scss`:
```scss
.btn {
  background-color: $primary-color;
  color: white;
  border-radius: 4px;  // Adjust roundness
}
```

### Modify Typography
Edit `_sass/minimal-mistakes/skins/_architecture.scss`:
```scss
$font-family-sans-serif: "Your Font Name", system fonts...;
$base-font-size: 18px;  // Increase base size
```

## Testing Checklist

Before publishing a project:
- [ ] Images optimized (< 200KB each)
- [ ] All links functional
- [ ] Mobile view tested (phone, tablet, desktop)
- [ ] ROI calculator works with sample data
- [ ] Before/after slider loads correctly
- [ ] Testimonial displays properly
- [ ] Gallery images load in lightbox
- [ ] No broken image references
- [ ] Spelling/grammar checked
- [ ] SEO meta description added

## Performance Tips

1. **Image Optimization**:
   - Use tools like ImageOptim or TinyPNG
   - Hero images: ~1200-1600px wide
   - Thumbnails: ~400px wide
   - Format: WebP with JPG fallback

2. **Lazy Loading**:
   - Add `loading="lazy"` to images below fold
   - Lightbox images load on-demand

3. **CSS**: 
   - Minified automatically via Jekyll
   - Use utility classes to avoid duplication

4. **JavaScript**:
   - Minify with `npm run uglify`
   - Defer non-critical scripts

## Git Workflow

```bash
# Feature branch
git checkout -b feature/new-project-type

# Make changes, test locally
git add .
git commit -m "Add studio ADU project template"

# Push and create PR
git push origin feature/new-project-type

# After review and merge
git checkout main
git pull origin main
```

## Troubleshooting

| Issue | Solution |
|-------|----------|
| Build fails | Check `_config.yml` syntax, run `jekyll doctor` |
| Styles not updating | Clear cache: `rm -rf .jekyll-cache` |
| Images missing | Check relative paths, ensure files exist in `/assets/images/` |
| JavaScript errors | Open browser console (F12), check `/assets/js/` imports |
| Navigation broken | Verify `_data/navigation.yml` YAML syntax |
| Liquid errors | Check for typos in `{% %}` tags, ensure variables exist |

## Resources

- **Jekyll Docs**: https://jekyllrb.com/docs/
- **Minimal Mistakes**: https://mmistakes.github.io/minimal-mistakes/
- **Big.dk Design Analysis**: https://big.dk/
- **Chart.js**: For ROI visualizations
- **Before/After Slider Inspiration**: Twentytwenty.js (Zurb)

---

**Last Updated**: November 2024  
**Maintained by**: Architecture Portfolio Team

# Project Dependencies Map

This document provides a comprehensive overview of all file dependencies in the UNCIA GROUP Jekyll site.

---

## Table of Contents

1. [Layouts](#layouts-_layouts)
2. [Includes](#includes-_includes)
3. [Stylesheets](#stylesheets-_sass-and-assetscss)
4. [JavaScript Assets](#javascript-assets-assetsjs)
5. [Data Files](#data-files-_data)
6. [Pages](#pages-_pages)
7. [Collections](#collections-_projects-_case_studies)
8. [Configuration](#configuration)
9. [External Dependencies](#external-dependencies)
10. [CI/CD & Deployment](#cicd--deployment-github)
11. [Page Types & Their Layouts](#page-types--their-layouts)

---

## Layouts (_layouts/)

### Layout Hierarchy

```
compress (root wrapper)
└── default (main wrapper)
    ├── archive
    │   ├── projects-showcase
    │   ├── archive-taxonomy
    │   ├── categories
    │   ├── category
    │   ├── collection
    │   ├── posts
    │   ├── tag
    │   └── tags
    ├── single
    ├── project-single
    ├── services
    ├── about
    ├── home (standalone)
    ├── search
    └── splash

home-portfolio (standalone, uses compress directly)
```

### Layout Details

#### [compress.html](_layouts/compress.html)
- **Purpose**: HTML minification wrapper
- **Used by**: Most other layouts (except those that don't specify a layout)
- **Includes**: None directly
- **Notes**: Optional layout for reducing HTML file size

#### [default.html](_layouts/default.html)
- **Extends**: None
- **Includes**:
  - [copyright.html](_includes/copyright.html)
  - [head.html](_includes/head.html)
  - [head/custom.html](_includes/head/custom.html)
  - [skip-links.html](_includes/skip-links.html) (cached)
  - [masthead.html](_includes/masthead.html) (cached)
  - [after-content.html](_includes/after-content.html)
  - [footer.html](_includes/footer.html) (cached)
  - [footer/custom.html](_includes/footer/custom.html)
  - [scripts.html](_includes/scripts.html)
  - [search/search_form.html](_includes/search/search_form.html) (cached, conditional)
- **Used by**: Most page layouts
- **Purpose**: Main site wrapper with header, footer, and basic structure

#### [archive.html](_layouts/archive.html)
- **Extends**: [default.html](_layouts/default.html)
- **Includes**:
  - [page__hero.html](_includes/page__hero.html) (conditional)
  - [page__hero_video.html](_includes/page__hero_video.html) (conditional)
  - [breadcrumbs.html](_includes/breadcrumbs.html) (conditional)
  - [sidebar.html](_includes/sidebar.html)
- **Used by**: Archive pages, collection pages, category pages
- **Purpose**: Template for archive-style pages with lists of posts/projects

#### [projects-showcase.html](_layouts/projects-showcase.html)
- **Extends**: [archive.html](_layouts/archive.html)
- **Includes**: None (uses inline styles and scripts)
- **Used by**: `/projects/` page (collection display)
- **Purpose**: Grid display of all projects with filtering
- **Features**:
  - Filter tabs (All, Education, Culture, Residential, Remodel)
  - Lazy loading images (tiny → small → full)
  - Click-to-navigate on project images
  - Inline JavaScript for filtering

#### [project-single.html](_layouts/project-single.html)
- **Extends**: [default.html](_layouts/default.html)
- **Includes**:
  - [page__hero.html](_includes/page__hero.html) (conditional)
- **Used by**: Individual project pages in `_projects/` collection
- **Purpose**: Single project detail page
- **Features**: Project metadata, gallery placeholder, description, CTA
- **Inline styles**: Yes

#### [single.html](_layouts/single.html)
- **Extends**: [default.html](_layouts/default.html)
- **Includes**:
  - [page__hero.html](_includes/page__hero.html) (conditional)
  - [page__hero_video.html](_includes/page__hero_video.html) (conditional)
  - [breadcrumbs.html](_includes/breadcrumbs.html) (conditional)
  - [sidebar.html](_includes/sidebar.html)
  - [page__meta.html](_includes/page__meta.html)
  - [toc.html](_includes/toc.html) (conditional)
  - [page__taxonomy.html](_includes/page__taxonomy.html)
  - [page__date.html](_includes/page__date.html)
  - [social-share.html](_includes/social-share.html) (conditional)
  - [post_pagination.html](_includes/post_pagination.html)
  - [comments.html](_includes/comments.html) (conditional, production only)
  - [page__related.html](_includes/page__related.html) (conditional)
- **Used by**: Blog posts, standard pages
- **Purpose**: General-purpose single page/post layout

#### [home-portfolio.html](_layouts/home-portfolio.html)
- **Extends**: [compress.html](_layouts/compress.html)
- **Includes**:
  - [head.html](_includes/head.html)
  - [skip-links.html](_includes/skip-links.html)
  - [masthead.html](_includes/masthead.html)
  - [footer.html](_includes/footer.html)
  - [scripts.html](_includes/scripts.html)
- **Used by**: Homepage (`/index.md`)
- **Purpose**: Custom homepage with hero, featured projects, services, process, testimonials
- **Features**: Sections are data-driven from page front matter
- **Inline styles**: Yes

#### [services.html](_layouts/services.html)
- **Extends**: [default.html](_layouts/default.html)
- **Includes**:
  - [page__hero.html](_includes/page__hero.html) (conditional)
  - [roi-calculator.html](_includes/roi-calculator.html) (conditional)
  - [cost-calculator.html](_includes/cost-calculator.html) (conditional, referenced but may not exist)
  - [timeline-calculator.html](_includes/timeline-calculator.html) (conditional, referenced but may not exist)
  - [testimonial.html](_includes/testimonial.html) (loop)
- **Used by**: Service pages
- **Purpose**: Service detail pages with features, case studies, process, pricing
- **Inline styles**: Yes

#### [about.html](_layouts/about.html)
- **Extends**: [default.html](_layouts/default.html)
- **Includes**:
  - [page__hero.html](_includes/page__hero.html) (conditional)
  - [testimonial.html](_includes/testimonial.html) (loop, conditional)
- **Used by**: About pages
- **Purpose**: Team/about page with team members, philosophy, values, stats
- **Inline styles**: Yes

#### Other Archive Layouts

- **[archive-taxonomy.html](_layouts/archive-taxonomy.html)**: Used for category/tag archive pages
- **[categories.html](_layouts/categories.html)**: All categories listing
- **[category.html](_layouts/category.html)**: Single category archive
- **[collection.html](_layouts/collection.html)**: Collection archive
- **[posts.html](_layouts/posts.html)**: Posts archive
- **[tag.html](_layouts/tag.html)**: Single tag archive
- **[tags.html](_layouts/tags.html)**: All tags listing
- **[home.html](_layouts/home.html)**: Alternative homepage layout (not currently used)
- **[search.html](_layouts/search.html)**: Search results page
- **[splash.html](_layouts/splash.html)**: Full-width splash page

---

## Includes (_includes/)

### Core Includes

#### [head.html](_includes/head.html)
- **Used by**: All layouts via [default.html](_layouts/default.html) or [home-portfolio.html](_layouts/home-portfolio.html)
- **Includes**:
  - [seo.html](_includes/seo.html)
- **External resources**:
  - FontAwesome CSS: `https://cdn.jsdelivr.net/npm/@fortawesome/fontawesome-free@latest/css/all.min.css`
- **Loads**:
  - `/assets/css/main.css`
  - Favicon from `site.favicon`
  - Custom head scripts from `site.head_scripts`

#### [masthead.html](_includes/masthead.html)
- **Used by**: [default.html](_layouts/default.html), [home-portfolio.html](_layouts/home-portfolio.html)
- **Purpose**: Site header with logo and main navigation
- **Data source**: `_data/navigation.yml` (`navigation.main`)
- **Includes**: None
- **Features**: Logo, site title, nav menu, search toggle, responsive hamburger menu

#### [footer.html](_includes/footer.html)
- **Used by**: [default.html](_layouts/default.html), [home-portfolio.html](_layouts/home-portfolio.html)
- **Purpose**: Site footer with social links and copyright
- **Data source**: `_data/ui-text.yml`
- **Includes**: None
- **Features**: Social links from `site.footer.links`, RSS feed link, powered-by text

#### [scripts.html](_includes/scripts.html)
- **Used by**: All layouts
- **Includes**:
  - [analytics.html](_includes/analytics.html)
  - [comments-providers/scripts.html](_includes/comments-providers/scripts.html)
  - [search/lunr-search-scripts.html](_includes/search/lunr-search-scripts.html) (conditional)
  - [search/google-search-scripts.html](_includes/search/google-search-scripts.html) (conditional)
  - [search/algolia-search-scripts.html](_includes/search/algolia-search-scripts.html) (conditional)
- **Loads**:
  - `/assets/js/main.min.js` (default)
  - Custom scripts from `site.footer_scripts` or `site.after_footer_scripts`

#### [seo.html](_includes/seo.html)
- **Used by**: [head.html](_includes/head.html)
- **Purpose**: SEO meta tags, Open Graph, Twitter Cards, schema.org
- **Data source**: `_data/authors.yml` (if exists)
- **Includes**: None
- **Features**: Dynamic title, description, author, social meta tags

### Navigation & Structure

#### [sidebar.html](_includes/sidebar.html)
- **Used by**: [archive.html](_layouts/archive.html), [single.html](_layouts/single.html)
- **Includes**:
  - [author-profile.html](_includes/author-profile.html) (conditional)
  - [author-profile-custom-links.html](_includes/author-profile-custom-links.html) (conditional)
- **Purpose**: Left sidebar with author info or custom navigation

#### [breadcrumbs.html](_includes/breadcrumbs.html)
- **Used by**: [archive.html](_layouts/archive.html), [single.html](_layouts/single.html)
- **Data source**: `_data/ui-text.yml`
- **Purpose**: Breadcrumb navigation trail

#### [skip-links.html](_includes/skip-links.html)
- **Used by**: [default.html](_layouts/default.html), [home-portfolio.html](_layouts/home-portfolio.html)
- **Data source**: `_data/ui-text.yml`
- **Purpose**: Accessibility skip navigation links

### Page Components

#### [page__hero.html](_includes/page__hero.html)
- **Used by**: [single.html](_layouts/single.html), [project-single.html](_layouts/project-single.html), [services.html](_layouts/services.html), [about.html](_layouts/about.html), [archive.html](_layouts/archive.html)
- **Purpose**: Hero header image/overlay

#### [page__hero_video.html](_includes/page__hero_video.html)
- **Used by**: [single.html](_layouts/single.html), [archive.html](_layouts/archive.html)
- **Purpose**: Video hero header

#### [page__meta.html](_includes/page__meta.html)
- **Used by**: [single.html](_layouts/single.html)
- **Includes**:
  - [page__taxonomy.html](_includes/page__taxonomy.html) (may be duplicated)
  - [page__date.html](_includes/page__date.html) (may be duplicated)
- **Purpose**: Post metadata (date, reading time, etc.)

#### [page__taxonomy.html](_includes/page__taxonomy.html)
- **Used by**: [single.html](_layouts/single.html)
- **Includes**:
  - [category-list.html](_includes/category-list.html)
  - [tag-list.html](_includes/tag-list.html)
- **Purpose**: Display categories and tags

#### [page__date.html](_includes/page__date.html)
- **Used by**: [single.html](_layouts/single.html)
- **Data source**: `_data/ui-text.yml`
- **Purpose**: Display publish/update dates

#### [toc.html](_includes/toc.html)
- **Used by**: [single.html](_layouts/single.html)
- **Purpose**: Table of contents generator
- **Data source**: `_data/ui-text.yml`

### Content Display

#### [archive-single.html](_includes/archive-single.html)
- **Used by**: Archive pages (categories, tags, collections)
- **Purpose**: Single post/page teaser in archive listings

#### [post_pagination.html](_includes/post_pagination.html)
- **Used by**: [single.html](_layouts/single.html)
- **Data source**: `_data/ui-text.yml`
- **Purpose**: Previous/next post navigation

#### [page__related.html](_includes/page__related.html)
- **Used by**: [single.html](_layouts/single.html)
- **Data source**: `_data/ui-text.yml`
- **Purpose**: Related posts section

#### [social-share.html](_includes/social-share.html)
- **Used by**: [single.html](_layouts/single.html)
- **Data source**: `_data/ui-text.yml`
- **Purpose**: Social media share buttons

### Custom Components (UNCIA-specific)

#### [testimonial.html](_includes/testimonial.html)
- **Used by**: [services.html](_layouts/services.html), [about.html](_layouts/about.html)
- **Purpose**: Display testimonial with quote, author, location, rating
- **Parameters**: `quote`, `author`, `location`, `image`, `rating`

#### [roi-calculator.html](_includes/roi-calculator.html)
- **Used by**: [services.html](_layouts/services.html)
- **Purpose**: Interactive ROI calculator widget

#### [project-gallery.html](_includes/project-gallery.html)
- **Used by**: Not currently used (available for future use)
- **Purpose**: Project image gallery component

#### [before-after-slider.html](_includes/before-after-slider.html)
- **Used by**: Not currently used (available for future use)
- **Purpose**: Before/after image comparison slider

### Comments

#### [comments.html](_includes/comments.html)
- **Used by**: [single.html](_layouts/single.html)
- **Includes**: Provider-specific comment includes based on `site.comments.provider`
  - [comments-providers/disqus.html](_includes/comments-providers/disqus.html)
  - [comments-providers/discourse.html](_includes/comments-providers/discourse.html)
  - [comments-providers/facebook.html](_includes/comments-providers/facebook.html)
  - [comments-providers/staticman.html](_includes/comments-providers/staticman.html)
  - [comments-providers/staticman_v2.html](_includes/comments-providers/staticman_v2.html)
  - [comments-providers/utterances.html](_includes/comments-providers/utterances.html)
  - [comments-providers/giscus.html](_includes/comments-providers/giscus.html)
  - [comments-providers/custom.html](_includes/comments-providers/custom.html)

#### [comments-providers/scripts.html](_includes/comments-providers/scripts.html)
- **Used by**: [scripts.html](_includes/scripts.html)
- **Includes**: [comments-providers/custom_scripts.html](_includes/comments-providers/custom_scripts.html)

### Analytics

#### [analytics.html](_includes/analytics.html)
- **Used by**: [scripts.html](_includes/scripts.html)
- **Includes**: Provider-specific analytics based on `site.analytics.provider`
  - [analytics-providers/google.html](_includes/analytics-providers/google.html)
  - [analytics-providers/google-universal.html](_includes/analytics-providers/google-universal.html)
  - [analytics-providers/google-gtag.html](_includes/analytics-providers/google-gtag.html)
  - [analytics-providers/custom.html](_includes/analytics-providers/custom.html)

### Search

#### [search/search_form.html](_includes/search/search_form.html)
- **Used by**: [default.html](_layouts/default.html)
- **Data source**: `_data/ui-text.yml`
- **Purpose**: Search input form

#### [search/lunr-search-scripts.html](_includes/search/lunr-search-scripts.html)
- **Used by**: [scripts.html](_includes/scripts.html)
- **Purpose**: Lunr.js search implementation
- **External**: Lunr.js library

#### [search/google-search-scripts.html](_includes/search/google-search-scripts.html)
- **Used by**: [scripts.html](_includes/scripts.html)
- **Purpose**: Google Custom Search implementation

#### [search/algolia-search-scripts.html](_includes/search/algolia-search-scripts.html)
- **Used by**: [scripts.html](_includes/scripts.html)
- **Purpose**: Algolia search implementation
- **External**: Algolia search API

### Utility Includes

#### [copyright.html](_includes/copyright.html)
- **Used by**: [default.html](_layouts/default.html)
- **Purpose**: Copyright comment in HTML

#### [after-content.html](_includes/after-content.html)
- **Used by**: [default.html](_layouts/default.html)
- **Purpose**: Custom content after main content (currently empty/customizable)

#### [before-related.html](_includes/before-related.html)
- **Used by**: Not currently used
- **Purpose**: Custom content before related posts

#### [head/custom.html](_includes/head/custom.html)
- **Used by**: [default.html](_layouts/default.html) via [head.html](_includes/head.html)
- **Purpose**: Custom head content (user customization point)

#### [footer/custom.html](_includes/footer/custom.html)
- **Used by**: [default.html](_layouts/default.html)
- **Purpose**: Custom footer content (user customization point)

### Pagination

#### [paginator.html](_includes/paginator.html)
- **Purpose**: Main paginator router
- **Includes**:
  - [paginator-v1.html](_includes/paginator-v1.html)
  - [paginator-v2.html](_includes/paginator-v2.html)

---

## Stylesheets (_sass/ and assets/css/)

### Main Entry Point

#### [assets/css/main.scss](assets/css/main.scss)
- **Compiled to**: `/assets/css/main.css`
- **Imports**:
  - `minimal-mistakes/skins/{{ site.minimal_mistakes_skin }}` (currently: `architecture`)
  - `minimal-mistakes`

### Core SCSS Structure

#### [_sass/minimal-mistakes.scss](_sass/minimal-mistakes.scss)
Main orchestrator that imports all component styles:

**Imports**:
1. `minimal-mistakes/copyright` - Copyright comment
2. `minimal-mistakes/variables` - SCSS variables
3. **Vendor libraries**:
   - `minimal-mistakes/vendor/breakpoint/breakpoint` - Responsive breakpoint system
   - `minimal-mistakes/vendor/magnific-popup/magnific-popup` - Lightbox popup
   - `minimal-mistakes/vendor/susy/susy` - Grid system
4. `minimal-mistakes/mixins` - SCSS mixins
5. **Core CSS**:
   - `minimal-mistakes/reset` - CSS reset
   - `minimal-mistakes/base` - Base styles
   - `minimal-mistakes/forms` - Form styles
   - `minimal-mistakes/tables` - Table styles
   - `minimal-mistakes/animations` - Animation keyframes
6. **Components**:
   - `minimal-mistakes/buttons` - Button styles
   - `minimal-mistakes/notices` - Notice/alert boxes
   - `minimal-mistakes/masthead` - Header/navigation
   - `minimal-mistakes/navigation` - Navigation components
   - `minimal-mistakes/footer` - Footer styles
   - `minimal-mistakes/search` - Search component styles
   - `minimal-mistakes/syntax` - Code syntax highlighting
7. **Utilities**:
   - `minimal-mistakes/utilities` - Utility classes
8. **Layout-specific**:
   - `minimal-mistakes/page` - Page layout styles
   - `minimal-mistakes/archive` - Archive page styles
   - `minimal-mistakes/sidebar` - Sidebar styles
   - `minimal-mistakes/home-portfolio` - Custom homepage styles
   - `minimal-mistakes/print` - Print media styles

### Skins (Color Schemes)

Located in `_sass/minimal-mistakes/skins/`:
- [_air.scss](_sass/minimal-mistakes/skins/_air.scss)
- [_aqua.scss](_sass/minimal-mistakes/skins/_aqua.scss)
- [_architecture.scss](_sass/minimal-mistakes/skins/_architecture.scss) ⭐ **Currently Active**
- [_contrast.scss](_sass/minimal-mistakes/skins/_contrast.scss)
- [_dark.scss](_sass/minimal-mistakes/skins/_dark.scss)
- [_default.scss](_sass/minimal-mistakes/skins/_default.scss)
- [_dirt.scss](_sass/minimal-mistakes/skins/_dirt.scss)
- [_mint.scss](_sass/minimal-mistakes/skins/_mint.scss)
- [_neon.scss](_sass/minimal-mistakes/skins/_neon.scss)
- [_plum.scss](_sass/minimal-mistakes/skins/_plum.scss)
- [_sunrise.scss](_sass/minimal-mistakes/skins/_sunrise.scss)

**Set in**: `_config.yml` → `minimal_mistakes_skin: "architecture"`

### Vendor Dependencies

#### Breakpoint Library
- **Location**: `_sass/minimal-mistakes/vendor/breakpoint/`
- **Purpose**: Responsive breakpoint mixin system
- **Files**:
  - `_breakpoint.scss` (main)
  - `_context.scss`
  - `_helpers.scss`
  - `_legacy-settings.scss`
  - `_no-query.scss`
  - `_parsers.scss`
  - `_respond-to.scss`
  - `_settings.scss`
  - `parsers/` subdirectory (double, query, resolution, single, triple)

#### Magnific Popup
- **Location**: `_sass/minimal-mistakes/vendor/magnific-popup/`
- **Purpose**: Lightbox/modal popup functionality
- **Files**:
  - `_magnific-popup.scss` (main)
  - `_settings.scss`

#### Susy Grid System
- **Location**: `_sass/minimal-mistakes/vendor/susy/`
- **Purpose**: Grid layout system
- **Files**:
  - `_su.scss`
  - `_susy.scss` (main)
  - `_susy-prefix.scss`
  - `plugins/_svg-grid.scss`
  - `susy/` subdirectory (api, normalize, parse, settings, math, validate, helpers, utilities)

### Custom SCSS Files

#### [_sass/minimal-mistakes/_home-portfolio.scss](_sass/minimal-mistakes/_home-portfolio.scss)
- **Purpose**: Styles for homepage ([home-portfolio.html](_layouts/home-portfolio.html))
- **Used by**: Main SCSS import chain
- **Features**: Hero section, project grid, service cards, testimonials, process steps

### Inline Styles

Several layouts include inline `<style>` blocks:
- [projects-showcase.html](_layouts/projects-showcase.html) - Filter tabs, project grid, lazy loading
- [project-single.html](_layouts/project-single.html) - Project detail page styles
- [services.html](_layouts/services.html) - Service page components
- [about.html](_layouts/about.html) - Team grid, stats, values

---

## JavaScript Assets (assets/js/)

### Main JavaScript File

#### [assets/js/main.min.js](assets/js/main.min.js)
- **Source**: Compiled from [assets/js/_main.js](assets/js/_main.js)
- **Loaded by**: [scripts.html](_includes/scripts.html)
- **Purpose**: Core site JavaScript functionality
- **Size**: Minified with source map ([main.min.js.map](assets/js/main.min.js.map))

### Source JavaScript

#### [assets/js/_main.js](assets/js/_main.js)
- **Purpose**: Main JavaScript source (pre-compilation)
- **Dependencies**: jQuery and all plugins listed below
- **Functionality**:
  - Navigation menu behavior
  - Smooth scrolling
  - Search functionality
  - Image galleries
  - Responsive features

### jQuery Core

#### [assets/js/vendor/jquery/jquery-3.6.0.js](assets/js/vendor/jquery/jquery-3.6.0.js)
- **Version**: 3.6.0
- **Purpose**: jQuery library dependency
- **Used by**: All plugins and main.js

### jQuery Plugins

Located in `assets/js/plugins/`:

1. **[jquery.greedy-navigation.js](assets/js/plugins/jquery.greedy-navigation.js)**
   - Purpose: Responsive navigation menu (collapses overflowing items)
   - Used in: Masthead navigation

2. **[jquery.magnific-popup.js](assets/js/plugins/jquery.magnific-popup.js)**
   - Purpose: Lightbox/modal popup for images and galleries
   - Used in: Project galleries, image popups
   - Paired with: SCSS `_magnific-popup.scss`

3. **[jquery.fitvids.js](assets/js/plugins/jquery.fitvids.js)**
   - Purpose: Responsive video embeds
   - Used in: Video content scaling

4. **[jquery.ba-throttle-debounce.js](assets/js/plugins/jquery.ba-throttle-debounce.js)**
   - Purpose: Performance optimization for scroll/resize events
   - Used in: Scroll handlers, resize handlers

5. **[smooth-scroll.js](assets/js/plugins/smooth-scroll.js)**
   - Purpose: Smooth scrolling to anchor links
   - Used in: Internal page navigation, skip links

6. **[gumshoe.js](assets/js/plugins/gumshoe.js)**
   - Purpose: Scroll spy for highlighting active navigation items
   - Used in: Table of contents, page sections

### Search JavaScript

Located in `assets/js/lunr/`:

1. **[lunr.min.js](assets/js/lunr/lunr.min.js)** / **[lunr.js](assets/js/lunr/lunr.js)**
   - Purpose: Lunr.js search library (client-side search engine)
   - Loaded by: [search/lunr-search-scripts.html](_includes/search/lunr-search-scripts.html)

2. **[lunr-en.js](assets/js/lunr/lunr-en.js)**
   - Purpose: English language support for Lunr
   - Dependency: lunr.js

3. **[lunr-gr.js](assets/js/lunr/lunr-gr.js)**
   - Purpose: Greek language support for Lunr (if needed)
   - Dependency: lunr.js

4. **[lunr-store.js](assets/js/lunr/lunr-store.js)**
   - Purpose: Generated search index store
   - Generated by: Jekyll during build
   - Contains: Searchable content from site pages/posts

### JavaScript Loading Order

1. jQuery core (`jquery-3.6.0.js`)
2. jQuery plugins (throttle-debounce, greedy-navigation, magnific-popup, fitvids)
3. Vanilla JS plugins (smooth-scroll, gumshoe)
4. Main site script (`main.min.js`)
5. Search scripts (conditional, if search enabled)
6. Analytics scripts (conditional)
7. Comment scripts (conditional)

---

## Data Files (_data/)

### [_data/navigation.yml](_data/navigation.yml)
- **Purpose**: Site-wide navigation menu configuration
- **Used by**: [masthead.html](_includes/masthead.html)
- **Structure**:
  ```yaml
  main:
    - title: "Projects"
      url: /projects/
    - title: "About"
      url: /about/
    - title: "Data & Dashboards"
      url: /data-engineering/
    - title: "Contact"
      url: /contact/
  ```
- **Fields**:
  - `title`: Display text for navigation link
  - `url`: Destination URL (can be relative or absolute)
  - `description`: Optional tooltip text

### [_data/ui-text.yml](_data/ui-text.yml)
- **Purpose**: Localized UI text strings for interface elements
- **Used by**: Multiple includes throughout site:
  - [footer.html](_includes/footer.html)
  - [breadcrumbs.html](_includes/breadcrumbs.html)
  - [skip-links.html](_includes/skip-links.html)
  - [search/search_form.html](_includes/search/search_form.html)
  - [paginator.html](_includes/paginator.html)
  - [page__meta.html](_includes/page__meta.html)
  - [social-share.html](_includes/social-share.html)
  - [comments.html](_includes/comments.html)
  - And many others
- **Languages Supported**: English (en), Spanish (es), and many more
- **Current Locale**: `en-US` (set in `_config.yml`)
- **Sample Strings**:
  - `skip_links`, `page`, `pagination_previous/next`
  - `breadcrumb_home_label`, `menu_label`, `search_label`
  - `toc_label`, `share_on_label`, `comments_label`
  - `feed_label`, `powered_by`, `recent_posts`

---

## Pages (_pages/)

All pages in `_pages/` are markdown files that generate site pages.

### [_pages/404.md](_pages/404.md)
- **Layout**: Not specified in snippet (likely `default` or `single`)
- **Permalink**: `/404.html`
- **Purpose**: 404 error page

### [_pages/projects.md](_pages/projects.md)
- **Layout**: [projects-showcase.html](_layouts/projects-showcase.html)
- **Permalink**: `/projects/`
- **Collection**: `projects`
- **Purpose**: Main projects listing page with filtering
- **Features**: Grid view of all projects with category filters

### [_pages/about.md](_pages/about.md)
- **Layout**: [single.html](_layouts/single.html)
- **Permalink**: `/about/`
- **Purpose**: About page for UNCIA team
- **Content**:
  - Team introduction (Zhun Jiao & Annie Branum-Jiao)
  - Etymology of "Uncia" name
  - Expertise areas (educational, residential, community)
  - Services offered
  - Portfolio summary
  - Contact information

### [_pages/contact.md](_pages/contact.md)
- **Layout**: [single.html](_layouts/single.html)
- **Permalink**: `/contact/`
- **Purpose**: Contact information and inquiry form
- **Content**:
  - Email: `zhun.jiao.architect@gmail.com`
  - Location: Austin, Texas
  - What to include in inquiries
  - Expected response timeline

### [_pages/data-engineering.md](_pages/data-engineering.md)
- **Layout**: [single.html](_layouts/single.html)
- **Permalink**: `/data-engineering/`
- **Purpose**: Data engineering services and dashboard examples
- **Content**:
  - ROI dashboard examples
  - Construction cost estimation
  - ADU investment analysis
  - Scenario planning tools
  - Technologies used (Python, Pandas, Plotly, D3.js, Tableau)

### [_pages/search.md](_pages/search.md)
- **Layout**: [search.html](_layouts/search.html)
- **Permalink**: `/search/`
- **Purpose**: Site-wide search page

---

## Collections (_projects/, _case_studies/)

### Projects Collection (`_projects/`)

**Configuration** (from `_config.yml`):
```yaml
collections:
  projects:
    output: true
    permalink: /projects/:path/
```

**Default Front Matter** (from `_config.yml`):
```yaml
defaults:
  - scope:
      path: ""
      type: projects
    values:
      layout: project-single
      author_profile: false
      share: true
```

**Files**: 15 project markdown files
- `2025-11-24-teacher-housing.md`
- `2025-11-24-doss-elementary.md`
- `2025-11-24-round-rock-city-center.md`
- `2025-11-25-hutto-high-school.md`
- `2025-11-25-bastrop-high-school.md`
- `2025-11-25-crockett-high-school.md`
- `2025-11-25-leander-high-school.md`
- `2025-11-25-cd-fulks-middle-school.md`
- `2025-11-25-austin-oaks-redevelopment.md`
- `2025-11-25-st-edwards-library.md`
- `2025-11-25-guggenheim-helsinki.md`
- `2025-11-25-atlantis-living-district.md`
- `2025-11-25-tea-house-design.md`
- `2025-11-25-new-braunfels-isd-admin.md`
- `2025-11-25-leander-early-college-high-school.md`

**Common Front Matter Fields**:
- `title`: Project name
- `layout`: `project-single` (default)
- `typology`: Building/project type
- `location`: Geographic location
- `year`: Project year
- `status`: Project status (concept, in-planning, proposed, etc.)
- `filter_tag`: Category for filtering (education, culture, residential, remodel)
- `budget`: Project budget
- `hero_image`: Main project image (default: `/assets/images/projects/placeholder-project-hero.svg`)
- `gallery`: Array of images with captions
- `categories`: Project categories/tags

**Content Structure**: Each project includes:
- Project Overview section (heading)
- Design features/concept
- Building sustainability (for educational/large projects)
- Community impact
- Budget & timeline
- Status footer

### Case Studies Collection (`_case_studies/`)

**Configuration** (from `_config.yml`):
```yaml
collections:
  case_studies:
    output: true
    permalink: /case-studies/:path/
```

**Default Front Matter**:
```yaml
defaults:
  - scope:
      path: ""
      type: case_studies
    values:
      layout: project-single
      author_profile: false
      share: true
```

**Status**: Collection configured but no files currently present

---

## Configuration

### [_config.yml](_config.yml)

#### Theme Settings
- **Theme**: `minimal-mistakes-jekyll`
- **Skin**: `architecture`
- **Title**: UNCIA GROUP
- **Subtitle**: Smart Design. Data-Driven ROI.

#### Asset Loading
- **Logo**: `/assets/images/uncia-logo.svg` (used in masthead)
- **Favicon**: `/assets/images/favicon.svg`
- **SASS directory**: `_sass`
- **SASS output style**: `compressed`

#### Search Configuration
- **Enabled**: `true`
- **Provider**: `lunr` (client-side search)
- **Full content search**: `true`

#### Collections
- **projects**:
  - Output: `true`
  - Permalink: `/projects/:path/`
  - Default layout: `project-single`
- **case_studies**:
  - Output: `true`
  - Permalink: `/case-studies/:path/`
  - Default layout: `project-single`

#### Plugins
- `jekyll-sitemap`
- `jekyll-gist`
- `jekyll-feed`
- `jekyll-include-cache`

#### Defaults
- **_pages**: layout `single`, no author profile
- **projects**: layout `project-single`, sharing enabled
- **case_studies**: layout `project-single`, sharing enabled

#### Markdown Processing
- **Engine**: `kramdown`
- **Syntax highlighter**: `rouge`
- **Input**: GFM (GitHub Flavored Markdown)

### [_data/navigation.yml](_data/navigation.yml)
- **Purpose**: Main navigation menu items
- **Used by**: [masthead.html](_includes/masthead.html)
- **Format**: Array of `{ title, url, description }`

### [_data/ui-text.yml](_data/ui-text.yml)
- **Purpose**: Localized UI text strings
- **Used by**: Multiple includes (footer, breadcrumbs, search, pagination, etc.)
- **Format**: Locale → string mappings

---

## External Dependencies

### CDN Resources

#### CSS
1. **FontAwesome Icons**
   - URL: `https://cdn.jsdelivr.net/npm/@fortawesome/fontawesome-free@latest/css/all.min.css`
   - Loaded in: [head.html](_includes/head.html)
   - Loading: Preloaded with async loading strategy
   - Used for: Icons throughout site (navigation, footer, buttons)

#### JavaScript
1. **Main Site JavaScript**
   - Path: `/assets/js/main.min.js`
   - Loaded in: [scripts.html](_includes/scripts.html)
   - Purpose: Core site functionality (navigation, smooth scroll, etc.)

2. **Search Libraries** (conditional based on provider)
   - **Lunr.js**: Client-side search engine
   - **Google Custom Search**: Google search integration
   - **Algolia**: Algolia search API integration

3. **Analytics** (conditional based on provider)
   - Google Analytics (Universal, GA4, or legacy)
   - Custom analytics solutions

4. **Comment Systems** (conditional based on provider)
   - Disqus
   - Discourse
   - Facebook Comments
   - Staticman
   - Utterances
   - Giscus

### Third-Party Integrations

#### Search Providers
- **Lunr** (default, local)
- **Google Custom Search**
- **Algolia** (config: application_id, index_name, api_key)

#### Analytics Providers
- **Google Analytics** (tracking_id from config)
- **Google Universal Analytics**
- **Google Tag Manager (gtag)**

#### Comment Providers
- **Disqus** (shortname from config)
- **Discourse** (server from config)
- **Facebook** (appid from config)
- **Utterances** (theme, issue_term from config)
- **Giscus** (repo_id, category from config)
- **Staticman** (branch, endpoint from config)

---

## Page Types & Their Layouts

### Homepage
- **File**: `/index.md`
- **Layout**: [home-portfolio.html](_layouts/home-portfolio.html)
- **Features**: Hero, featured projects, services, process, testimonials, CTA

### Projects Listing
- **File**: `_pages/projects.md`
- **Layout**: [projects-showcase.html](_layouts/projects-showcase.html)
- **Features**: Filterable grid of all projects, lazy-loaded images

### Individual Projects
- **Files**: `_projects/*.md`
- **Layout**: [project-single.html](_layouts/project-single.html)
- **Features**: Hero image, metadata, gallery, description, CTA

### Service Pages
- **Files**: `_pages/services/*.md`
- **Layout**: [services.html](_layouts/services.html)
- **Features**: Overview, features, calculator, case studies, process, testimonials, pricing, FAQ, CTA

### About Page
- **File**: `_pages/about.md`
- **Layout**: [about.html](_layouts/about.html)
- **Features**: Team members, philosophy, values, process, stats, testimonials, CTA

### Standard Pages
- **Files**: `_pages/*.md`
- **Default layout**: [single.html](_layouts/single.html)
- **Features**: Content, sidebar, TOC, social sharing, comments, related posts

### Archive Pages
- **Category/Tag Pages**: [archive-taxonomy.html](_layouts/archive-taxonomy.html)
- **All Categories**: [categories.html](_layouts/categories.html)
- **All Tags**: [tags.html](_layouts/tags.html)
- **Posts Archive**: [posts.html](_layouts/posts.html)

---

## CI/CD & Deployment (.github/)

### GitHub Actions Workflow

#### [.github/workflows/jekyll.yml](.github/workflows/jekyll.yml)
- **Purpose**: Automated build and deployment to GitHub Pages
- **Trigger**: Push to `main` branch
- **Permissions**:
  - `contents: read` - Read repository files
  - `pages: write` - Deploy to GitHub Pages
  - `id-token: write` - OIDC token for deployment

**Workflow Steps**:

1. **Checkout** (`actions/checkout@v4`)
   - Checks out repository code

2. **Setup Ruby** (`ruby/setup-ruby@v1`)
   - Ruby version: `3.2.2`
   - Enables bundler caching for faster builds
   - Cache version: 0

3. **Install Dependencies**
   - Runs: `bundle install --verbose`
   - Installs all Ruby gems from `Gemfile`

4. **Build with Jekyll**
   - Runs: `bundle exec jekyll build --verbose`
   - Environment: `JEKYLL_ENV=production`
   - Output directory: `./_site`

5. **Upload Artifact** (`actions/upload-pages-artifact@v3`)
   - Uploads built site from `./_site` directory

6. **Deploy to GitHub Pages** (`actions/deploy-pages@v4`)
   - Publishes site to GitHub Pages
   - URL: `https://[username].github.io`

**Concurrency**: Single deployment group ("pages") with cancel-in-progress disabled

### Build Output

The build process generates:
- **_site/** - Complete built website (HTML, CSS, JS, images)
  - Static HTML files from all layouts and pages
  - Compiled CSS from SCSS
  - Copied assets (images, JavaScript)
  - Generated search index (lunr-store.js)
  - Sitemap and feed files

**Note**: The `_site/` directory is excluded from version control (.gitignore) but is the final deployment artifact.

### Other .github Files

#### [.github/copilot-instructions.md](.github/copilot-instructions.md)
- **Purpose**: GitHub Copilot configuration and project context
- **Contains**: Project overview and coding guidelines for AI assistance

---

## Assets Directory Structure

### Images (assets/images/)

1. **[uncia-logo.svg](assets/images/uncia-logo.svg)**
   - Used in: Masthead (configured in `_config.yml` as `site.logo`)
   - Purpose: Site logo in navigation

2. **[favicon.svg](assets/images/favicon.svg)**
   - Used in: `<head>` (configured in `_config.yml` as `site.favicon`)
   - Purpose: Browser tab icon

3. **[osiris.JPG](assets/images/osiris.JPG)**
   - Used in: Homepage hero section ([index.md](index.md))
   - Purpose: Header background image

4. **[projects/placeholder-project-hero.svg](assets/images/projects/placeholder-project-hero.svg)**
   - Used in: Project files as default `hero_image`
   - Purpose: Placeholder for projects without custom images

**Note**: Several `.DS_Store` files present (macOS system files, should be in .gitignore)

---

## Homepage Configuration

### [index.md](index.md)
- **Layout**: [home-portfolio.html](_layouts/home-portfolio.html)
- **Title**: "UNCIA"
- **Permalink**: `/`

**Data-Driven Sections** (configured in front matter):

1. **Header**:
   - Title: "Smart Design. Data-Driven ROI."
   - Subtitle: "We help homeowners and small businesses..."
   - CTA: "View Our Work" → `/projects/`
   - Background image: `/assets/images/osiris.JPG`

2. **Featured Projects** (3 projects):
   - Round Rock City Center
   - Teacher Housing Community
   - Doss Elementary School

3. **Services** (3 services):
   - Home Remodels
   - ADU Design
   - ROI Dashboards

4. **Process** (4 steps):
   - Consult
   - Design
   - Analyze
   - Build

5. **Testimonials** (2 testimonials):
   - John & Sarah Martinez
   - The Chen Family

6. **CTA Section**:
   - Title: "Ready to Start Your Project?"
   - Link to: `/contact/`

**Content Section**: Welcome text and "Why Work With Us" benefits

---

## Dependency Flow Visualization

### Critical Rendering Path

```
Browser Request
    ↓
[default.html]
    ├── [head.html]
    │   ├── [seo.html]
    │   └── /assets/css/main.css
    │       ├── [skins/architecture.scss]
    │       └── [minimal-mistakes.scss]
    │           ├── [variables, mixins, vendor libs]
    │           └── [all component SCSS files]
    ├── [masthead.html]
    │   └── _data/navigation.yml
    ├── CONTENT (from child layout)
    ├── [footer.html]
    │   └── _data/ui-text.yml
    └── [scripts.html]
        ├── /assets/js/main.min.js
        ├── FontAwesome (CDN)
        ├── Search scripts (conditional)
        ├── Analytics (conditional)
        └── Comments (conditional)
```

### Data Flow

```
_config.yml
    ↓
├── Site global variables → All layouts & includes
├── Collections config → _projects/, _case_studies/
├── Defaults → Default layouts for content types
└── Plugin config → Jekyll behavior

_data/
    ├── navigation.yml → [masthead.html]
    └── ui-text.yml → Multiple includes (footer, search, etc.)
```

---

## Notes

### Caching Strategy
- Several includes use `include_cached` for performance:
  - `skip-links.html`
  - `masthead.html`
  - `footer.html`
  - `search/search_form.html`
  - Search provider scripts

### Conditional Loading
- **Search**: Only loads provider scripts when `site.search == true`
- **Analytics**: Only loads when provider is configured
- **Comments**: Only loads when provider is configured and in production
- **Hero images**: Conditionally loaded based on page front matter

### Performance Optimizations
1. **Lazy Loading**: Projects showcase uses progressive image loading (tiny → small → full)
2. **Async CSS**: FontAwesome loaded with preload + async strategy
3. **Include Caching**: Frequently used includes are cached
4. **SASS Compression**: Compiled CSS is compressed
5. **Conditional Scripts**: Only load what's needed based on configuration

### Customization Points
- `_includes/head/custom.html` - Add custom `<head>` content
- `_includes/footer/custom.html` - Add custom footer content
- `_includes/after-content.html` - Add content after main content
- `_includes/analytics-providers/custom.html` - Custom analytics
- `_includes/comments-providers/custom.html` - Custom comments
- Inline styles in custom layouts (projects-showcase, services, about, project-single)

---

**Last Updated**: 2025-11-30
**Maintained by**: UNCIA GROUP

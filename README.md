# Uncia | Architecture & Data-Driven Design Portfolio

[![LICENSE](https://img.shields.io/badge/license-Apache%202.0-blue.svg)](LICENSE)
[![Jekyll](https://img.shields.io/badge/jekyll-%3E%3D%204.3-blue.svg)](https://jekyllrb.com/)

Professional portfolio website for Uncia, specializing in smart home design and financial optimization through data-driven ROI analysis.

## 🏠 Features

- **Portfolio**: 15+ completed architectural projects showcasing residential, commercial, and institutional work
- **Data-Driven ROI**: Interactive calculators and dashboards for cost estimation and financial analysis
- **Services**: Home remodels, ADU (Accessory Dwelling Unit) design, and custom ROI dashboards
- **Responsive Design**: Mobile-first design built on Jekyll and Minimal Mistakes theme
- **Fast Performance**: Static site generation with optimized build time (~0.5 seconds)

## 👥 Team

- **Zhun Jiao** - Architect | Expert in institutional, multi-family, and community planning design
- **Annie Jiao** - Data Engineer | Specialized in financial modeling and ROI analysis

Contact: [zhun.jiao.architect@gmail.com](mailto:zhun.jiao.architect@gmail.com)

## 🛠 Technology Stack

- **Jekyll 4.3.4** - Static site generator
- **Minimal Mistakes Theme** - Professional, customizable Jekyll theme
- **GitHub Pages** - Hosting and continuous deployment
- **Ruby 3.2.2** - Development environment

## 📦 Building Locally

### Prerequisites

- Ruby 3.2.2
- Bundler

### Setup

```bash
bundle install
bundle exec jekyll serve
```

Visit `http://localhost:4000` to view the site locally.

### Building for Production

```bash
bundle exec jekyll build
```

Output will be in the `_site/` directory.

## 📁 Site Structure

- `_pages/` - Main pages (about, contact, services)
- `_projects/` - Portfolio project entries (15 projects)
- `_layouts/` - Custom Jekyll layouts
- `_includes/` - Reusable template components
- `_sass/` - Stylesheets and theme customization
- `assets/` - Images, logos, and fonts

## 🚀 Deployment

This site is automatically deployed to GitHub Pages on every push to the `main` branch via GitHub Actions.

### GitHub Actions Workflow

The `.github/workflows/jekyll.yml` workflow:
1. Checks out the repository
2. Sets up Ruby 3.2.2
3. Installs dependencies with bundler
4. Builds the Jekyll site
5. Deploys to GitHub Pages

## 📄 License

Licensed under the Apache License, Version 2.0. See [LICENSE](LICENSE) file for details.

---

*Built with Jekyll and Minimal Mistakes theme*

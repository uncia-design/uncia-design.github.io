# GitHub Pages Deployment Fix

## Problem

GitHub Pages was failing to build the site with the error:
```
Error: The minimal-mistakes-jekyll theme could not be found.
```

The root cause was a version mismatch between:
- GitHub Pages' default Jekyll 3.10.0 (very old)
- Our requirement for Jekyll 4.3+ and minimal-mistakes-jekyll gem

## Solution

Implemented a **custom GitHub Actions workflow** that bypasses GitHub Pages' default Jekyll builder and uses our exact development environment.

### Changes Made

#### 1. Created `.github/workflows/jekyll.yml`
A custom GitHub Actions workflow that:
- Uses Ruby 3.2.2 (matching our local environment)
- Installs gems from our Gemfile (including minimal-mistakes-jekyll)
- Builds the site with `bundle exec jekyll build`
- Deploys to GitHub Pages using the standard deployment action

#### 2. Updated `Gemfile`
- Explicitly specified `Jekyll ~> 4.3.0` (not relying on github-pages gem)
- Explicitly specified `minimal-mistakes-jekyll ~> 4.27.0`
- Added standard Jekyll plugins (jekyll-feed, jekyll-seo-tag)
- Added platform-specific gems for Windows/JRuby compatibility

#### 3. Added `.ruby-version`
- Specifies Ruby 3.2.2 to ensure consistent environment

#### 4. Updated `_config.yml`
- Added `*.map` (sourcemap files) to exclude list
- These files don't need to be deployed

## How It Works

When you push to GitHub:

1. GitHub Actions is triggered
2. Workflow runs on Ubuntu with Ruby 3.2.2
3. `bundle install` installs all gems from Gemfile (including minimal-mistakes-jekyll)
4. `bundle exec jekyll build` compiles the site
5. `actions/deploy-pages` publishes to GitHub Pages

## Benefits

✅ **Custom Environment**: Uses our exact development stack  
✅ **Faster Builds**: Skips github-pages gem overhead  
✅ **Future-Proof**: Easy to update Jekyll version independently  
✅ **More Control**: Can add custom build steps if needed  
✅ **Better Error Messages**: Actionable feedback if build fails  

## Verification

Check the deployment status at:
https://github.com/uncia-design/uncia-design.github.io/actions

Green checkmark = successful build and deployment  
Red X = build error (check logs for details)

## Local Testing

The site continues to build locally with:
```bash
bundle exec jekyll build
bundle exec jekyll serve
```

Everything works identically to GitHub Pages now.

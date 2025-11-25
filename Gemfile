source "https://rubygems.org"

# Use the github-pages gem to have GitHub Pages dependencies on your local machine.
# If you have any plugins referenced in your site's _config.yml, add them here
# as well. For example:
# gem 'jekyll-github-metadata'
#
# The following plugins are automatically loaded by the github-pages gem:
#   gem 'jekyll-sass-converter'
#   gem 'jekyll-remote-theme'
#   gem 'jekyll-paginate'
#   gem 'jekyll-sitemap'
#   gem 'jekyll-gist'
#   gem 'jekyll-feed'
#   gem 'jekyll-include-cache'
#   gem 'jekyll-mentions'
#   gem 'jekyll-optional-front-matter'
#   gem 'jekyll-paginate'
#   gem 'jekyll-readme-index'
#   gem 'jekyll-redirect-from'
#   gem 'jekyll-relative-links'
#   gem 'jekyll-seo-tag'
#   gem 'jekyll-sitemap'
#   gem 'jekyll-titles-from-headings'
#   gem 'jekyll-feed'
#   gem 'jemoji'
#   gem 'jekyll-mentions'
#   gem 'jekyll-relative-links'
#   gem 'jekyll-optional-front-matter'
#   gem 'jekyll-readme-index'

# If you want to use Jekyll without relying on the github-pages gem,
# comment out the line below and uncomment the lines which follow.
# gem "github-pages"

gem "jekyll", "~> 4.3.0"
gem "minimal-mistakes-jekyll", "~> 4.27.0"
gem "jekyll-include-cache", group: :jekyll_plugins
gem "kramdown-parser-gfm", "~> 1.1"
gem "webrick", "~> 1.8"

# If you have any plugins referenced in your site's _config.yml, add them here
# as well. For example:
group :jekyll_plugins do
  gem "jekyll-feed", "~> 0.12"
  gem "jekyll-seo-tag", "~> 2.8"
end

# Windows and JRuby does not include zoneinfo files, so bundle the tzinfo-data gem
# and associated library.
platforms :mingw, :x64_mingw, :mswin, :jruby do
  gem "tzinfo", "~> 1.2"
  gem "tzinfo-data"
end

# Performance-booster for watching directories on Windows
gem "wdm", "~> 0.1.1", :platforms => [:mingw, :x64_mingw, :mswin]

# Lock `http_parser.rb` gemspec issue against aspnet-core
gem "http_parser.rb", "~> 0.6.0", :platforms => [:jruby]

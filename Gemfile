source "https://rubygems.org"

# Jekyll
gem "jekyll", "~> 4.0"

# This is the theme you are using
gem "minimal-mistakes-jekyll"

# If you want to use GitHub Pages, include this as well
# gem "github-pages", group: :jekyll_plugins

# Plugins for Jekyll
group :jekyll_plugins do
  gem "jekyll-feed", "~> 0.12"
  gem "jekyll-seo-tag", "~> 2.6"
  gem "jekyll-paginate"
  gem "jekyll-sitemap"
  gem "jekyll-include-cache" # Required for 'include_cached' tag
end

# Windows does not include zoneinfo files, so bundle the tzinfo-data gem
# and associated library.
platforms :mingw, :x64_mingw, :mswin, :jruby do
  gem "tzinfo", "~> 1.2"
  gem "tzinfo-data"
end

# Performance-booster for watching directories on Windows
gem "wdm", "~> 0.1.1", platforms: [:x64_mingw, :mingw, :mswin]
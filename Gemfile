source "https://rubygems.org"

# This matches the gem set GitHub Pages actually runs in production,
# so if it builds locally with this Gemfile, it'll build on GitHub too.
gem "github-pages", group: :jekyll_plugins

group :jekyll_plugins do
  gem "jekyll-seo-tag"
end

# Windows and JRuby does not include zoneinfo files, so bundle the tzinfo-data gem
# and associated library.
install_if -> { RUBY_PLATFORM =~ %r!mingw|mswin|java! } do
  gem "tzinfo", "~> 1.2"
  gem "tzinfo-data"
end

# Performance-booster for watching directories on Windows
gem "wdm", "~> 0.1.1", :install_if => Gem.win_platform?

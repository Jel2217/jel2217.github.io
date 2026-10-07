source "https://rubygems.org"

# The site is built with plain Jekyll. Cloudflare Pages runs `bundle install`,
# then the build command `bundle exec jekyll build`, and serves `_site`.
gem "jekyll", "~> 4.4"

group :jekyll_plugins do
  gem "jekyll-seo-tag", "~> 2.8"
  gem "jekyll-sitemap", "~> 1.4"
end

# Needed for `bundle exec jekyll serve` on Ruby 3 and later
gem "webrick", "~> 1.9"

# Windows and JRuby don't include zoneinfo files
platforms :mingw, :x64_mingw, :mswin, :jruby do
  gem "tzinfo", ">= 1", "< 3"
  gem "tzinfo-data"
end

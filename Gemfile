source "https://rubygems.org"

# This:
gem "jekyll", "~> 4.2.2"
# Or below:
# gem "github-pages", group: :jekyll_plugins

#gem "minima", "~> 2.5"

group :jekyll_plugins do
  gem "jekyll-feed"
  gem 'jekyll-tagging-related_posts'
  gem 'jekyll-paginate'
  gem 'jekyll-include-cache'
  gem 'jekyll-seo-tag'
  gem 'jekyll-admin'
  gem 'jekyll-archives'
  gem 'jekyll-sitemap'
  gem 'jekyll-toc'
end

platforms :mingw, :x64_mingw, :mswin, :jruby do
  gem "tzinfo", "~> 1.2"
  gem "tzinfo-data"
end

# Performance-booster for watching directories on Windows
gem "wdm", "~> 0.1.1", :platforms => [:mingw, :x64_mingw, :mswin]

# Lock `http_parser.rb` gem to `v0.6.x` on JRuby builds since newer versions do not have a Java counterpart.
gem "http_parser.rb", "~> 0.6.0", :platforms => [:jruby]

gem "webrick", "~> 1.7"
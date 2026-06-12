source "https://rubygems.org"

# Match the version of Jekyll used by GitHub Pages so local builds line up
# with the deployed site. See https://pages.github.com/versions/.
gem "github-pages", group: :jekyll_plugins

group :jekyll_plugins do
  gem "jekyll-seo-tag"
end

# Ruby 3.4+ removed these from default gems; Jekyll 3.9 still requires them.
gem "csv"
gem "base64"
gem "bigdecimal"

# Standard Jekyll runtime gems on macOS.
gem "tzinfo-data", platforms: [:mingw, :mswin, :x64_mingw, :jruby]
gem "wdm", "~> 0.1.1", platforms: [:mingw, :mswin, :x64_mingw]

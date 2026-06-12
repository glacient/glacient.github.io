# Glacient Docs

The source for the Glacient documentation site, published at <https://docs.glacient.ai>.

Built with Jekyll. GitHub Pages deploys the site from `main` via the workflow in `.github/workflows/jekyll-gh-pages.yml`.

## Structure

```
.
├── _config.yml              Jekyll site config and sidebar nav
├── _layouts/                Page layouts (default, page)
├── _includes/               Topnav, sidebar, footer partials
├── assets/css/main.scss     Theme
├── index.md                 Introduction
├── quickstart.md            Quickstart
├── sign-in.md
├── concepts/                Workflows, Triggers, Conditions, Actions, Self-custody
├── canvas/                  Canvas, AI prompt, lifecycle
├── protocols/               Morpho, Aave, Hyperliquid, Polymarket
├── notifications/           Telegram, alert lifecycle
├── spaces/                  Spaces overview and sharing
├── security.md
└── reference/               Metrics, operators, chains
```

## Local development

### Prerequisites (macOS)

GitHub Pages pins an older Jekyll (3.9.x) that requires **Ruby 3.3.x**. The system Ruby at `/usr/bin/ruby` is too old (2.6), and the latest Homebrew Ruby (4.0+) is too new — its stdlib dropped `csv`, and the old liquid gem still calls the long-removed `String#tainted?`. Install Ruby 3.3 explicitly:

```sh
brew install ruby@3.3
```

Add it to your shell's PATH ahead of the system Ruby. Append to `~/.zshrc`:

```sh
export PATH="/opt/homebrew/opt/ruby@3.3/bin:$PATH"
```

Then reload and verify:

```sh
source ~/.zshrc
ruby --version   # should print ruby 3.3.x
```

This only changes which Ruby your shell finds first. The system Ruby at `/usr/bin/ruby` is untouched.

Install Bundler if you don't have it:

```sh
gem install bundler
```

### Run the site

From the repo root:

```sh
bundle install
bundle exec jekyll serve --livereload
```

Open <http://127.0.0.1:4000/>. With `--livereload`, edits to Markdown and CSS reload the browser automatically.

### Switching Ruby versions

If you previously ran `bundle install` under a different Ruby (you'll see native-extension errors or "cannot load such file" messages), wipe the locked deps and reinstall:

```sh
rm -rf vendor Gemfile.lock
bundle install
```

### Preview without local setup

You can also push a feature branch and open a draft PR — GitHub Pages will build a preview.

## Adding a page

1. Create the Markdown file in the right directory.
2. Add the frontmatter:
   ```yaml
   ---
   title: Page title
   eyebrow: Section name
   summary: One-sentence summary that becomes the lede.
   permalink: /path/to/page/
   ---
   ```
3. Register the page in the `nav` array in `_config.yml` so it shows up in the sidebar.

# zola-silk

Silk is a clean, responsive blog theme for [Zola](https://www.getzola.org/)

![silk screenshot](docs/screenshot.png)

## Features

- Minimalistic design
- Default robots.txt with AI bots prevention
- Responsive
- Syntax highlighting
- Math formula support
- Social media links
- Instant page prefetching
- Fontawesome icons
- Table, Figure shortcodes
- RSS feed
- Pagination
- Anchor links
- Customizable footer, favicon, copyright, subtitle, social media links, and more

## Installation

First download this theme to your `themes` directory:

```bash
git submodule add https://github.com/DenysVuika/zola-silk themes/silk
```

and then enable it in your `config.toml`:

```toml
theme = "silk"
```

The theme requires putting the posts in the root of the `content` folder and to enable pagination,
for example in `content/_index.md`.

```
+++
paginate_by = 5
sort_by = "date"
insert_anchor_links = "right"
+++
```

## Updating theme

To get the latest version of the theme:

```bash
cd themes/zola-silk
git pull --rebase
```

## Reference guides

## Configuration Options

```toml
[extra]
# A line to display underneath the main title
subtitle = "Example subtitle"

# Text to display in the footer of the page
copyright = "Copyright details"

# Your Google Analytics ID
analytics = ""

# See below
katex_enable = false

# See below
instantpage_enable = false

[extra.silk]

# Social media headers
social_mastodon = "@account"

# Social icons
social_icons = [
  { url = "https://mastodon.social/@account", title = "Mastodon", icon = "mastodon" },
  { url = "https://github.com/account", title = "GitHub", icon = "github" },
  { url = "$BASE_URL/atom.xml", title = "RSS", icon = "rss" },
]

[extra.silk.favicon]

# [recommended] a SVG favicon
# svg = "/images/favicon.svg"

# [recommended] generate a 32px PNG favicon from the SVG
# png = "/images/favicon-32x32.png"

# [recommended] generate either a 180px or a 192px PNG image
# 180px - if you want to use the size recommended by apple
# 192px - if you want to use a single 192px image both for apple devices and for
# the android web app manifest; the image will be automatically resized to 180px
# for apple devices
# apple = "/images/apple-touch-icon.png"
```

See `config.toml` for more options.

Note how theme also expects `title` and `description` to also be set in the Zola configuration.

### KaTeX math formula support

This theme contains math formula support using [KaTeX](https://katex.org/), which can be enabled by setting `katex_enable = true` in the `extra` section of `config.toml`.

After enabling this extension, the `katex` short code can be used in documents:
* `{% katex(block=true) %}\KaTeX{% end %}` to typeset a block of math formulas,
  similar to `$$...$$` in LaTeX

### Figure Shortcode

The figure shortcode is convenient for captioning figures.

```
{% figure(link="https://www.example.com/", src="https://www.example.com/img.jpeg", alt="sample alt text") %}
Your caption here.
{% end %}
```

### Table Shortcode

The table shortcode is convenient for making mobile-friendly tables (centered with overflow scrollbar).

```
{% table() %}
| Item         | Price | # In stock |
| :----------- | ----: | ---------: |
| Juicy Apples |  1.99 |        739 |
| Bananas      |  1.89 |          6 |
{% end %}
```

### Fontawesome

This theme includes fontawesome, so that fontawesome icons can be directly used.

### Instant.page

The theme contains instant.page prefetching. This can be enabled by setting `instantpage_enable = true` in the `extra` section of `config.toml`.

## Showing article summaries

By default, the theme will use the first 280 characters of your post as a summary, if a proper [page summary](https://www.getzola.org/documentation/content/page/#summary) using `<!-- more -->` is not provided.
For more sensible summaries, we recommend using the manual more indicator.

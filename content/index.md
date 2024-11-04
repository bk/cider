---
title: Cider
layout: base
exclude_from_nav: true
---

# Cider

**Cider** is a simple, elegant, and responsive wmk theme for product, project, or company sites.

- Built for product sites
- Simple and intuitive structure
- Clean and elegant design
- Responsive and mobile device compatible
- Easy to customize and extend

Cider is a port of the excellent [Juice](https://juice.huhu.io/) theme for Zola.

# Getting started

1. Start by [installing wmk](https://wmk.baldr.net/installation/), if you haven't already.
2. Create your project directory and place your Markdown or HTML content in the `content/` subdirectory.
3. Create a `wmk_config.yaml` file containing the line `theme: cider`
4. In the `theme/` subdirectory of your project, run the command `git clone https://github.com/bk/cider` (or add it as a submodule, or clone/copy it elsewhere and point to it with a symbolic link).
5. Run `wmk b .` in your project directory to build your site.
6. Examine your site, e.g. by running `wmk s .` and pointing your browser to `http://localhost:7007/`.
7. Once you're satisfied with the result, deploy the files from `htdocs/` to your web host.

# Structure

## Hero

**Cider** is designed for product websites with a handful of subpages.

On such sites it is normal to start with a "hero" on the home page, i.e. a graphically striking section that fills the whole screen regardless of the size of the browser window.

In order to activate this, you should set `layout: base` in the YAML frontmatter of your `index.md` file and either create a new `_hero.html` in your `templates/` directory (overriding the one provided by the theme), or add something like `hero_component: _some_filename_here.html` to the frontmatter and create the corresponding template file.

## Pages

Every markdown file located in `content` directory will become a page and will be linked to from the navigation menu in the upper right corner (in desktop) or top center below the title (in mobile). The pages are ordered by the value of `weight` in the frontmatter, and the homepage will be omitted automatically.

In order to exclude a page from the nav, you can add `exclude_from_nav: true` to the frontmatter.

## CSS variables

You can override the theme's CSS variables by creating a file named `_variables.html` in your `templates` directory. The default version of the file is similar to the following:

```html
<style>
    :root {
        /* Primary theme color */
        --primary-color: #FED43F;
        /* Primary theme text color */
        --primary-text-color: #543631;
        --primary-text-color-over: #000;
        /* Primary theme link color */
        --primary-link-color: #F9BB2D;
        /* Secondary color: the background body color */
        --secondary-color: #fcfaf6;
        --secondary-text-color: #303030;
        /* Highlight text color of table of content */
        --toc-highlight-text-color: #d46e13;
        --toc-background-color: white;
        --code-color: #4a4a4a;
        --code-background-color: white;
        --shadow-color: #ddd;

        /* Font used for headers (h1 & h2) */
        --header-font-family: "Fira Sans", sans-serif;
        /* Font used for text */
        --text-font-family: "Fira Sans", sans-serif;
        /* Font used for hero/logo */
        --logo-font-family: "Alfa Slab One", serif;
    }

    @media (prefers-color-scheme: dark) {
        :root {
            --primary-color: #382929;
            --primary-text-color: #d7d7d7;
            --primary-text-color-over: #FFF;
            --primary-link-color: #9b9b9b;
            --secondary-color: #282828;
            --secondary-text-color: #f2f2f2;
            --toc-highlight-text-color: #f2f2f2;
            --toc-background-color: #3a3a3a;
            --code-color: white;
            --code-background-color: #4a4a4a;
            --shadow-color: #202020;
        }
    }
</style>
```

## Fonts

If you changed the `--*-font-family`-variables in `_variables.html`, you should also override the `_fonts.html` template, which by default loads Alfa Slab One and Fira Sans from Google Fonts.

## Sidebar

**Cinder** has an optional sidebar on the right side of the page (in desktop width). You can customize it by overriding the `_sidebar.html` template, or by setting a `sidebar_component` variable in the frontmatter of your page.

If you want to remove the sidebar entirely, either create an empty `_sidebar.html` template file, or set the page variable `no_sidebar` to a true value.

# Configuration

Cider uses a few configuration settings under the key `cider` in `site.extra`. You can add them directly to `wmk_config.yaml` or in a separate file file under `wmk_config.d/`. For instance, `wmk_config.d/site/extra.yaml` might contain the following:

```yaml
cider:
  logo_name: Cider
  logo_path: /cider.png
  extra_menu:
    - title: Github
      link: https://github.com/bk/cider
  footer_text: |
    <a href="https://github.com/bk/wmk">Built by wmk</a>
```

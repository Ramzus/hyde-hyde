# Hyde-hyde (Fork)

> **🍴 This is a fork of the original [Hyde-hyde](https://github.com/htr3n/hyde-hyde) theme by [@htr3n](https://github.com/htr3n)**

__`Hyde-hyde`__ is a [Hugo](https://gohugo.io)'s theme inspired and derived from @spf13's [Hyde](https://github.com/spf13/hyde.git) and [Nate Finch's blog](https://npf.io). 

## About This Fork

This repository is a fork of the original hyde-hyde theme. The original theme can be found at [htr3n/hyde-hyde](https://github.com/htr3n/hyde-hyde).

### Fork Objectives

This fork aims to:
- Continue maintenance and development of the hyde-hyde theme
- Address any outstanding issues and feature requests
- Provide ongoing support for the Hugo community
- Maintain compatibility with newer Hugo versions

### Differences from Original

Currently, this fork maintains compatibility with the original theme. Any significant changes or improvements will be documented here.

#### New Features in This Fork

* **Customizable Sidebar Color**: Added `sidebarColor` parameter in `config.toml` to easily customize the sidebar background color. Set `sidebarColor = "#your-color"` in the `[params]` section.
* **Wonderful Sidebar Animation**: Added `sidebarAnimation` parameter to enable a stunning multi-layered animation effect on the sidebar. Set `sidebarAnimation = true` to enable.

### Repository Status
[![MIT license](https://img.shields.io/badge/License-MIT-blue.svg?style=flat)](https://github.com/ramzus/hyde-hyde/blob/main/LICENSE.md) ![GitHub stars](https://img.shields.io/github/stars/ramzus/hyde-hyde.svg) ![GitHub forks](https://img.shields.io/github/forks/ramzus/hyde-hyde.svg) ![GitHub issues](https://img.shields.io/github/issues/ramzus/hyde-hyde.svg)

## Breaking Changes

Since version 2.0, __`hyde-hyde`__ has been overhauled and, therefore, might cause some disruptions.

* The main styles are refactored and redeveloped using SCSS (see [_assets/scss_](https://github.com/htr3n/hyde-hyde/blob/master/assets/scss)),  `poole.css` and `hyde.css` are no longer needed because `hyde-hyde.scss` already incorporates relevant elements (I still keep them there for reference purpose)
  * Per PR [#45 by [@jd4no](https://github.com/jd4no), `hyde-hyde` can use SCSSs directly in the templates instead of the generated CSSs. The generated CSSs and the generated resources are still kept in `hyde-hyde` in order to ensure the demo on [Hugo theme site](https://themes.gohugo.io) working.
* The layouts have been heavily restructured and modularised further (see [_layouts_](https://github.com/htr3n/hyde-hyde/blob/master/layouts))
* Adding '[_Portfolio_](https://github.com/htr3n/hyde-hyde/blob/master/layouts/portfolio)' page inspired by Xiaoying Riley (@3rdwave_themes) [Developer-Theme](https://github.com/xriley/developer-theme)
* Switching to use system fonts instead of Web fonts (e.g. privacy issues)
* Experimenting a collapsible menu in mobile mode
* Adding _Table of Contents_
  * Configure using `.Site.Params.toc` with two possible value: "hugo" (using Hugo `{{ .TableOfContents }}`, and "tocbot" (using [Tocbot](https://tscanlin.github.io/tocbot/)), remove `.Site.Params.toc` to disable TOC
  * Tocbot can be configured in [layouts/partials/page-single/footer.html](layouts/partials/page-single/footer.html) with options as described in [its documentation](https://tscanlin.github.io/tocbot/#api)

For more details, please refer to [CHANGELOG](https://github.com/htr3n/hyde-hyde/blob/master/CHANGELOG.md).  A real site in action can be found [here](https://htr3n.github.io) and its [WIP source](https://github.com/htr3n/htr3n-blog) for reference.

## Usage

### Installation

__`Hyde-hyde`__ can be easily installed as many other Hugo themes:

```sh
$ cd HUGO_PROJECT

# clone this fork
$ git clone https://github.com/ramzus/hyde-hyde.git themes/hyde-hyde

# or add this fork as a submodule
$ git submodule add https://github.com/ramzus/hyde-hyde.git themes/hyde-hyde

# alternatively, use the original repository
$ git clone https://github.com/htr3n/hyde-hyde.git themes/hyde-hyde
# or
$ git submodule add https://github.com/htr3n/hyde-hyde.git themes/hyde-hyde
```

After that, choose `hyde-hyde` as the main theme.

* `config.toml` 

```toml
theme = "hyde-hyde"
```

* `config.yaml`

```yaml
theme : "hyde-hyde"
```

That's all. You can render your site using `hugo` and see `hyde-hyde` in action.

### Development

To serve the theme for development purposes, you can use the included example site:

```sh
# From the theme root directory
$ hugo server --source exampleSite/ --themesDir ../..
```

This command will:
- Use the `exampleSite/` directory as the Hugo site source
- Set the themes directory to point to the parent directories (where this theme is located)
- Start a local development server with live reload

The development server will typically be available at `http://localhost:1313` and will automatically reload when you make changes to the theme files.

### Options

__`Hyde-hyde`__ essentially inherits most of Hyde's [options](https://github.com/spf13/hyde#options). There are some extra options though

* `highlightjs = true`: use [highlight.js](https://highlightjs.org) instead of Hugo built-in support for code highlighting

  * `highlightjsstyle="highlight-style"`: only when `highlightjs = true`, please choose one of many _highlight.js_'s [styles](https://highlightjs.org/static/demo).
  * Since [v2.0.1](https://github.com/htr3n/hyde-hyde/tree/v2.0.1), highlighting for each page can be fine-tuned in the front matter, for example
    * `highlight = false`  (default `true`)
    * `highlightjslanguages = ["swift", "objectivec"]` 

* `postNavigation = true|false` (default `true`): Setting to `false` will disable the navigation _Previous Post_/ _Next Post_

* `relatedPosts = false|true` (default `false`): Setting to `true` allows related posts. Please refer [here](https://gohugo.io/content-management/related) for more details on related contents with Hugo.

* `GraphCommentId = "your-graphcomment-id"`: to use [GraphComment](https://graphcomment.com) instead of the built-in [Disqus](https://disqus.com). This option should be used exclusively with `disqusShortname = "disqus-shortname"`.

* `UtterancesRepo = "owner/repo-name"`: to use [Utterances](https://utteranc.es/) instead of the built-in [Disqus](https://disqus.com). This option should be used exclusively with `disqusShortname = "disqus-shortname"`.
  * `UtterancesIssueTerm = "pathname"` Method for Utterances to match issue's to posts (pathname, url, title, og:title)
  * `UtterancesTheme = "github-light"` Theme for Utterances (github-light, github-dark)

* `Commento = true`: to use [Commento](https://commento.io/) instead of the built-in [Disqus](https://disqus.com). This option should be used exclusively with `disqusShortname = "disqus-shortname"`.
  * `CommentoHost = "your-commento-instance"` [Self-hosted Commento](https://docs.commento.io/installation/self-hosting/) instance. This is not required if you're a [Commento.io](https://commento.io) user.

* `[params.social]`: in this section, you can set many social identities such as Twitter, Facebook, Github, Bitbucket, Gitlab, Instagram, LinkedIn, StackOverflow, Medium, Xing, Keybase.

  ```toml
  [params.social]
  	twitter = "htr3n"
  	keybase = "htr3n"
  	github = "htr3n"
  	...
  ```

* `sidebarColor = "#300030"`: Setting a custom color for the sidebar background. Any valid CSS color value can be used (hex, rgb, hsl, color names, etc.).

  ```toml
  [params]
  	sidebarColor = "#2c3e50"  # Dark blue-gray
  	# or
  	sidebarColor = "rgb(44, 62, 80)"
  	# or  
  	sidebarColor = "darkslateblue"
  ```

* `sidebarAnimation = true|false` (default `false`): Enable a wonderful multi-layered animation effect on the sidebar background.

  ```toml
  [params]
  	sidebarAnimation = true  # Enable wonderful sidebar animation
  ```
  
*  `include_toc = false`: Setting to `false` in FrontMatter will disable too short TOC data as your want. 

  * Per PR [#56](https://github.com/htr3n/hyde-hyde/commit/5ed13e17400bbc09a342b60fd50cd9fe3e6f1525), Gravatar pics can be used exclusively to `.Site.Params.authorimage` via the parameter `.Site.Params.social.gravatar`

    * ```toml
      [params.social]
      	gravatar = "your.email@domain.com"
      ```

### Customisations

* Most of the customisable SCSS styles in [_assets/scss/hyde-hyde_](https://github.com/htr3n/hyde-hyde/blob/master/assets/scss/hyde-hyde) and Hugo templates in [_hyde-hyde/layouts_](https://github.com/htr3n/hyde-hyde/blob/master/layouts) are modularised and can be altered/adapted easily.

#### Custom Sidebar Color

You can customize the sidebar color by setting the `sidebarColor` parameter in your `config.toml`:

```toml
[params]
sidebarColor = "#2c3e50"  # Dark blue-gray
```

Any valid CSS color value is supported:
```toml
[params]
sidebarColor = "#ff6b6b"           # Hex color
# or
sidebarColor = "rgb(255, 107, 107)" # RGB color  
# or
sidebarColor = "darkslateblue"      # Color name
```

#### Wonderful Sidebar Animation

You can enable a stunning multi-layered animation on the sidebar:

```toml
[params]
sidebarAnimation = true  # Enable wonderful sidebar animation
sidebarColor = "#001f3f" # Works amazingly with any color
```

This animation creates a wonderful visual experience with multiple layers:

- **🌈 Shifting Gradients**: Smooth color transitions that flow across the sidebar
- **✨ Floating Particles**: Delicate light points that gently float and rotate
- **🎨 Dual-layered Depth**: Two independent animation layers create rich visual depth

The combined effect is elegant yet professional, creating a sidebar that feels alive and dynamic while maintaining readability and sophistication. This animation works beautifully with any sidebar color and adds a premium, modern feel to your site.

## Portfolio

Since version 2.0+, I added a portfolio page just in case. If you need it, simply add a menu section '_Portfolio_' in `config.toml` as following.

```toml
[[menu.main]]
    name = "Portfolio"
    identifier = "portfolio"
    weight = xyz
    url = "/portfolio/"
```

In the folder `content` , create a subfolder `portfolio` and use the following folder/content structure as reference.

```
$ tree portfolio
portfolio
├── _index.md
├── p1.md
├── p1.png
├── p2.md
├── p2.png
    ...
├── pn.md
└── pn.png
```

As I design the section _portfolio_ to be rendered as _list_,  `_index.md` can be used to set the title for your portfolio (you can read more about `_index.md` [here](https://gohugo.io/content-management/organization/#index-pages-index-md)). For instance, when I want to set the title of my portfolio "_Projects_", the front matter of `_index.md` will be:

```markdown
---
title: 'Projects'
---
```
The remaining of `_index.md` will be ignored.

For each project, just create a Markdown file with the following parameters in the front matter:

```markdown
---
title: "Project P1's Title"
description: "A short description"
date: '2018-01-02'
link: 'https://project-p1.com'
screenshot: 'p1.png'
layout: 'portfolio'
featured: true
---
Here is a longer summary of the project. You can write as long as you wish.
```

> __Note__:
>
> * `date` is important to sort the project chronologically
> * `layout 'portfolio'` is important as you don't want your project's page appear in the list of posts in the main page of your Web site but only in the _Portfolio_ ;)
> * `featured: true` : when you want to show a project as featured project. It is default to `false`. Note that only one project should be marked `featured: true` , otherwise, the result could be random as [the Hugo template](https://github.com/htr3n/hyde-hyde/blob/master/layouts/partials/portfolio/content.html) will take the first one.
> * The body of the Markdown file will be the summary of the project.

If you want to adjust the portfolio page to your needs, please have a look at the [main template](https://github.com/htr3n/hyde-hyde/blob/master/layouts/portfolio/list.html), that uses this [partial template](https://github.com/htr3n/hyde-hyde/blob/master/layouts/partials/portfolio/content.html) and [this SCSS style](https://github.com/htr3n/hyde-hyde/blob/master/assets/scss/hyde-hyde/_project.scss).

### Posts in home page
By default hugo will show in your home page the most populated section.
This means that if you have more projects than posts, by default your home page will list your projects instead of your posts.
If you want to change this behaviour you can change the [mainsections](https://gohugo.io/functions/where/#mainsections).
For example, for the [exampleSite](https://github.com/htr3n/hyde-hyde/tree/master/exampleSite) this is how you should change the `config.toml` file:
```
[params]
    mainSections = ["posts"]
```

## Some Screenshots

### Main page

![hyde-hyde main screen](https://github.com/htr3n/hyde-hyde/raw/master/images/main.png)

### A post

![A post in hyde-hyde](https://github.com/htr3n/hyde-hyde/raw/master/images/post.png)

### Portfolio

![Portfolio hyde-hyde](https://github.com/htr3n/hyde-hyde/raw/master/images/portfolio.png)



### Mobile Mode with Collapsible Menu

<img src='https://github.com/htr3n/hyde-hyde/raw/master/images/mobile.png' alt='hyde-hyde in mobile mode' width='60%'>

## Contributing

Contributions to this fork are welcome! Please feel free to:
- Report issues
- Submit pull requests
- Suggest improvements
- Help with documentation

For issues related to the original theme design or architecture, you may also want to check the [original repository](https://github.com/htr3n/hyde-hyde) for context.

## Author(s)

* **Original Hyde theme** developed by [Mark Otto](https://github.com/mdo)
* **Hugo's `hyde` port** by [Steve Francia](https://github.com/spf13)
* **Hyde-hyde theme** developed by [@htr3n](https://github.com/htr3n) - [Original Repository](https://github.com/htr3n/hyde-hyde)
* **This fork** maintained by [@ramzus](https://github.com/ramzus)

## Original Repository

This is a fork of the original hyde-hyde theme. For the original work, issues, and discussions, please visit:
- **Original Repository**: [htr3n/hyde-hyde](https://github.com/htr3n/hyde-hyde)
- **Original Author**: [@htr3n](https://github.com/htr3n)

## License

Open sourced under the [MIT license](LICENSE.md)

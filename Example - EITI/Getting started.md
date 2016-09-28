# What starts it all?

For EITI, we are using a combination of npm and Jekyll to create the html pages that are eventually displayed to the user.

[npm](https://www.npmjs.com/) can be be found in the [package.json](https://github.com/18F/doi-extractives-data/blob/dev/package.json) file, and is essentially a list of javascript packages that we are using for data transformations and visualizations, and commands that we can run to build and test our site. When it comes to 'running' the site, think of npm as command central, dictating when our suite of tools do what.

To run the site, type `npm run start` into your terminal. This delegates to Jekyll, running the `bundle exec jekyll serve --incrimental` command.

[Jekyll](https://jekyllrb.com/) is the framework that EITI is built around. It is a static site generator, which means that it is a magic black box that turns a wacky file structure of templates, scripts, and stylesheets into a neatly packaged set of HTML files. The neat package is `_site`, and is created or updated everytime `bundle exec jeykll serve` is run. If you open any of the `index.html` files in that directory with a browser, you will see that page!

We could simply have a `_site` directory and edit every page in our site as pure HTML, but this would get incredibly tedius. Many of the pages are over 10,000 lines long with a lot of duplication. Jekyll allows us to arrive at this end result, while enabling us to create layouts for pages with similar structure and succinct templates that have logic to make our lives easier.

# More on how Jekyll works

Every jekyll project has a [_config.yml](https://github.com/18F/doi-extractives-data/blob/dev/_config.yml) file that tells Jekyll what to do. For EITI, this mostly contains details about which files to exclude when we are bundling things, and file structure for different collections of content.

## Pages and posts

Jekyll has two major categories for content: [pages](https://jekyllrb.com/docs/pages/) and [posts](http://jekyllrb.com/docs/posts/).


### Pages

The building block of a jekyll site is a page. A page has both text and  a specified layout which tells Jekyll how to turn that text into appropriate HTML. All pages have [front matter](https://jekyllrb.com/docs/frontmatter/) which is a set of page attributes sandwiched between two sets of three dashes, that signal to Jekyll that the contents of the file should be built as HTML.

```
---
layout: page
title: Some slick title
---
```

### Posts

Because Jekyll is often used as a blogging platform, one of its defining features is the ability to manage time-stamped content. This means that Jekyll comes with default functionality that transforms files within the `_posts` and sets the default layout for those pages as 'post'. Jekyll also comes with a `_drafts` directory that allows you to have posts without a date.

## Collections

When a number of pages on a site share similar content or can be otherwise categorized together, Jekyll uses its handy [collections](https://jekyllrb.com/docs/collections/) feature and groups these files into a common URL structure. Examples of this for EITI are `case-studies`, `how-it-works`, `explore`, and `downloads`.


## Layouts

When we are creating a page, we need to specify a layout, like in the above example. When a layout is referenced for a page, Jekyll inserts the contents of that page into the `{{ content }}` defined in that layout and builds it!

For example, the base layout that EITI is uses can be found in `_layouts` as [default.html](https://github.com/18F/doi-extractives-data/blob/dev/_layouts/default.html). In Jekyll, if no layout is specified in a page, it will actually look for `default.html`, and render accordingly if available.

For the EITI homepage, we can find this reference in the front matter of [index.html](https://github.com/18F/doi-extractives-data/blob/dev/index.html#L2). When Jekyll builds the site, it will plop the entire contents of this file into the [{{ content }} brackets here](https://github.com/18F/doi-extractives-data/blob/dev/_layouts/default.html#L63)

## Liquid

So that is all well and good, but what in the heck are those double curly braces all about?? By default, Jekyll uses a templating language called [Liquid](https://shopify.github.io/liquid/), that was created by Shopify for use in their websites. There are a bunch of templating engines out there, and while Liquid is probably not my favorite, it is what Jekyll uses, and has a bunch of nice features. Those features include, but are not limited to: includes, logic, variables, and filters. Let's unpack some of that.

### Includes

### Logic

### Variables

### Filters






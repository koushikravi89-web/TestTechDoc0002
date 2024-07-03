## TechDocs and MkDocs

[TechDocs](https://backstage.io/docs/features/techdocs/) uses [MkDocs](https://www.mkdocs.org/) as its Markdown building tool.

MkDocs, in turn, uses the [Python Markdown](https://python-markdown.github.io/) library to translate Markdown .MD files into .HTML websites.

Therefore, your Markdown content can be enhanced and visually enriched by using supported [MkDocs Extensions](https://www.mkdocs.org/user-guide/configuration/#markdown_extensions) and [Python Markdown Extensions](https://python-markdown.github.io/extensions/).


## Supported MkDocs Extensions

As mentioned in the [Backstage documentation](https://backstage.io/docs/features/techdocs/how-to-guides/#how-to-use-other-mkdocs-plugins), a TechDocs plugin named `mkdocs-techdocs-core` is enabled by default within the XELERATE's TechDocs backend rendering services.

This TechDocs [Core MkDocs plugin](https://github.com/backstage/mkdocs-techdocs-core) bundles a set of extensions and plugins that MkDocs supports, including all of the following:

**Plugins:**

- [search](https://www.mkdocs.org/user-guide/configuration/#search): A search plugin is provided by default with MkDocs which uses [lunr.js](https://lunrjs.com/) as a search engine.

- [mkdocs-monorepo-plugin](https://github.com/backstage/mkdocs-monorepo-plugin): This plugin enables you to build multiple sets of documentation in a single MkDocs project. It is designed to address writing documentation in Spotify's largest and most business-critical code bases (typically monoliths or monorepos).

**Extensions:**

- [admonition](https://squidfunk.github.io/mkdocs-material/reference/admonitions/#admonitions): Admonitions, also known as call-outs, are an excellent choice for including side content without significantly interrupting the document flow. [Material for MkDocs](https://squidfunk.github.io/mkdocs-material/) provides several different types of admonitions and allows for the inclusion and nesting of arbitrary content.

- [toc](https://python-markdown.github.io/extensions/toc/): The Table of Contents extension generates a Table of Contents from a Markdown document and adds it into the resulting HTML document.

- [markdown_inline_graphviz](https://pypi.org/project/markdown-inline-graphviz/): A Python Markdown extension that replaces inline Graphviz definitions with inline SVGs or PNGs. Activate the inline_graphviz extension using the [usage instructions](https://github.com/sprin/markdown-inline-graphviz#usage).

- [plantuml_markdown](https://pypi.org/project/plantuml-markdown/): This plugin implements a block extension which can be used to specify a PlantUML diagram which will be converted into an image and inserted in the document.
  - Note that the format `svg_object` is not supported for rendering diagrams. Read more in the [TechDocs troubleshooting](https://backstage.io/docs/features/techdocs/troubleshooting#plantuml-with-svg_object-doesnt-render) section.

- [mdx_truly_sane_lists](https://pypi.org/project/mdx-truly-sane-lists/): An extension for Python-Markdown that makes lists truly sane. Features custom indents for nested lists and fix for messy line breaks and paragraphs between lists.

- [pymdown](https://facelessuser.github.io/pymdown-extensions/): PyMdown Extensions is a collection of extensions for Python Markdown. All extensions are found under the module namespace of `pymdownx`.
  - [caret](https://facelessuser.github.io/pymdown-extensions/extensions/caret/): Caret is an extension that is syntactically built around the ^ character. It adds support for inserting superscripts via a `<sup>` tag, and adds an easy way to place text in an `<ins>` tag.
  - [tilde](https://facelessuser.github.io/pymdown-extensions/extensions/tilde/): Tilde is syntactically built around the ~ character. It adds support for inserting subscripts using `<sub>` tags, and adds an easy way to place text in a `<del>` tag.
  - [critic](https://facelessuser.github.io/pymdown-extensions/extensions/critic/): Critic adds handling and support for the tracking of changes (additions, deletions and comments) in documents.
  - [details](https://facelessuser.github.io/pymdown-extensions/extensions/details/): Details creates collapsible elements with `<details>` and `<summary>` tags.
  - [emoji](https://facelessuser.github.io/pymdown-extensions/extensions/emoji/): Emoji makes adding emojis via Markdown easy 😄.
  - [superfences](https://facelessuser.github.io/pymdown-extensions/extensions/superfences/): SuperFences is like Python Markdown's fences, but better. Nest fences under lists, admonitions, and other syntaxes. You can even create special custom fences for content like UML.
  - [inlinehilite](https://facelessuser.github.io/pymdown-extensions/extensions/inlinehilite/): InlineHilite highlights inline code: from module import function as func.
  - [highlight](https://facelessuser.github.io/pymdown-extensions/extensions/highlight/): Highlight allows you to configure the syntax highlighting of SuperFences and InlineHilite. Also passes standard Markdown indented code blocks through the syntax highlighter.
  - [magiclink](https://facelessuser.github.io/pymdown-extensions/extensions/magiclink/): MagicLink linkifies URL and email links without having to wrap them in Markdown syntax. Also, shortens repository issue, pull request, and commit links automatically for popular code hosting providers. You can even use special shorthand syntax to link to issues, diffs, and even mention people
  - [mark](https://facelessuser.github.io/pymdown-extensions/extensions/mark/): Mark allows you to mark words easily.
  - [smartsymbols](https://facelessuser.github.io/pymdown-extensions/extensions/smartsymbols/)**: SmartSymbols inserts commonly used Unicode characters via simple ASCII representations: =/= → ≠.
  - [tabbed](https://facelessuser.github.io/pymdown-extensions/extensions/tabbed/): Tabbed allows for tabbed Markdown content.
  - [tasklist](https://facelessuser.github.io/pymdown-extensions/extensions/tasklist/): Tasklist allows inserting lists with check boxes.    
  - [extra](https://facelessuser.github.io/pymdown-extensions/extensions/extra/): Extra is a bundle of several other extensions including:
    - pymdownx.betterem: Smarter "emphasis" parsing (for **bold** and *italics*)
    - pymdownx.superfences: See above
    - And these [markdown.extensions](https://python-markdown.github.io/extensions/extra/):
      - markdown.extensions.footnotes: 
      - markdown.extensions.[attr_list](https://squidfunk.github.io/mkdocs-material/setup/extensions/python-markdown/#attribute-lists)
      - markdown.extensions.def_list
      - markdown.extensions.tables
      - markdown.extensions.[abbr](https://python-markdown.github.io/extensions/abbreviations/)
      - markdown.extensions.md_in_html


## Built-In MkDocs Extensions

Since all of the above MkDocs Plugins and Extensions are enabled and supported by default, they do *not* need to be individually referenced in your `mkdocs.yml` configuration file.

You only need to add the one `techdocs-core` plugin in your `mkdocs.yml` file to enable all of the above.

```{.yaml linenums="1"}
plugins:
  - techdocs-core
```

By enabling that one `techdocs-core` plugin, you can consider *all* of the content below as being enabled for you to use:

```{.yaml linenums="1"}
plugins:
  - search
  - mkdocs-monorepo-plugin

markdown_extensions:
  - admonition
  - toc

  - pymdownx.caret
  - pymdownx.tilde
  - pymdownx.critic
  - pymdownx.details
  - pymdownx.emoji
  - pymdownx.inlinehilite
  - pymdownx.highlight
  - pymdownx.magiclink
  - pymdownx.mark
  - pymdownx.smartsymbols
  - pymdownx.tabbed
  - pymdownx.tasklist

  - pymdownx.extra

  ## PyMdown.Extra adds the equivalent of ALL the following extensions:
  - pymdownx.betterem
  - pymdownx.superfences
  - markdown.extensions.footnotes
  - markdown.extensions.attr_list
  - markdown.extensions.def_list
  - markdown.extensions.tables
  - markdown.extensions.abbr
  - markdown.extensions.md_in_html

  - inline_graphviz
  - plantuml-markdown
  - mdx_truly_sane_lists
```

## Configuring Built-In Extensions

If you need to specify parameters or configurations details for a specific built-in extension, you will need to add those details into your `mkdocs.yml` file.

In the example below we have add some custom settings for `pymdownx.tabbed`, `pymdownx.emoji`, and `mdx_truly_sane_lists`:

```{.yaml linenums="1"}
plugins:
  - techdocs-core

markdown_extensions:
  - pymdownx.tabbed:
      alternate_style: true
  - pymdownx.emoji:
      emoji_generator: !!python/name:pymdownx.emoji.to_svg
      emoji_index: !!python/name:pymdownx.emoji.emojione
  - mdx_truly_sane_lists:
      nested_indent: 2
      truly_sane: True
```


## Support for Additional Plugins, Extensions, & Themes

Over time, the CARIAD TechDocs implementation will grow and adapt. 

We expect to include support for additional plug-ins and extensions in the near future.

See the [Add-on Extensions & Examples](addon-extensions.md) article for more details.

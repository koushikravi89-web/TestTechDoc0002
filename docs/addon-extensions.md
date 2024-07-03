At this time, additional MkDocs Plugins, Extensions, and Themes are only minimally supported.

We hope to add testing and validation for tools such as the following in the near future:

```{.yaml linenums="1"}
theme:
  name: material

plugins:
  - mkdocs-video
  - mermaid2

markdown_extensions:
  - pymdownx.snippets
  - pymdownx.keys
```

Please contact the XELERATE team to request support for your favorite extension or plug-in!


## Validated Add-on Extensions

As of April, 2024 we have tested and now support the following additional Markdown features for use within the CARIAD TechDocs environment:

- pymdownx.snippets
- pymdownx.keys

## PyMdown Snippets

Reference: https://facelessuser.github.io/pymdown-extensions/extensions/snippets/

PymMdown Snippets is an extension which includes (inserts) Markdown content from one .MD file into another .MD file. 

The Snippets extension is great for single-sourcing content that you need to insert/include into multiple documents, such as creating a single `abbreviations.md` file, but using it to highlight and define words throughout your *entire* set of TechDocs pages.

As an example, we will modify the final example provided in the [Built-in Markdown: Examples > Abbreviations](mkdocs-examples.md/#abbreviations) section by separating the abbreviation definitions into a separate file, and then referencing that new file at the end of the original `mkdocs-examples.md` file.

1. Add `pymdownx.snippets` to your `mkdocs.yml`.

  PyMdown Snippets is not added to the TechDocs installation by default.

  You must edit your `mkdocs.yml` file and add `- pymdownx.snippets` under the `markdown_extensions:` section.

  Example:

  ```
  markdown_extensions:
    - pymdownx.snippets
  ```

2. Create a new `abbreviations.md` file.

  We removed the three definitions from the [Abbreviations](mkdocs-examples.md/#abbreviations) example, and added them into their own `abbreviations.md` file:

  ```
  *[CARIAD]: Car, I Am Digital
  *[IVI]: In-Vehicle Infotainment
  *[GAS]: Google Automotive Services
  ```

  We stored that file in the location: `docs/files/abbreviations.md`.

3. Reference the new file in any/all other .MD files.

  We then added the reference to the `abbreviations.md` file to the bottom of the original "Abbreviations" example .MD file.
    
  The syntax for Snippets (using a "scissors" motif) is: 

  ```
  ;--8<-- "filename.ext"
  ```
  
  We needed to include the relative location of the file based on our Docs file structure, so we added the following to both the original "Abbreviations" example .MD document and to this .MD file as well:
  
  ```
  ;--8<-- "docs/files/abbreviations.md"
  ```

Result:

The Clipper Project will extend CARIAD's IVI offering with a GAS-Variant.

--8<-- "docs/files/abbreviations.md"


## PyMdown Keys

Reference: https://facelessuser.github.io/pymdown-extensions/extensions/keys/

The PyMdown Keys extension adds a simple way to render keyboard keys within your documents.

### Native keyboard syntax

The following syntax can be used "out of the box" to render generic keyboard keys:

Example:

```
<kbd>Ctrl</kbd> + <kbd>Alt</kbd> + <kbd>Del</kbd>

<kbd>Cmd</kbd> + <kbd>Opt</kbd> + <kbd>P</kbd>
```

Result:

<kbd>Ctrl</kbd> + <kbd>Alt</kbd> + <kbd>Del</kbd>

<kbd>Cmd</kbd> + <kbd>Opt</kbd> + <kbd>P</kbd>

### PyMdown Keys syntax

PyMdown Keys brings a slightly improved look to the keys, and uses a slightly simpler syntax:

Example:

```
++ctrl+alt+del++

++cmd+opt+p++
```

Result:

++ctrl+alt+del++

++cmd+opt+p++

See the [PyMdown Keys](https://facelessuser.github.io/pymdown-extensions/extensions/keys/) Extension documentation for a detailed list of supported keys and their labels.

# Publishing Content: Overview

## Adding Content to XELERATE

There are three unique and separate methods for adding your team's content into XELERATE:

1. Adding [**Entities**](#entities) such as: Systems, Components, API Specifications, Tools, Websites, etc.

2. Adding [**Expository Content**](#expository-content) such as: Guides, Documentation, How-to's and Tutorials.

3. Adding [**Release Notes**](#release-notes) for each new version of your API or service.


## Entities

!!! tip "Everything starts with an Entity"

    - You cannot publish Expository Content ... until you have an Entity to attach the content to.

    - You cannot publish Release Notes ... until you have an Entity to attach the content to.

To add an Entity into the XELERATE Software Catalog, you will:

1. Create a YAML file with in your repo.
2. Define your entity in that YAML file (using the standards that are described in the following articles).
3. Grant the XELERATE App "read-only access" to your repo.
4. Import your YAML file into the Software Catalog.

Once added, XELERATE will monitor your catalog file (and any other files your YAML file references, like Swagger specifications) for any changes and will automatically import your updates in near-real time (about 90 seconds or less). 

No action is required on your part for updates and changes make to your catalog entry to be automatically ingested and displayed in XELERATE.

**Entity Next Step:** 

- For details on creating your catalog entry YAML file, see: [Catalog Entities](./entities.md).


## Expository Content

Once an entity has been added for your team's tool, service, or system, you can attach expository content to that entity such as Guides, Documentations, Tutorials, or other long-form content.

Backstage uses **Markdown** as it's primary source material for adding long-form content.

More specifically, Backstage uses a home-grown tool call **TechDocs** that leverages an open source Markdown standard from **MkDocs**.

At this time all expository guides and documentation you want to publish into XELERATE *must* be in MkDocs-compatible .md files, and *should* be published using the TechDocs CLI tools.

!!! abstract "References"
    - More info on the [MkDocs standard](https://www.mkdocs.org/).
    - More info on Backstage.io's [TechDocs](https://backstage.io/docs/features/techdocs/).
    - More info on Backstage.io's [TechDocs CLI](https://backstage.io/docs/features/techdocs/concepts/#techdocs-cli).

**Markdown Next Step:** 

- For details on creating and publishing your Markdown content see: [Publishing Markdown](./guide-publishing.md).


## Release Notes

Support for automated Release Note publishing was added in early 2024 by the XELERATE Development Team.

**Release Notes Next Step:** 

- For details on publishing Release Notes to your Service or API see: [Publishing Release Notes](./release-notes.md).

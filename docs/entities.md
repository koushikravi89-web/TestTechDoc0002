# XELERATE Entity Model

The XELERATE Software Catalog is constructed primarily from these main kinds of entities:

- Domains
- Groups (or Teams)
- Users
- Systems
- Components
- APIs

The relationships between these entities is shown in the following diagram:

![Entities](./img/entities.png)

In general, the following guidelines apply to these main entities:

- Only XELERATE Admins can create **Users**, **Groups/Teams**, and **Domains**.
- Anyone at CARIAD can create and publish **Systems**, **Components**, and **APIs**.
- Systems, Components, and APIs are owned by a specific **Group/Team**.
- Systems *may* be associated with a Domain.
- Components and APIs *may* be associated with Systems.
- Components *may* also be associated with APIs.
- **TechDocs** (Guides) are *not* entities themselves, but are associated to an entity:
  - TechDocs can be associated to both Systems and Components.
  - TechDocs can only be published by an authorized **User**.

For more detail on the Backstage.io entity model and options see: https://backstage.io/docs/features/software-catalog/system-model.


## Systems, Components, and APIs

The **System** entity is usually the best initial entity for a CARIAD Team to use when publishing their product or service.
 
The System entity will: 

- Act as a the “Front Door” for your team’s product in CARIAD's Backstage environment.
- Be the home page URL for your product.
- Contain your product's: Overview details, Description, and Ownership info (at a minimum).
- Contain your product's: Docs, APIs, and sub-components (as needed).

**Component** and **API** entities comprise all the "functional parts" of a Team’s product or service.

**TechDocs** (Markdown content) is not an actual entity. Instead, TechDocs/.MD content is associated (via `annotations`) to Systems and/or Components.

# Publishing API Specifications


## Add an API Entity

To add an API into the XELERATE Software Catalog, create an entity in [your catalog file](./entity-publishing.md#step-1-create-your-projects-catalog-file)

The API entity should have a `kind: API` declaration using the following settings:

- `name` is a system field used to identify your API. It can contain only lowercase letters, numbers, and dashes.
- `title` is a human-readable display name for your API. It can contain upper and lowercase letters, spaces, and special characters. It should be short, but long enough to distinguish it from other services. For example, "Data API" may be clear in the context of your project, but it is not specific enough in a general context. If the API is part of the "Frobs" platform, it could be named the "Frobs Data API".
- `description` describes the entity to be shown in XELERATE. It should be kept short and informative; suitable to give an overview of the entity's purpose at a glance. More detailed explanations and documentation should be placed elsewhere.
- `owner` refers to the owning team. It is probably the same as your `System`'s owner, and can contain only lowercase letters, numbers, and dashes.
- `type` is the type of the API definition: openapi, asyncapi, graphql, or grpc.  Learn more about these options in the [Backstage project documentation](https://backstage.io/docs/features/software-catalog/descriptor-format/#spectype-required-2).
- `definition:$text` is a link to the API specification/definition file. For example, an API of `type: openapi` would require a relative URL pointing to the OAS/Swagger file for the API specification.


## Example API Entity

```yaml
--- # dashes separate the API from other entities in the same file
apiVersion: backstage.io/v1alpha1
kind: API
spec:
  type: openapi
  owner: frobs-data-team
  system: frobs
  lifecycle: production
  definition:
    $text: ./api/frobs-data-api.json   # A relative link to your API spec file
metadata:
  name: frobs-data-api
  title: Frobs Data API
  description: Used to retrieve the data stream for updates to the frobs project.
```


## API Specification File

In order to create a visual representation of your API, XELERATE needs to reference an API spec file in a [compatible format](https://backstage.io/docs/features/software-catalog/descriptor-format/#kind-api), such as OpenAPI. This file must be checked into the **same repository as your catalog file** and linked in the `spec.definition.$text` entry of your API entity. 

See the example below for how to create the reference.

```yaml
  definition:
    # This OpenAPI Swagger YAML file location is relative to the catalog file.
    $text: ./spec/frobs-data-api-swagger.json
```


## Create a Relationship Between an API and a Component

XELERATE will not automatically infer any relationship between two files in the same catalog file. 

You must add an annotation to your component to show that it provides the new API entity. 

Add a `providesApis` entry under the `spec` field in your `component`:

```yaml
kind: Component
spec:
  providesApis:
    - frobs-data-api # the value of the API's metadata.name field
metadata:
  name: my-awesome-project
```

If you have additional APIs, you can add additional relationships. 

Each API relationship should be on its own line under the `providesApis` entry:

```yaml
spec:
  providesApis:
    - frobs-data-api
    - another-frobs-api
```


## Publish Your Changes

Based on the above examples, your catalog file might now contain the following changes:

1. A new entity of **kind: API** with a reference to your API specification file.

2. A `spec.providesApi` entry on your component with a reference to your new API entity.

Commit these changes in your repository and merge them into the branch that contains your catalog file. 

Backstage will automatically detect the changes and update the software catalog.

If you're not sure where to find your catalog file, [see the instructions here](faq.md).


## Additional API Options

For more options on configuring the API entities, see the [Backstage Documentation](https://backstage.io/docs/features/software-catalog/descriptor-format#kind-api).


## Enabling TryIt Features

XELERATE provides an integrated UI to "Try It" for every API in the catalog. 

The TryIt feature can help users of the site construct and send requests to APIs directly from their browser. 

To make this work, your API spec file needs **server** and **security scheme** entries that support "TryIt".

### Servers

Your API spec can contain a [list of servers](https://spec.openapis.org/oas/v3.1.0#server-object) that provide this API. 

For each server in this list that supports the "TryIt" feature, ensure that the server includes XELERATE ( https://developer.cariad.digital/) in it's CORS allowed origins. 

For more information, please see the documentation for your server technology.

### Security schemes

XELERATE will assist users in creating requests to your API, but it will not help them by providing any access or authentication to your API. 

To allow users to authenticate, include a [security scheme](https://spec.openapis.org/oas/v3.1.0#security-scheme-object) and directions for how to create an identity in your authentication server.

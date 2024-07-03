# Self-Publishing Markdown Documentation

XELERATE provides a docs-as-code feature called TechDocs. This allows you to keep Markdown-based documentation and guides alongside your source code, preview the documentation locally, and self-publish it to XELERATE so that it can be accessed from within the software catalog.

**NOTE:** If you already have quality documentation and do not wish to migrate it to TechDocs, please [link to it from your entity page](onboarding.md).


## Structuring Your Documentation

XELERATE leverages [TechDocs](https://backstage.io/docs/features/techdocs/), generated using MkDocs (requires Node and Docker).

### `mkdocs.yml`

Add a `mkdocs.yml` config file used by MkDocs for taking the markdown files found in this repo and rendering them into an HTML website.

**NOTE:** It is best practice to have mkdocs.yml a peer of your catalog file.

Include `site_name`, `docs_dir`, and a complete Table of Contents (ToC) descriptor tree for navigation (`nav`). See the [Sample Documentation Repo for an example mkdocs.yml](https://github.com/cariad-dxp/docs-sample-repo/blob/main/mkdocs.yml) file.



### `techdocs-ref` annotation

In addition, in the component that you [onboarded](onboarding.md) with your catalog file, adjust it to include the [techdocs-ref annotation](https://backstage.io/docs/features/software-catalog/well-known-annotations#backstageiotechdocs-ref) with a path to where mkdocs.yml can be found.

**Example `techdocs-ref` annotation:**

```yaml
  annotations:
    backstage.io/techdocs-ref: dir:.
```

More details: [Enable documentation for an already existing entity](https://backstage.io/docs/features/techdocs/creating-and-publishing#enable-documentation-for-an-already-existing-entity)

### Build

You can build with `npx @techdocs/cli build` which should add a new `site` folder containing the generated .HTML files.

- [Backstage TechDocs CLI](https://backstage.io/docs/features/techdocs/cli/)
- [Sample Documentation Repo](https://github.com/cariad-dxp/docs-sample-repo)


## Authentication

The requester (e.g., the deployment pipeline) must self-generate an ID token using its local development environment's OIDC token issuer. 

The pipeline will use that token to authenticate with the CARIAD techdocs upload auth endpoint. 

If authenticated correctly, the AUTH service will return an Access Token which the pipeline can then use to upload a file.


### Retrieve Information

In order to authenticate the caller to the XELERATE Public Backend, the XELERATE Team will need:

- **Issuer** - The issuer (The value of the token's `iss`)
- **Subject** - The Subject (The value of the token's `oidc_sub`, `sub`, or a related key)

You can decode your token using https://jwt.io/

![ADO Pipeline Creation](images/decode.png)

### Send Info to XELERATE Team

Make a request to the XELERATE Team through [these channels](faq.md#Contact-Information).

Ensure your message contains the necessary information similar to:

```
Request: To be authorized to make a call to the XELERATE Public Endpoint for Publishing Documentation.
* Token URL From Pipeline: <FILL_ME (i.e. https://token.actions.githubusercontent.com/)>
* Audience from Token: <FILL_ME (i.e. repo:cariad-dxp/developer-experience-react:environment:dxp_production)>
```


## Public Endpoint

The general steps needed in your pipeline:

1. Generate an OIDC JWT ID Token
2. Request and Extract an Access Token from XELERATE AUTH service ([backstage-auth API Reference](https://developer.cariad.digital/catalog/default/api/backstage-auth/definition#/default/))
3. Use TechDocs to build your documentation
4. Bundle the files into a .tar file
5. Publish the .tar website to XELERATE UPLOAD service ([backstage-techdocs-uploader API Reference](https://developer.cariad.digital/catalog/default/api/backstage-techdocs-uploader/definition#/))

Adapt or adjust your automated pipeline as needed to successfully make the API Calls.

For more details, see the:

- [Github example](examples/publish-via-github.md)
- [ADO example](examples/publish-via-ado.md)


## Troubleshooting

### "AuthenticationError" on Auth Refresh

When calling the refresh endpoint, you get an error message similar to this:

```json
{
  "error": {
    "name": "AuthenticationError",
    "message": "Refresh failed; caused by OPError: expected 200 OK, got: 302 Found",
    "cause": {
      "error": "expected 200 OK, got: 302 Found",
      "name": "OPError",
      "message": "expected 200 OK, got: 302 Found",
      "stack": "OPError: expected 200 OK, got: 302 Found\n    at processResponse (/app/node_modules/openid-client/lib/helpers/process_response.js:41:11)\n    at Issuer.discover (/app/node_modules/openid-client/lib/issuer.js:179:18)\n    at process.processTicksAndRejections (node:internal/process/task_queues:95:5)\n    at async IssuerStore.refreshKeyStore (/app/plugins/techdocs-upload-common/dist/index.cjs.js:84:22)\n    at async IssuerStore.verify (/app/plugins/techdocs-upload-common/dist/index.cjs.js:36:5)\n    at async JwtVerifier.verify (/app/plugins/techdocs-upload-common/dist/index.cjs.js:106:10)\n    at async IssuerSubjectResolver.resolver (/app/plugins/techdocs-upload-common/dist/index.cjs.js:145:16)\n    at async Oauth2ProxyAuthProvider.handleResult (/app/node_modules/@backstage/plugin-auth-backend/dist/index.cjs.js:2220:35)\n    at async Oauth2ProxyAuthProvider.refresh (/app/node_modules/@backstage/plugin-auth-backend/dist/index.cjs.js:2209:24)"
    }
  },
  "request": { "method": "GET", "url": "/public/auth/oauth2proxy/refresh/" },
  "response": { "statusCode": 401 }
}
```

**Solution:** The domain may be blocked by Megatron, preventing XELERATE from reaching your catalog file. Reach out to the XELERATE Team for assistance.

### "NotAllowedError" on upload

When calling the techdocs-upload endpoint, you get an error message:

```json
{
  "error": { "name": "NotAllowedError", "message": "Unauthorized" },
  "request": { "method": "PUT", "url": "/default/component/my-cool-component" },
  "response": { "statusCode": 403 }
}
```

**Solution:** Navigate through your entity file and:

- Make sure that the `component` entity exists. If not, import the expected component.

- Look up your User Entity in the pipeline and ensure there is an annotation for it. If it is not present, or you suspect the annotation is incorrect, reach out to the XELERATE Team to make adjustments.

![Ensure the TechDocs Upload Authentication exists for a user](images/techdocsUploadAuthentication.png)
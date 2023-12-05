# Kong Portal Customisation

Specific customisation example.

## Installation

Set this as your current portal markup in the "default" workspace, from the root of this repository, using [Kong Portal CLI](https://github.com/Kong/kong-portal-cli):

```sh
KONG_ADMIN_URL=https://kong-admin.domain.local:443 KONG_ADMIN_TOKEN=abc portal -D deploy default
```

or a Kong running on the local host:

```sh
portal deploy default
```

## Customisation

With these modications, under the `Catalog` screen, when you select an API specification for the detail view instead of going directly to the Swagger UI renderer you are instead directed to "${api_spec_file_name}-detail" index.txt.

This means that you can now created extended Markdown documentation for each API spec under the directory name respective to the API spec file name, in the `./workspaces/default/content/documentation/` parent directory.

The "Petstore" example is provided for you, to demonstrate how this works.

### Dynamic Content

Whilst inside the "petstore-detail" directory under `./workspaces/default/content/documentation/`, you can see that this content is agnostic to the API specification that the user selected - the `index.txt` file designated the API's friendly-name, description, and other metadata, in addition to an array of extra doc pages:

```yaml
topic_pages:
- title: "Subscribing"
  href: "subscribing"
- title: "Usage"
  href: "usage"
```

Each of thesse topic pages will be rendered in the sidebar to the left of the page. It will default to "href: about".
These 'topic' pages correspond to a .md file in the same relative directory. Whilst not rendered dynamically based on the API spec, it hopefully gives you an idea of how you could easily add documentation for each published API specification.

The sidebar menu option "API Spec", in bold, is added to each spec automatically.

## TODO

* Dynamic page listing on the left side

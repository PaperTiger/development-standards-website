{% include _includes/nav.md %}

## Getting Started

### .env
There should be a `.env` file in the root directory of the project. If there isn't copy `.env.example` and name it `.env`. Depending on the project (craft/wordpress/static) you should see different variables that are needed.

The most important and only required variables to start are:
```bash
ENVIRONMENT="dev"
SITE_NAME="Project Name"
WEB_ROOT="/web"
TEMPLATE_DIR="/templates"
GENERATE_LEGACY="false"
DEFAULT_SITE_URL="http://project-name.test"
```

#### `enviroment`
```bash
dev|development # Used for development (BrowserSync, source maps, live reload, etc)
production|live # Used on production servers (minify/gzip, dynamic imports, file spliting)
stage|staging # Used on staging server (file spliting, source maps)
```

#### `SITE_NAME`
This variable is to defined the name of the project. This is used in different places depending on the type of project (craft/wordpress/static).

`WEB_ROOT` - Where the server accesses your app. This can change depending on the type of project:
- Craft: `/web`
- Wordpress: `/wp-content`
- Static: `/web`

`TEMPLATE_DIR` - This is where you add your template or HTML files. These changes based on the type of project.
- Craft: `/templates`
- Wordpress: `/wp-content`
- Static: `/web` or where ever php/html files live.
`GENERATE_LEGACY` - This a Boolean value, and tell Webpack to generate a legacy version of the JS assets so older browsers use ES6+
`DEFAULT_SITE_URL` - This is the site URL being used to view the site.

# Project Type
## Craft
`composer i` Install all dependencies to run.

{% include _includes/nav.md %}
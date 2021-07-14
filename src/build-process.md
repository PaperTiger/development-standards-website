{% include _includes/nav.md %}

## In-Progress

We use Webpack to build and compile all our JS/CSS (sometimes images if needed).

### Commands
- `npm i` Install all node modules used for the project.
- `npm run dev` Run webpack and watch for changes. Used in development. We use browser-sync to look for changes on port 3000. When running you will find the URL once the initial build have finished
- `npm run build` Build a compiled version of all assets. Mainly used in Production environments so unsure all comments/logs are removed, and everything is minified/gzipped.


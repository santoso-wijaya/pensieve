---
title: "Using Material Web Components"
tag: material design
tag: node.js
tag: web component
toc: true
---

# M3 components

## Buttons

<md-outlined-button>Back</md-outlined-button>
<md-filled-button>Next</md-filled-button>
<br />

# Integrating Material Web components into Pensieve

## Self-hosting: install `@material/web`

I want to try using [Material Web 3](https://m3.material.io/develop/web)
components on this site. First, let's install it with NPM.

I created a `package.json` manifest file.

```json
{
  "engines": {
    "node": ">=20.11.1"
  },
  "dependencies": {
    "@material/web": "^1.2.0"
  }
}
```

Now, executing `npm install` will pull Material Web components sources into our
working directory.

## JavaScript: import components

Next, we create `_material.js` script to import the components that we need.

```javascript
import '@material/web/button/filled-button.js';
import '@material/web/button/outlined-button.js';
```

These import statements still need to be rolled up (expanded with the content
of these imported files) before we can use them in the rest of our site, so
we have to add the following in our `package.json` file.

```json
{
  "devDependencies": {
    "@rollup/plugin-node-resolve": "^15.2.3",
    "rollup": "^4.12.0"
  },
  "scripts": {
    "rollup": "rollup -p @rollup/plugin-node-resolve assets/js/_material.js -o assets/js/material.rollup.js",
    "build:js": "npm run rollup"
  }
}
```

Running `npm run build:js` would create the output `material.rollup.js` file.
This is what we need to actually use in our `<head>` script tag.

There are different routes to make this happen. The Minimal Mistakes theme that
I am using defines a config for this. In our `_config.yml` file:

```yaml
head_scripts:
  - /assets/js/material.rollup.js # Generated by `npm run build:js`
```

## Styling M3 components

M3 uses
[design tokens](https://github.com/material-components/material-web/tree/main/docs/theming#tokens)
as an API for styling and customizing their components.

For instance, to change the typography of M3 components that I will use, I just
need to add the following in this site's `main.scss` file.

```scss
/*--- material web customizations ---*/
:root {
  --md-ref-typeface-brand: Roboto;
  --md-ref-typeface-plain: system-ui;
}
/*--- end material web customizations ---*/
```

NOTE: To make Roboto available, I also need to add the fonts in `<head>`.
```yaml
head_scripts:
- https://fonts.googleapis.com/css2?family=Roboto:wght@400;500;700&display=swap
```
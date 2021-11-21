---
name: "Front End"
ordem: 2
rg: "front-end-ptbr-v1"
idioma: "PT-BR"
intenção: "Informações sobre o front-end."
sumário Prático: "Use o front-end."
descrição Mozilla: "Front-end é."
descrição WP: "Front-end é."
descrição W3C: "Front-end é."
descrição Google: "Front-end é."
tempo Estimado: "(1 hora, 30 minutos, 5 horas)" <!-- // (min, tool, hard) -
panorâma histórico: ""
tags: ""
---

# Frontend

Frontend without myths

Canvas

Design

Brand

Code

Pattern and Standarize

Perfomance

Maintenence

Reusability

READEM

dump.sql

docker-compose.yml

php.ini

Dot Config Files

.htaccess

.code-workspace

.gitignore

.editorconfig

.eslintrc.js

.stylelintrc

composer.json

package.json

Scripts

```json
"scripts": {
    "build": "cross-env NODE_ENV=development run-s mix",
    "build:production": "cross-env NODE_ENV=production run-s clean mix",
    "start": "cross-env NODE_ENV=development run-s \"mix -- --watch\"",
    "hot": "cross-env NODE_ENV=development run-s build mix:hot",
    "mix": "webpack --progress --hide-modules --config=node_modules/laravel-mix/setup/webpack.config.js",
    "mix:hot": "webpack-dev-server --inline --hot --config=node_modules/laravel-mix/setup/webpack.config.js",
    "clean": "run-p clean:*",
    "clean:dist": "rimraf dist",
    "clean:cache": "rimraf storage/framework/cache/*.php storage/framework/cache/data/*.php",
    "clean:views": "rimraf storage/framework/views/*.php",
    "lint": "run-s -c lint:*",
    "lint:scripts": "eslint resources/assets/scripts",
    "lint:styles": "stylelint \"resources/assets/**/*.{vue,css,sass,scss,less}\"",
    "test": "run-s -c lint",
    "translate": "run-s -c translate:*",
    "translate:pot": "wp i18n make-pot . ./resources/languages/sage.pot --ignore-domain --include=\"app,resources/assets,resources/views\"",
    "translate:js": "wp i18n make-json ./resources/languages --no-purge --pretty-print"
  }
  "devDependencies": {
    "@tinypixelco/laravel-mix-wp-blocks": "^1.0.0",
    "@wordpress/babel-preset-default": "^4.12.1",
    "@wordpress/browserslist-config": "^2.6.0",
    "@wordpress/dependency-extraction-webpack-plugin": "^2.5.0",
    "babel-eslint": "^10.1.0",
    "browser-sync": "^2.26.7",
    "browser-sync-webpack-plugin": "^2.0.1",
    "cross-env": "^7.0.2",
    "eslint": "^6.8.0",
    "eslint-plugin-import": "^2.20.2",
    "laravel-mix": "^5.0.4",
    "laravel-mix-copy-watched": "^2.2.4",
    "laravel-mix-purgecss": "^5.0.0-rc.1",
    "npm-run-all": "^4.1",
    "purgecss-with-wordpress": "^2.1.0",
    "rimraf": "^3.0.2",
    "sass": "^1.26.3",
    "sass-loader": "^8.0.2",
    "stylelint": "^13.3.3",
    "stylelint-config-standard": "^20.0.0",
    "vue-template-compiler": "^2.6.11"
  }
  "dependencies": {
    "@popperjs/core": "^2.10.2",
    "bootstrap": "^5.1.2",
    "import-glob-loader": "^1.1.0",
    "jquery": "^3.6.0"
  }




```

webpack

```js
mix.setPublicPath("./dist").browserSync({
  proxy: "wordpress",
  tunnel: true,
  open: false,
});

mix
  .webpackConfig({
    module: {
      rules: [
        {
          test: /.scss/,
          enforce: "pre",
          loader: "import-glob-loader",
        },
      ],
    },
  })
  .sass("resources/assets/styles/main.scss", "styles")
  .options({
    processCssUrls: false,
    postCss: [],
  })
  .purgeCss({
    whitelist: require("purgecss-with-wordpress").whitelist,
    whitelistPatterns: require("purgecss-with-wordpress").whitelistPatterns,
  });

mix
  .js("resources/assets/scripts/main.js", "scripts")
  .js("resources/assets/scripts/customizer.js", "scripts");

mix
  .copyWatched("resources/assets/images/**", "dist/images")
  .copyWatched("resources/assets/fonts/**", "dist/fonts");

mix.autoload({
  jquery: ["$", "window.jQuery"],
});

mix.sourceMaps(false, "source-map").version();
```

phpcs.xml

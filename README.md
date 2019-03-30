[![](https://data.jsdelivr.com/v1/package/npm/@zooplus/zoo-web-components/badge)](https://www.jsdelivr.com/package/npm/@zooplus/zoo-web-components)
![npm](https://img.shields.io/npm/dw/@zooplus/zoo-web-components.svg)
![NPM](https://img.shields.io/npm/l/@zooplus/zoo-web-components.svg)     
![npm bundle size (scoped)](https://img.shields.io/bundlephobia/min/@zooplus/zoo-web-components.svg)
![npm bundle size (scoped)](https://img.shields.io/bundlephobia/minzip/@zooplus/zoo-web-components.svg)      
![David](https://img.shields.io/david/dev/zooplus/zoo-web-components.svg)
![David](https://img.shields.io/david/zooplus/zoo-web-components.svg)

# Intro
 - Set of web-components which can be used in any modern UI framework (or without any).
 - The web-component set implements Z+ shop style guide.
 - Future releases will include theming, more components, ESM support.
 - Built with [SvelteJS](https://github.com/sveltejs)

## Installation
To use exported modules install this library as a dependency in your application by running       
`npm i @zooplus/zoo-web-components --save`;      
Or add the following line to your `index.html`:      
`<script src="https://cdn.jsdelivr.net/npm/@zooplus/zoo-web-components@4.0.1/dist/zoo-components-iife.min.js"></script>`

## Examples integrating with various frameworks
+ [VueJS](https://github.com/GeorgeTailor/vue-wc-integration)
+ [Angular](https://github.com/GeorgeTailor/angular-wc-integration)
+ [React](https://github.com/GeorgeTailor/react-wc-integration)

## Size of the library
Uncompressed size of the library is around 62 Kbytes;
Gzipped version is 15 Kbytes;

## Documentation
Head over to [online documentation](https://zooplus.github.io/zoo-web-components/) for more info regarding this library.


# Dev area
## Run
Run `npm start`. That command will build all available modules, write them as `bundle.js` file and throw it into `/docs` folder.

## Test
This project uses `Mocha` and `Chai` for writing tests. The tests are run using `Puppeteer`.
Run `npm test` to run the tests. Tests are automatically run before triying to publish new version to npm.

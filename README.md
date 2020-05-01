# cra-template-complex-browserext-typescript

A TypeScript template for bootstrapping complex Chrome/Firefox/(any Chromium-based browser) extensions, to be used with [Create React App](https://github.com/facebook/create-react-app) v3.3.0 and higher.

[Article](https://medium.com/swlh/bootstrapping-complex-chrome-firefox-edge-extensions-with-create-react-app-667be8df35d7)

## Usage

```sh
npx create-react-app my-app --template complex-browserext-typescript
```

## Includes

* [react-app-rewired](https://github.com/timarney/react-app-rewired) - to customize the default CRA configuration.

## Features

This template replaces the default single entry point with the following multiple ones:

* popup (`src/index.tsx`) - extension's popup page, replaces the default index entry point.
* options (`src/options.tsx`) - extension's options page.
* background (`src/background.ts`) - background script.
* content (`src/content.ts`) - content script.

### Notes

Index/popup entry point still refers to `src/index` (which can't be changed) and the respective HTML template still refers to `public/index.html`, whereas the respective output (both JS and HTML) uses `'popup'` in its filename template.

Any listed entry point except index/popup may be excluded from compilation. See `config-overrides.js` file for details on config customization.

The default CRA's development mode is incompatible with this template cause, unlike regular web pages, browser extensions can't be hosted on server. So running `npm start` script doesn't make sense (though it's still available).

This template uses the same simple React component test from older CRA versions (prior to v3.3.0) for popup and options' React components. If you want to use more advanced tests like in CRA v3.3.0 and higher, look at the official base template [sources](https://github.com/facebook/create-react-app/blob/master/packages/cra-template) for example.

CRA and Jest aren't aware of Chrome API or WebExtensions API. So if you want to use these APIs in your tests, you have to mock all used API methods (manually or with help of 3rd-party libraries).

## License

Licensed under the MIT license.

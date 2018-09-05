# userscript-webpack-skeleton

A basic skeleton for developing userscripts in node / webpack.

## Setup
1. Pull down, run `yarn install` or `npm install`.
2. Open a terminal and do `yarn run build` or `npm run build`. This should build the application.
3. Go to the `dist/` folder - there should be 2 files there. A `main.js` and a `local.user.js`.
4. Go to your userscript manager, create a new script, copy the contents of `local.user.js` and save.
5. Nagivate to www.google.com and open the console. You should be greeted by a "Hello World!" message.

## Usage
The `local.user.js` file is generated by the build script from your `package.json` file. If you open that you will see it contains some standard properties for that file, plus one non-standard property: `userscript`.
The userscript metadata is generated from existing `package.json` properties, when possible (with **name** and **version** being the only mandatory ones). Properties that do not exist in `package.json` natively (e.g. `match`, `grant` must be provided in the `userscript` property:
```javascript
"userscript": {
  "grant": [
    "GM_xmlhttpRequest",
    "GM_openInTab"
  ],
  "match": "https://*.deviantart.com/*",
}
```
There are 2 ways to do so - as a string or as an array. When arrays, they are transformed into multiple lines, e.g.
```
// @grant       GM_xmlhttpRequest
// @grant       GM_openInTab
```
Additionally, the `userscript` property can be used to override any native properties of `package.json`.

Further config, with the full capabilities of webpack is available in `webpack.config.js`.

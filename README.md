Babel issue [T2484], marked `WONTFIX`:

[T2484]: https://phabricator.babeljs.io/T2484

Babel ignores the `sourceMaps` option in `.babelrc` or `package.json`.

Reproduction steps:

* `npm install`
* `npm run clean`
* `npm run build`
* check last line of `lib/index.js`
* observe no source map

Maybe I'm specifying the option incorrectly?

* change `sourceMaps` to `sourceMapsX` in `package.json`
* `npm run build`
* observe `babel` fails because `sourceMapsX` is not a valid option

Maybe it's specific to `package.json`?

* remove `babel` from `package.json`
* `echo '{"sourceMaps": true,"presets": ["es2015"]}'>.babelrc`
* `npm run build`
* check last line of `lib/index.js`
* observe no source map

My conclusion:

* I'm specifying `sourceMaps` correctly in `package.json`
* Babel is ignoring it

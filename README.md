# api documentation for  [rollup (v0.41.6)](https://github.com/rollup/rollup)  [![npm package](https://img.shields.io/npm/v/npmdoc-rollup.svg?style=flat-square)](https://www.npmjs.org/package/npmdoc-rollup) [![travis-ci.org build-status](https://api.travis-ci.org/npmdoc/node-npmdoc-rollup.svg)](https://travis-ci.org/npmdoc/node-npmdoc-rollup)
#### Next-generation ES6 module bundler

[![NPM](https://nodei.co/npm/rollup.png?downloads=true&downloadRank=true&stars=true)](https://www.npmjs.com/package/rollup)

[![apidoc](https://npmdoc.github.io/node-npmdoc-rollup/build/screenCapture.buildCi.browser.%252Ftmp%252Fbuild%252Fapidoc.html.png)](https://npmdoc.github.io/node-npmdoc-rollup/build/apidoc.html)

![npmPackageListing](https://npmdoc.github.io/node-npmdoc-rollup/build/screenCapture.npmPackageListing.svg)

![npmPackageDependencyTree](https://npmdoc.github.io/node-npmdoc-rollup/build/screenCapture.npmPackageDependencyTree.svg)



# package.json

```json

{
    "author": {
        "name": "Rich Harris"
    },
    "bin": {
        "rollup": "./bin/rollup"
    },
    "bugs": {
        "url": "https://github.com/rollup/rollup/issues"
    },
    "contributors": [
        {
            "name": "Oskar Segersvärd"
        },
        {
            "name": "Bogdan Chadkin"
        }
    ],
    "dependencies": {
        "source-map-support": "^0.4.0"
    },
    "description": "Next-generation ES6 module bundler",
    "devDependencies": {
        "acorn": "4.0.4",
        "buble": "^0.15.1",
        "chalk": "^1.1.3",
        "codecov.io": "^0.1.6",
        "console-group": "^0.3.1",
        "eslint": "^3.12.2",
        "eslint-plugin-import": "^2.2.0",
        "is-reference": "^1.0.0",
        "istanbul": "^0.4.3",
        "locate-character": "^2.0.0",
        "magic-string": "^0.15.2",
        "minimist": "^1.2.0",
        "mocha": "^3.0.0",
        "remap-istanbul": "^0.6.4",
        "require-relative": "^0.8.7",
        "rollup": "^0.39.0",
        "rollup-plugin-buble": "^0.13.0",
        "rollup-plugin-commonjs": "^7.0.0",
        "rollup-plugin-json": "^2.0.0",
        "rollup-plugin-node-resolve": "^2.0.0",
        "rollup-plugin-replace": "^1.1.0",
        "rollup-plugin-string": "^2.0.0",
        "sander": "^0.6.0",
        "source-map": "^0.5.6",
        "sourcemap-codec": "^1.3.0",
        "uglify-js": "^2.6.2"
    },
    "directories": {},
    "dist": {
        "shasum": "e0d05497877a398c104d816d2733a718a7a94e2a",
        "tarball": "https://registry.npmjs.org/rollup/-/rollup-0.41.6.tgz"
    },
    "files": [
        "dist",
        "bin/rollup",
        "README.md"
    ],
    "gitHead": "a96a923d631b9d2c471137542b9c4f578b8faa53",
    "homepage": "https://github.com/rollup/rollup",
    "jsnext:main": "dist/rollup.es.js",
    "keywords": [
        "modules",
        "bundler",
        "bundling",
        "es6",
        "optimizer"
    ],
    "license": "MIT",
    "main": "dist/rollup.js",
    "maintainers": [
        {
            "name": "eventualbuddha"
        },
        {
            "name": "rich_harris"
        },
        {
            "name": "trysound"
        },
        {
            "name": "victorystick"
        }
    ],
    "module": "dist/rollup.es.js",
    "name": "rollup",
    "optionalDependencies": {},
    "repository": {
        "type": "git",
        "url": "git+https://github.com/rollup/rollup.git"
    },
    "scripts": {
        "build": "git rev-parse HEAD > .commithash && rollup -c",
        "build:browser": "git rev-parse HEAD > .commithash && rollup -c rollup.config.browser.js",
        "build:cli": "rollup -c rollup.config.cli.js && chmod a+x bin/rollup",
        "ci": "npm run test-coverage && codecov < coverage/coverage-remapped.lcov",
        "lint": "eslint src browser test/test.js test/utils test/**/_config.js",
        "posttest-coverage": "remap-istanbul -i coverage/coverage-final.json -o coverage/coverage-remapped.json -b dist && remap-istanbul -i coverage/coverage-final.json -o coverage/coverage-remapped.lcov -t lcovonly -b dist && remap-istanbul -i coverage/coverage-final.json -o coverage/coverage-remapped -t html -b dist",
        "prepublish": "npm run lint && npm test && npm run build:browser",
        "pretest": "npm run build && npm run build:cli",
        "pretest-coverage": "npm run build",
        "test": "mocha",
        "test-coverage": "rm -rf coverage/* && istanbul cover --report json node_modules/.bin/_mocha -- -u exports -R spec test/test.js",
        "test:quick": "rollup -c && mocha",
        "watch": "rollup -c -w",
        "watch:browser": "rollup -c rollup.config.browser.js -w",
        "watch:cli": "rollup -c rollup.config.cli.js -w"
    },
    "version": "0.41.6"
}
```



# <a name="apidoc.tableOfContents"></a>[table of contents](#apidoc.tableOfContents)

#### [module rollup](#apidoc.module.rollup)
1.  [function <span class="apidocSignatureSpan"></span>rollup ( options )](#apidoc.element.rollup.rollup)
1.  string <span class="apidocSignatureSpan">rollup.</span>VERSION



# <a name="apidoc.module.rollup"></a>[module rollup](#apidoc.module.rollup)

#### <a name="apidoc.element.rollup.rollup"></a>[function <span class="apidocSignatureSpan"></span>rollup ( options )](#apidoc.element.rollup.rollup)
- description and source-code
```javascript
function rollup( options ) {
	var err = checkOptions ( options );
	if ( err ) return Promise.reject( err );

	var bundle = new Bundle$$1( options );

	timeStart( '--BUILD--' );

	return bundle.build().then( function () {
		timeEnd( '--BUILD--' );

		function generate ( options ) {
			if ( options === void 0 ) options = {};

			if ( !options.format ) {
				bundle.warn({
					code: 'MISSING_FORMAT',
					message: "No format option was supplied – defaulting to 'es'",
					url: "https://github.com/rollup/rollup/wiki/JavaScript-API#format"
				});

				options.format = 'es';
			}

			timeStart( '--GENERATE--' );

			var rendered = bundle.render( options );

			timeEnd( '--GENERATE--' );

			bundle.plugins.forEach( function (plugin) {
				if ( plugin.ongenerate ) {
					plugin.ongenerate( assign({
						bundle: result
					}, options ), rendered);
				}
			});

			flushTime();

			return rendered;
		}

		var result = {
			imports: bundle.externalModules.map( function (module) { return module.id; } ),
			exports: keys( bundle.entryModule.exports ),
			modules: bundle.orderedModules.map( function (module) { return module.toJSON(); } ),

			generate: generate,
			write: function (options) {
				if ( !options || !options.dest ) {
					error({
						code: 'MISSING_OPTION',
						message: 'You must supply options.dest to bundle.write'
					});
				}

				var dest = options.dest;
				var output = generate( options );
				var code = output.code;
				var map = output.map;

				var promises = [];

				if ( options.sourceMap ) {
					var url;

					if ( options.sourceMap === 'inline' ) {
						url = map.toUrl();
					} else {
						url = (path.basename( dest )) + ".map";
						promises.push( writeFile$1( dest + '.map', map.toString() ) );
					}

					code += "//# " + SOURCEMAPPING_URL + "=" + url + "\n";
				}

				promises.push( writeFile$1( dest, code ) );
				return Promise.all( promises ).then( function () {
					return mapSequence( bundle.plugins.filter( function (plugin) { return plugin.onwrite; } ), function (plugin) {
						return Promise.resolve( plugin.onwrite( assign({
							bundle: result
						}, options ), output));
					});
				});
			}
		};

		return result;
	});
}
```
- example usage
```shell
n/a
```



# misc
- this document was created with [utility2](https://github.com/kaizhu256/node-utility2)

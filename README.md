# Creating and Publishing Meteor Packages

### Package folder structure
```sh
tapfuse:package-name/
 docs/                   --| Generated docs meteor app
 docs-static/            --| Output folder for static docs website
 lib/                    --| All package code should go here
  tp-package-name.js     --| JavaScript goes here
  tp-package-name.jade   --| JADE autocompiles to HTML (Packages with UI only)
  tp-package-name.less   --| LESS autocompiles to CSS (Packages with UI only)
 tests/                  --| All testing related files should go here
 .eslintignore           --| ESLint ignore rules
 .eslintrc               --| ESLint overrides
 .eslintrc-meteor        --| ESLint meteor defaults
 CHANGELOG.md            --| Version history log file
 jsdoc-conf.json         --| Config for jsdoc
 jsdoc.json              --| Config for meteor-jsdoc generator
 LICENSE                 --| MIT license
 package.js              --| Meteor package info
 publish.json            --| Config for docs publishing
 README.md               --| Readme
```

### 1. Generate package structure with `oo-cli`
```sh
# Package with UI
  oo g:package some:package
# For JS only pakage use --lib flag
  oo g:package tapfuse:package-name --lib
  # XXX For now manually change where your export goes 'server' or `client`
```

### 2. Publish to GitHub

* Do not for get to move to `_packages` directory
* GitHub **repository names** must be prefixed with `meteor-` e.g. `meteor-package-name`

### 3. Comment your package functions using [JSDOC](http://usejsdoc.org)
Automatic build tool uses `meteor-jsdoc` to generate documentation, more info on [metero-jsdoc repo](https://www.npmjs.com/package/meteor-jsdoc) and [meteor hackpad](https://meteor.hackpad.com/Automatically-Generating-API-Docs-using-JSDoc-EpPmd2iuFEH).

Some Meteor specific `jsdoc` examples:
```
# Meteor methods

/**
 * @memberOf Methods
 * @isMethod true
 * @summary Method description.
 * @param   {string} id Document id
 * @param   {string} query Query params
 * @return  {String} Result
 */
   
```
```
# Meteor templates/components

/**
 * @memberOf Components
 * @isTemplate true
 * @name  myComponent
 * @summary Component description.
 * @param {String} id Document _id
 * @param {Number} limit Limit number of records
 */
   
```

### 4. Generate and publish documentation with `oo-cli`
```sh
# Build a meteor app for docs, output goes to /docs
oo docs build
# Build a static html site from meteor app
oo docs static
# Commit changes
# Publish your docs to guthub pages
oo docs publish

# Commands aliases
docs    -> d

build   -> b
static  -> s
publish -> p
```
  * If you are having issues with publishing try removing the remote branch `git push origin --delete gh-pages`

#### You can also run meteor docs app locally at [localhost:3333](http://localhost:3333) by running:
```sh
oo docs start
oo docs stop
```

### 5. Publish package
Resources:
  * https://atmospherejs.com/i/publishing
  * https://meteorhacks.com/meteor-packaging-system-understanding-versioning
```sh
# In package folder run:
  # For first time publish use --create flag
  meteor publish --create
  # Publish new versions
  meteor publish
```
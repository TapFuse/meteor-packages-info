# Creating and Publishing Meteor Packages

### Package structure
```sh
tapfuse:package-name/
 docs/                   --> Generated docs meteor app
 docs-static/            --> Output folder for static docs website
 lib/                    --> All package code should go here
  tp-package-name.js     --> JavaScript goes here
  tp-package-name.jade   --> JADE autocompiles to HTML (UI packages only)
  tp-package-name.less   --> LESS autocompiles to CSS (UI packages only)
 tests/                  --> All testing related files should go here
 .eslintignore           --> ESLint ignore rules
 .eslintrc               --> ESLint overrides
 .eslintrc-meteor        --> ESLint meteor defaults
 CHANGELOG.md            --> Version history log file
 jsdoc-conf.json         --> Config for jsdoc
 jsdoc.json              --> Config for meteor-jsdoc generator
 LICENSE                 --> MIT license
 package.js              --> Meteor package info
 README.md               --> Readme
```

### Generate package structure with `oo-cli`
```
# Package with UI
  oo g:package some:package
# For JS only pakage use --lib flag
  oo g:package tapfuse:package-name --lib
  # XXX For now manually change where your export goes 'server' or `client`
```
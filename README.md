## Introduction

This repository aims to reproduce the incompatibility between the `--bundle` and
`--css-modules` options of parcel-css as described [here](https://github.com/parcel-bundler/parcel-css/issues/102).

In the repo you will find two CSS files: `app.css` and `index.css`. Both of them
contain a class selector called `.test` and `app.css` is imported by `index.css`.

After installing the node-modules and running the `parcel-css` script defined in
`package.json`, you will see that the generated `bundle.css` contains both
classes with different names, as expected, but `bundle.json` only contains a
mapping for one of these generated classes (the one from `index.css`). This
effectively makes the `.test` class unreachable by whatever tooling is used to
extract generated class names from the JSON file.

## Reproduction steps

```
git clone git@github.com:Blond11516/parcel-css-bundle-modules-repro.git
cd parcel-css-bundle-modules-repro
npm i
npm run parcel-css
```

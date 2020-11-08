# Antiboredom

## Overview

![Antiboredom logo](./src/assets/logo.svg)

This is a simple web app that shows how to use VueJS to display data from a public REST API.
The displayed data can be sorted and filtered by the user.

This app uses VueJS and Bootstrap-vue, and the following APIs,
[The Bored API](https://www.boredapi.com/)
[Placedog.net](https://placedog.net)

## Live demo

A live demo hosted on Github Pages can be found [here](https://amyxs.github.io/antiboredom/)
 
## Development notes

### Project requirments

This project uses Vue2

VueJS 2.6.12, Node.js v12.16.2

### Project setup

```
yarn install
```

### Compiles and hot-reloads for development

```
yarn serve
```

### Compiles and minifies for production

```
yarn build
```

### Lints and fixes files

```
yarn lint
```

### Customize configuration

See [Configuration Reference](https://cli.vuejs.org/config/).

### Deployment

When ready for deployment, run the deploy.sh script.
Running the deploy.sh will create a commit on a branch called gh-pages, which is a subtree of the main branch. It's used as the build output folder.
Github Pages needs to be setup to show the gh-pages branch.

```
./deploy.sh
```
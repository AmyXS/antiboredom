# Antiboredom

## Overview

This is a simple web app that showcases the [Bored API](https://www.boredapi.com/)

## Live demo

A live demo hosted on Github Pages can be found [here](https://amyxs.github.io/antiboredom/)
 
## Development notes

### Project requirments

Vue CLI v2, with its required version of Node.js

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
Running the deploy.sh will create a branch called gh-pages, which is a subtree of the main branch. It's used as the build output folder. 
Github Pages is setup to show the gh-pages branch.

```
./deploy.sh
```
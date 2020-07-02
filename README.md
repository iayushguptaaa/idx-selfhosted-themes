# idx-selfhosted-themes

# Introduction 

This folder contains everything needed to build the LoginRadius Self-Hosted IDX.


# Getting Started

## Installation

1. Clone the repo to your desired where it should be hosted on your localhost.

2. Add your LoginRadiusV2.js and IDX options e.g. API Key and Secret in `static/idx-options.js`. 

3. In the repo's parent folder run `npm install` this will install any packages necessary for the project.

4. Once everything is installed type `npm run start` to get webpack to start serving the JavaScript.

5. Visit `http://localhost:8080/`

## Development

All of the code is in the `src` folder, the main code logic is in `main.js` and the styling that depends on JavaScript is located in `styles.js`.

## Build and Test

Once you're ready to do a release of the identity experience framework, follow the steps below:

`npm run build`

This will build a javascript file in the `build` folder that you can grab and use for the release.


## Build Process

The build process is as follows; There are 3 webpack configuration files each one of them has a different build process based on your requirements, in package.json if you look at the `"scripts"` field you will see what they represent.

1. webpack.dev.config.js: `npm run start` deploys all of the assets in a convenient way that the IDX Framework can be tested and developed using hot reload.

2. webpack.prod.config.js: `npm run build` creates a "build" folder with only the necessary assets to deploy to production, the main file `idx-selfhosted.x.x.x.js` file is not minifed as this is a requirement for the implementation team. the second config object for webpack.prod.config.js will cause to output only a single minfied version of the framework's JavaScript named `idx-selfhosted.1.3.0.min.js`. This is useful for the product team's inclusion in the Admin Console. 

*Note:* Webpack requires an entry point into your code in order to bunde the code, in the `src` folder where most of the code is located, the `index.js` is the entry point for the production configs, `webpack.prod.config.js` while for development we need to load different JavaScript code and as such the entry point for `webpack.dev.config.js` is the `index-dev.js` file.

**Versioning** To release a new version we use the semver.org convention, to set the version number you will need to edit `webpack.prod.config.js` in the "Entry" field to make sure they show the correct version. 

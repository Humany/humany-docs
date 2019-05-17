---
path: '/widgets/webprovisions/standalone/standalone-setup'
date: '2017-11-07'
title: 'Standalone setup'
---

# Standalone setup
This tutorial will you guide you on how to setup a standalone widget installation using the [`@humany/cli`](https://www.npmjs.com/package/@humany/cli) utility. 

## Prerequisities
This tutorial will assume you have a valid enterprise account of Humany with at least one public widget based on a V4 implementation. Also make sure you have [NodeJS](https://nodejs.org) and [NPM](https://www.npmjs.com/get-npm) installed on your computer.

## Installing the CLI
Open a command prompt and run the following command to install the Humany CLI globally:
```
> npm install @humany/cli -g
```
Ensure the CLI has been successfully installed by running the following command:
```
> humany -V
```
It should print the currently installed version.

## Setting up an implementation
The CLI will create a default widget installation on your computer and install all required dependencies.

### Create an empty target directory
Start by creating an empty target directory.
```
> mkdir humany
> cd humany
```

### Locate the implementation URL
* Go to the Humany portal and edit the V4 implementation of your choice (right-click and select 'Edit')
* Ensure the implementation is using the V4 runtime
* Expand the "Installation" section and locate the embed URL, e.g.: `https://demo.humany.net/my-implementation/embed.js`
* Remove the trailing `/embed.js` part to get the implementation URL, e.g.: `https://demo.humany.net/my-implementation`

### Execute the `setup` command
Execute the following command:
```
> humany setup [implementation-url]
```
It will prompt you to select one widget from the specified implementation. The CLI will create a template project and bootstrap the selected widget. When the setup is completed a local web server will start displaying the widget.

### Creating a distribution bundle
The setup uses Webpack to generate the distribution bundles. Use one of the following commands to generate the bundle. The generated files are located in the `/dist` folder.

**Production bundle**
```
> npm run build
```
**Development bundle**
```
> npm run build-dev
```
---
title: "Useful npm commands"
categories: npm
author: "Andy Knight"
---
NPM (Node Package Manager) is a great command line tool used to managed packages in your project. You can download and install it [here][npm-url]. NPM has become an ever increasingly important tool. Here is just a couple of notes on useful commands.

### npm install
The `install` parameter is probably the most used and very important when starting a project. Used on its own and in a project folder, npm will install all dependency packages listed in the package.json file. Any dependencies installed will be placed in the `node_modules` folder.

### npm install -g
Including the `-g` parameter allows packages to be installed as a global dependency and available to all projects. These are really handy for things like CLI tools, such as the angular cli tool.

### npm update
The `update` parameter works slightly differently. Using `npm update` will cause dependencies in the `node_modules` folder to be updated. 

### npm outdated
The `outdated` parameter allows you to see which packages are updateable.

### npm outdated -g --depth=0
Use this command to find outdated packages in the global section. Using this will a nice table of outdated packages.

![npm outdated -g --depth=0](/assets/img/2018-12-20/outdated.png) 

You can then use the update parameter to individually update each package, or everything.

### Finally

Just a few helpful notes for npm if you're starting out. I hope this helps!

[npm-url]: https://www.npmjs.com/
# monterey

[![Join the chat at https://gitter.im/aurelia-tools/monterey](https://badges.gitter.im/aurelia-tools/monterey.svg)](https://gitter.im/aurelia-tools/monterey?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)

This application structure is modeled after the [electron-boilerplate](https://github.com/szwacz/electron-boilerplate) by Jakub Szwacz.

***

### Quick start
The only development dependency of this project is [Node.js](https://nodejs.org). So just make sure you have it installed.
Then type few commands known to every Node developer...
```
git clone https://github.com/aurelia-tools/monterey.git
cd monterey
npm install
npm start
```

### Structure of the project

There are **two** `package.json` files:

#### 1. For development
Sits on path: `monterey/package.json`. Here you declare dependencies for your development environment and build scripts. **This file is not distributed with real application!**

Also here you declare the version of Electron runtime you want to use:
```json
"devDependencies": {
  "electron-prebuilt": "^0.34.0"
}
```

#### 2. For monterey
Sits on path: `monterey/app/package.json`. This is **real** manifest of monterey. Declare your app dependencies here.

#### Why two `package.json`?
1. Native npm modules (those written in C, not JavaScript) need to be compiled, and here we have two different compilation targets for them. Those used in application need to be compiled against electron runtime, and all `devDependencies` need to be compiled against your locally installed node.js. Thanks to having two files this is trivial.
2. When you package the app for distribution there is no need to add up to size of the app with your `devDependencies`. Here those are always not included (because reside outside the `app` directory).

***

### Project's folders

- `app` - code of your application goes here.
- `config` - place where you can declare environment specific stuff for your app.
- `build` - in this folder lands built, runnable application.
- `releases` - ready for distribution installers will land here.
- `resources` - resources needed for particular operating system.
- `tasks` - build and development environment scripts.

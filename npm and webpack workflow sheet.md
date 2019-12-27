# npm and webpack Workflow cheatsheet

## Versions

os: Ubuntu LTS

npm : 6.13.4

webpack :

git:

## Workflow

### Initialize npm

In a terminal,

```
npm init
```

This will create a files; package.json and package-lock.json. package.json will have all of your projects dependencies. So you can just `npm install` to re-install all of the modules.

### Install webpack and webpack cli via npm. webpack-cli so we can use webpack via scripts

```
npm install --save-dev webpack webpack-cli
```

the --save saves this as a dependency for our project, while -dev flags that this is a developer dependency and will not be added to production.

### Make github ignore node_modules folder.

node_modules folder is where all your modules will reside. Meaning this folder will be huge. Which is a problem when you wanted to upload your repo to github. You can set git to ignore this folder so it will not be uploaded. Anyhow, you can re-install modules easily via `npm install`.

In the root of the repo,

```
touch .gitignore
```

open the file and then add,

```
node_modules/
```

## Create a dist and src folder

This the default folders used by webpack. We can name them anything but will need to use a configuration to align them. So why not use the default :). Anyway, with all that said we will still create a configuration for webpack so that this becomes a natural for us.

We will create the folder structure,

```
mkdir src dist
touch src/index.js
touch dist/index.html
```

Now open index.html and link main.js. main.js file is to created by webpack after we run it later.

Now, we will create the webpack config.

```
touch webpack.config.js
```

inside this file, follow this basic configuration setup. https://webpack.js.org/guides/getting-started/#using-a-configuration.

## Run webpack

You can run webpack by typing `webpack` in the terminal.

```
npx webpack
```

A better way would be to add this to our build script in npm. This way, we can use `npm run build` to run all of our build scripts.

To do so, add this script in your package.json file under scripts

```
"build": "webpack"
```

now you can use `npm run build` to run webpack for your project.

```
npm run build
```

### Test if it worked.

Inside index.js file. Add an alert(). Save the file and then in the terminal, run webpack `npm run build`. Load index.html and check if the alert will show up.

To automate this you can activate, `webpack --watch` so webpack auto repack everytime you make changes.

```
webpack --watch
```

That's all!

-- RyeCoder

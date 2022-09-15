## Create React App from Scratch like a Pro

Creating a **React App** is a very difficult feat, even when you are an _experienced developer_. That led to the development of `create-react-app`, a **Command Line Tool** to streamline the process of creating a **React app**.

Using `create-react-app` comes with _several added benefits_ such as **rapid prototyping** and making the development of React Apps **accessible to beginners**, but there are some _disadvantages_ as well.

Since `create-react-app` aims to generate more or less an **all-purpose app**, leading to a lot of additional **not-so-necessary dependencies** for any given **niche case**. Another _con_ for using `create-react-app` is **customizing** it might be a _pain_ at times.

So let's dive into how to create your **React Apps** from scratch that allow you to **customize the app** to your **heart's content**

# Preparations
## Installing Node

This goes without saying, you need **Node.js** and **npm** or **yarn** (in this article I would be using **npm**). To test if you have them installed, run the following commands:

```bash
node -v
```

```bash
npm -v
```

In case you don't have them installed, I trust you with being able to install them, so I am moving on to the next step.

## Initializing the project

Create a new folder and navigate into it. To initialize a node project use:

```bash
npm init
```

and modify the generated `package.json`.

## Installing dependencies

Now we would be adding the necessary **Dependencies** to our project.

### React

These are the only _dependencies_ that are **NOT** _dev dependencies_

```bash
npm install react react-dom
```

Let's take a look at the libraries:

`react`: **library** we'll be working with.
`react-dom`: package to _manage_ **DOM elements**.

### Webpack

**Webpack** is the _most popular bundler_ in the world of **Node.js**. It _bundles_ and even _minifies_ the JavaScript files in the project.

```bash
npm install -save-dev webpack webpack-cli
```

Taking a look at the libraries:

`webpack`: the **bundler**.
`webpack-cli`: **CLI** for **Webpack**.

### 3. **Webpack Loaders**

**Webpack** needs **loaders** to **preprocess** files. They allow the user customize **Webpack** to bundle **static resources** beyond **JavaScript**.

```bash
npm install --save-dev babel-loader
```

For now, let's start with the absolutely necessary `babel-loader` (**loader** for **Babel**) and later add additional functionality based on need.

### Babel

**Babel** is a JavaScript compiler that converts (or rather **transpiles**) **JavaScript ES6** to targeted version of **JavaScript** since _not all browsers_ support **ECMAScript 6** features. We would be using it to **transpile** the **JSX** code in our project to regular **JavaScript** that browsers can understand.

```bash
npm install --save-dev @babel/core @babel/preset-react
```

The dependencies:

`@babel/core`: Babel compiler core.
`@babel/preset-react`: package with a _set of plugins_ used to support **React features**.

## Configuring dependencies
### Babel

To configure **Babel**, we need to add `.babelrc` in the _root level_ of our project

```json
{
  "presets": [
    "@babel/preset-react"
  ]
}
```

### Webpack

Now its time to configure **Webpack**. Add the `webpack.config.js` at the _root level_ of the project and add the following code:

```js
const path = require("path");
const webpack = require("webpack");

module.exports = {
  entry: "./src/index.js",
  mode: "development",
  output: {
    filename: "bundle.js",
    path: path.resolve("dist"),
    publicPath: "/",
  },
  module: {
    rules:[
      {
        test: /\.(js|jsx)$/,
        exclude: /node_modules/,
        use: "babel-loader"
      },
    ], 
  },
}
```

And let’s see what all of this is doing:
- `entry`: The **entry point** for our application. In **React**, this is the file where we use our **renderer**.
- `mode`: The **mode** in which the application is being run (**development** or **production**).
- `output`: Informing **Webpack** where to put our **bundled code** and the name of the file.
- `module`: Informing **Webpack** how and when to use the **loaders** we installed. We’re using regex to tell each loader which file extensions to target.

## HTML Body

Add an `/public/index.html` and the basic body:

```html
<!DOCTYPE html>
<html lang="en">
	<head>
		<meta charset="UTF-8" />
		<meta http-equiv="X-UA-Compatible" content="IE=edge" />
		<meta name="viewport" content="width=device-width, initial-scale=1.0" />
		<title>React From Scratch</title>
	</head>
	<body>
		<div id="root"></div>
		
		<!-- The bundle-name should be same as you defined in webpack config file -->
		<script src="../dist/bundle.js"></script>
	</body>
</html>
```

# Creating the React App

Finally, we now start working on our app. Add `/src/index.js` (the entry point for the app mentioned in `webpack.config.js`)

```jsx
import React from "react";
import ReactDOM from "react-dom";

import App from "./App"

ReactDOM.render(
	<App />,
	document.querySelector("#root")
);
```

and the **App** file `/src/App.js`

```jsx
import React from "react";

export default function App() {
	return (
		<div>
			<h1>React from Scratch</h1>
		</div>
	);
}
```

## Adding Scripts

We are done making the app, but how do we run it? Glad you asked. we need to add 2 scripts for ease of use:

```json
"scripts": {
    "build": "webpack --mode production",
    "start": "webpack --mode development"
}
```

Now you can use `npm run build` or `npm run start` to bundle the **React App** and run the app from `/public/index.html`.

# Conclusion

You can extend the functionality with **additional plugins** and **loaders** such as installing `style-loader` & `css-loader` and adding:

```js
{
    test: /\.css$/,
    use: ['style-loader', 'css-loader']
}
```

in your `webpack.config.js`, you can implement **CSS** support in your **React App**

You can add `webpack-dev-server` to serve the website instead of opening the **HTML** file (and potentially more optimized `start` script), use `HotModuleReplacementPlugin` to enable **Hot Reload** and much more. The possibilities are endless. Now you can create **React Apps** that cater to your individual requirements.

All the best in your **React** Development journey! :)
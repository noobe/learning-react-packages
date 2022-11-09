# learning-react-packages
A project to test various packages used in React

## Setting up a minimal React project:
01. Setting up the project
Run `npm init -y` to create a new npm project. This results in creationg of a `package.json` file.

02. Installing Babel libs
Run `npm install --save-dev @babel/core babel-loader @babel/cli @babel/preset-env @babel/preset-react` to install all babel related dependencies.

`@babel/core`: the core/main package that is needed to use Babel in our project.
`babel-loader`: enables us to use Babel together linked with webpack.
`@babel/cli`: (optional) allow us to use Babel to compile files directly from the command line. You don't necessarily need this to use React but you may need to use Babel in command line.
`@babel/preset-env`: used to convert ES6 JavaScript syntax into backward versions of JavaScript supported by older browsers.
`@babel/preset-react`: used to convert React syntax (jsx) into backward versions of JavaScript supported by older browsers.

03. Installing Webpack libs
Run `npm install --save-dev webpack webpack-cli webpack-dev-server` to install all webpack and related dependencies.
`webpack`: the actual package that enables us to use webpack in our project
`webpack-cli`: allow us to run webpack commands in the command line
`webpack-dev-server`: the webpack server that will act as our server in development if you are familiar with development servers live-server or nodemon it works the same

04. Install HtmlWebpackPlugin
Run `npm install --save-dev html-webpack-plugin`. The HtmlWebpackPlugin simplifies creation of HTML files to serve your webpack bundles. as mentioned above when Webpack bundles all our files, it generate a single JavaScript (know as bundle) that will be served along our html file. HtmlWebpackPlugin handles creation these html files.

05. Install React dependencies
Run `npm install react react-dom` to install React and ReactDOM libs.

06. Create folder named `public` and create file  `index.html` in it, with the following content:
```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>React App</title>
</head>
<body>
  <div id="root"></div>
</body>
</html>
```

07. Create folder `src` to house all React components and create the 1st file `App.js` in it with the following content:
```js
import React from "react";

const App = () =><h1>Hello world! I am using React</h1>;

export default App
```

08. Create file `index.j` in the project root that will mount the react components into the page using the following code in it:
```js
import React from 'react'
import  { createRoot }  from 'react-dom/client';
import App from './src/App.js'

const container = document.getElementById('root');
const root = createRoot(container);
root.render(<App/>);
```

09. Create file `.babelrc` to provide the follwing babel specification:
```js
{
  "presets": ["@babel/preset-env","@babel/preset-react"]
}
```

10. Create file `webpack.config.js` to add the follwing webpack spec:
```js
const HtmlWebpackPlugin = require('html-webpack-plugin');
const path = require('path');

module.exports = {
  entry: './index.js',
  mode: 'development',
  output: {
    path: path.resolve(__dirname, './dist'),
    filename: 'index_bundle.js',
  },
  target: 'web',
  devServer: {
    port: '5000',
    static: {
      directory: path.join(__dirname, 'public')
    },
    open: true,
    hot: true,
    liveReload: true,
  },
  resolve: {
    extensions: ['.js', '.jsx', '.json'],
  },
  module: {
    rules: [
      {
        test: /\.(js|jsx)$/, 
        exclude: /node_modules/, 
        use: 'babel-loader', 
      },
    ],
  },
  plugins: [
    new HtmlWebpackPlugin({
      template: path.join(__dirname, 'public', 'index.html')
    })
  ]
};
```

11. Add the following in the `scripts` section of `package.json` file:
```json
"scripts": {
  "start": "webpack-dev-server .",
  "build": "webpack .",
},
```

12. Run the command `npm start` to test.

13. Run the command `npm run build` to build the production version of the HTML/CSS/JS files as per the webpack output spec.
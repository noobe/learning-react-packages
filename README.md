# learning-react-packages
A project to test various packages used in React

## Steps:
1. Setting up the project
Run `npm init -y` to create a new npm project. This results in creationg of a `package.json` file.

2. Installing Babel libs
Run `npm install --save-dev @babel/core babel-loader @babel/cli @babel/preset-env @babel/preset-react` to install all babel related dependencies.

`@babel/core`: the core/main package that is needed to use Babel in our project.
`babel-loader`: enables us to use Babel together linked with webpack.
`@babel/cli`: (optional) allow us to use Babel to compile files directly from the command line. You don't necessarily need this to use React but you may need to use Babel in command line.
`@babel/preset-env`: used to convert ES6 JavaScript syntax into backward versions of JavaScript supported by older browsers.
`@babel/preset-react`: used to convert React syntax (jsx) into backward versions of JavaScript supported by older browsers.

3. Installing Webpack libs
Run `npm install --save-dev webpack webpack-cli webpack-dev-server` to install all webpack and related dependencies.
`webpack`: the actual package that enables us to use webpack in our project
`webpack-cli`: allow us to run webpack commands in the command line
`webpack-dev-server`: the webpack server that will act as our server in development if you are familiar with development servers live-server or nodemon it works the same

4. Install HtmlWebpackPlugin
Run `npm install --save-dev html-webpack-plugin`. The HtmlWebpackPlugin simplifies creation of HTML files to serve your webpack bundles. as mentioned above when Webpack bundles all our files, it generate a single JavaScript (know as bundle) that will be served along our html file. HtmlWebpackPlugin handles creation these html files.

5. Install React dependencies
Run `npm install react react-dom` to install React and ReactDOM libs.

6. 

# Steps to create this template

git init
npm init

npm i vue vue-router core-js

npm install webpack webpack-cli webpack-dev-server babel-loader @babel/core @babel/preset-env vue-loader vue-template-compiler -D

create the folder 'dist' and 'src'

create the .gitignore and add the following folders

<pre>
node_modules/
dist/
</pre>

create the webpack.config.js file and add the following configs in webpack.config.js

<pre>
const { VueLoaderPlugin } = require("vue-loader");
const path = require("path");

module.exports = {
  entry: {
    main: "./src/main.js",
  },
  output: {
    path: path.resolve(__dirname, "dist"),
  },
  module: {
    rules: [
      {
        test: /\.js$/,
        exclude: /node_modules/,
        use: {
          loader: "babel-loader",
        },
      },
      {
        test: /\.vue$/,
        loader: "vue-loader",
      },
    ],
  },
  plugins: [
    new VueLoaderPlugin(),
  ],
  resolve: {
    extensions: [ '.tsx', '.ts', '.js', '.vue' ],
    alias: {
      'vue': '@vue/runtime-dom'
    }
  },
};
</pre>
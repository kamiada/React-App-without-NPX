So first of all: making react app without npx

1. Create folder for the project. 
2. Run `npm init -y `
3. Run `npm install react react-dom `
4. Run `npm install --save-dev @babel/core @babel/preset-env @babel/preset-react webpack webpack-cli webpack-dev-server babel-loader css-loader style-loader html-webpack-plugin `
5. Check what version of webpack you are using, if it is 4 or 5, then put below in the package.json 
``
"scripts": {
    "start": "webpack serve",
}
``
5. In project's folder run `touch webpack.config.js`
6. In this file paste this: 
``
var path = require('path');
var HtmlWebpackPlugin =  require('html-webpack-plugin');

module.exports = {
    entry : './app/index.js',
    output : {
        path : path.resolve(__dirname , 'dist'),
        filename: 'index_bundle.js'
    },
    module : {
        rules : [
            {test : /\.(js)$/, use:'babel-loader'},
            {test : /\.css$/, use:['style-loader', 'css-loader']}
        ]
    },
    mode:'development',
    plugins : [
        new HtmlWebpackPlugin ({
            template : 'app/index.html'
        })
    ]

};
``
7. Create .gitignore with this inside: 
``  node_modules
    .DS_Store
    dist ``
8. Create folder app inside your project folder and run `touch index.js index.css index.html`
9. Create .babelrc in the project's folder and add below inside
``
{
    "presets": ["@babel/preset-env", "@babel/preset-react"]
}
``
10. Add your code, run `npm start` in the console






Tutorial to follow in order to learn Redux: https://redux.js.org/tutorials/quick-start
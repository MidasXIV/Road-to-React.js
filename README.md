<p align="center">
  <h1 align="center">Learning React</h1>
</p>


<p align="center">
  <a href="#introduction">Introduction</a>
  <a href="#introduction">Boiler Plate</a>
  <a href="#introduction">Environment Setup</a>
</p>

***

# Introduction
* Faster than applications developed in vanilla javascript.
	* -> Because of virtualDom.
* Reusable Web Components.
	* -> Cleaner Code.
* Maintained by Facebook.
* Very in demand Framework for front end development.

1. `Components` : 
	* JSX : javascript wrapper.
	* Props : State.
	* Must Know HTML, CSS, JS, ES6 (2015).
	
```javascript
import React from "react"
import ReactDOM from "react-dom"

ReactDOM.render(What do i want to render, where do i want to render it)
//JSX : javascript rendering HTML
ReactDOM.render(<h1>React Introduction</h1>, document.getElementById("root"))

```
### React Environment from BoilerPlate
1. `npm install create-react-app`
2. `create-react-app 'project-name'`

### React Environment from Scratch
1. Create a Directory.
    `mkdir react-application && cd react-application`
2. Initialize Directory.
    `npm init`
3. Install webpack and webpack-dev-server.
    * Webpack: to bundle all of our javascript files into one file and host that file on the server.
    * Webpack Development Server: We need this server to recompile our main javascript file every time we make changes and provide us one server.
    `npm install webpack webpack-dev-server --save-dev`
4. Create index.html file.
    ```HTML
    <!-- index.html -->
    <!DOCTYPE html>
    <html lang="en">
        <head>
            <meta charset="UTF-8">
            <title>React Application</title>
        </head>
        <body>
            <script type="text/javascript"  data-src="bundle.js"></script>
        </body>
    </html>
    ```
    > Here we have included only one javascript file called bundle.js in our HTML page, which is bundled by Webpack.
5. Create a directory called app in the root folder.
    * In the app directory, create a new javascript file called main.js.
    ```javaScript
    console.log('Inside app folder');
    ```
6. Configure webpack.config.js file in a root directory
    * In the webpack.config.js file, we need to export all the webpack settings by exporting javascript object.
    ```javaScript
    module.exports = {
        entry: ['./app/main.js'],
        output: {
            filename: 'bundle.js'
        }
    };
    ```
    * The object contains two properties.
        * entry: – which represents our entry javascript file for the project. In our case It is  js6 > app > main.js
        * output: – the output bundled file, which we have to include in our main HTML file called bundle.js
7. Go to the package.json file and edit the following JSON property.
    * We add a new property  called “build” and value called “webpack-dev-server.”
    ```JSON
    {
      "name": "react-environment",
      "version": "1.0.0",
      "description": "",
      "main": "index.js",
      "scripts": {
        "build": "webpack-dev-server"
      },
      "author": "KRUNAL LATHIYA",
      "license": "ISC"
    }
    ```
8. Go to the terminal in your root project folder and type following command.
    `npm run build`
9.  Install and set Babel dependencies.
    `npm install --save-dev @babel/core @babel/preset-env`
    * babel-core and babel-loader is the dependency, which transpile the ES6 code to ES5
    * babel-preset-env let us use some advanced feature of ECMAScript in our web applications.
    * Update our webpack.config.js file.
    ```javascript
    module.exports = {
        entry: './app/main.js',
        output: {
            filename: 'bundle.js'
        },
        module: {
            rules: [{
                test: /\.js$/,
                exclude: /node_modules/,
                use: [{
                    loader: 'babel-loader'
                }]
            }]
        },
        devServer: {
            port: 3000
        }
    };
    ```
    * Here we have added module object, which has loaders property.
        * It will accept an array of loader configuration, like which loader we want to use and which file we have to test with the extension .js and which file we need to exclude from transpiling from es6 to es5 like “node_modules” folder.
    * I have added one optional attribute called devServer.
        * It includes the port number on which we need to host our app. by default webpack-dev-server provides port 8080.
        * But we can change it and put port 3000.
    
10. Check if everything is working so far
    * `npm i -D webpack-cli`
    * `npm run build`
    * open http://localhost:3000
    
11. Install React & React-dom
    * `npm install --save react react-dom`
    * We also need to use the package called “babel-preset-react” and “babel-preset-stage-3” to use latest ES6 features as well as we can write react code in ES6 syntax.
    * `npm install --save-dev babel-preset-react babel-preset-stage-3`

12. Create one file in root directory called .babelrc
    ```JSON
    {
        "presets": ["es2015", "react", "stage-3"]
    }
    ```
13. Create a component file App.js inside components folder.
    ```javascript
    import React, { Component } from 'react';
    export default class App extends Component {
        render(){
            return (
                <div>
                    Hello From React v15.4.2
                </div>
            );
        }
    }
    ```
14. Import App.js file into main.js file.
    ```javascript
    import React from 'react';
    import ReactDOM from 'react-dom';
    import App from './components/App';

    ReactDOM.render(<App />, document.getElementById('app'));
    ```
15. Run the program
    * `npm run build`
    * open  http://localhost:3000/
    
***
## Reference
* https://appdividend.com/2017/03/29/beginners-guide-to-setup-react-v15-4-2-environment/
* https://github.com/babel/gulp-babel/issues/124
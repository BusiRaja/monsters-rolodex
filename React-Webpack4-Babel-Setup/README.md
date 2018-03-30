# React-Webpack4-Babel-Setup

React project setup using babel and webpack

## Project setup step by step

The below command will initialize the project and create package json file

```
	npm init 

```

Install react and react-dom using following command

```
	npm install --save react react-dom

```

Next we need to install webpack 

```
	npm install --save webpack webpack-dev-server webpack-cli html-webpack-plugin

```

We need to install babel and babel-loader to transpile the Javascript files

```
	npm install --save babel-core babel-loader babel-preset-env babel-preset-react

```

Create webpack config file and setup as following

```
	    const path = require('path');
		const HtmlWebpackPlugin = require('html-webpack-plugin');

		module.exports = {
			entry: './src/index.js',
			output: {
				path: path.join(__dirname,'/dist'),
				filename: 'index_bundle.js'
			},
			module: {
			    rules: [
			      {
			        test: /\.js$/,
			        exclude: /node_modules/,
			        use: {
			          loader: 'babel-loader'
			        }
			      }
			    ]
			},
			plugins: [
			  new HtmlWebpackPlugin({
			    title: 'React Webpack Babel Setup', 
			    
			    template: './src/index.html'
			  })
			]
		}

```

Create babel presets file with .babelrc extension and add following code

```
	{
	 "presets": ["env","react"]
	}

```

Creat index.html file and following code

```
		<!DOCTYPE html>
		<html lang="en">
		<head>
			<meta charset="utf-8">
		    <meta name="viewport" content="width=device-width, initial-scale=1, shrink-to-fit=no">
		    
			<title>React Webpack Babel Setup</title>
		</head>
		<body>
			<div id="app"></div>
		</body>
		</html>	

```

Create index.js file and add the code as following

```
		import React from 'react'
		import ReactDOM from 'react-dom'
		import App from './components/App'

		ReactDOM.render(<App />, document.getElementById('app'));

```

We need to create App component to render the content 

```
	import React, {Component} from 'react' 

	class App extends Component {
		render() {
		    return(
		  		<div>
					<h1>React setup completed successfulling using Babel and Webpack</h1>
					<br />
					Happy Coding..!!!
					</h1>
			    </div> 
		  	) 
		}
	}

	export default App;
```

We need to add following scripts in package json file to start the webpack server

```
	"start": "webpack-dev-server --mode development --open --hot",
    "build": "webpack --mode production"

```

Once we add the above scripts run the following command

```
	npm start

```

The output will be displayed in browser

http://localhost:8080

Happy Coding...!!!
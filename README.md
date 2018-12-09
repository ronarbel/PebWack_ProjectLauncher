Goals: Create a new directory with webpack/node modules fully loaded, and render 'Hello World' in the browser.

Three steps: 
  1. Create directory structure.
  2. Add text to files.
  3. Launch app.

STEP 1:
  * From terminal, navigate into the PebWack_ProjectLauncher directory.
  * Run ' ./NewProject.txt ' (this will take a moment to download all modules).

STEP 2:
  * Four files will open in your text editor.
    - In package.json:
      * Add and save the following property to the scripts object: "build": "webpack --watch"
    - In index.jsx:
      * Copy and save the following:
        --------------------------------
        import React from 'react';
        import ReactDOM from 'react-dom';
        import App from './components/App.jsx';

        ReactDOM.render(
          <App />,
          document.getElementById('root')
        );
        --------------------------------
    - In App.jsx:
      * Copy and save the following:
        --------------------------------
        import React from 'react';

        class App extends React.Component {
          constructor(props) {
            super(props);
          }
          
          render() {
            return (
              <h1>Hello World</h1>
            );
          }	
        }

        export default App; 
        --------------------------------
    - In webpack.config.js:
      * Copy and save the following:
        --------------------------------
        const path = require('path');

        module.exports = {
          entry: path.resolve(__dirname, 'src/index.jsx'),
          output: {
            filename: 'bundle.js',
            path: path.resolve(__dirname, 'public/'),
          },
          mode: 'development',
          devtool: 'inline-source-map',
          module: {
            rules: [
              {
                test: /\.jsx?$/,
                exclude: /(node_modules|bower_components)/,
                use: {
                  loader: 'babel-loader',
                  options: {
                    presets: ['@babel/preset-env', '@babel/preset-react']
                  }
                },
              },
              {
                test: /\.css$/,
                use: ['css-loader'],
              },
            ],
          }
        };
        --------------------------------
    - A new folder 'YourNewWebpackReactProject will exist on your desktop. Manually open index.html in your text editor:
      * Copy and save the following:
        --------------------------------
        <!DOCTYPE html>
          <html lang="en">
          <head>
          </head>
        <body>
	        <div id="root"></div>
	        <script src="./public/bundle.js"></script>
        </body>
        </html>
        --------------------------------

STEP 3:
  * In terminal, navigate into 'YourNewWebpackReactProject'.
  * Run ' npm run build '.
  * Run ' live-server '.


Done! The folder 'YourNewWebpackReactProject' will have all modules/dependencies fully loaded.  Inside, src/components/app.jsx contains "Hello World". Change this folder to your app name, and repeat Step 3 when you want to run your app.

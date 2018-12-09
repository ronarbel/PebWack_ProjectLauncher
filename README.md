Goals: Create a new directory with webpack/node modules fully loaded, and render 'Hello World' in the browser.

Three steps: 
  1. Create directory structure.
  2. Add text to files.
  3. Launch app.

STEP 1:
  * From terminal, navigate into the PebWack_ProjectLauncher directory.
  * Run ' ./NewProject.txt ' (this will take a moment as it's literally doing all the things automatically).
  * New_Pebwack_Project will be created on your Desktop.

STEP 2:
  * Four files will open in your text editor. *YOU WILL EDIT 5 FILES TOTAL*
    1. In package.json:
    
        --------------------------------
      - Add and save the following property to the scripts object: "build": "webpack --watch"
        --------------------------------

    2. In index.jsx:
      - Copy and save the following:

        --------------------------------
        import React from 'react';
        import ReactDOM from 'react-dom';
        import App from './components/App.jsx';

        ReactDOM.render(
          <App />,
          document.getElementById('root')
        );
        --------------------------------

    3. In App.jsx:
      - Copy and save the following:

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

    4. In webpack.config.js:
      - Copy and save the following:

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

    5. A new folder 'New_PebWack_Project' will exist on your desktop. Manually open index.html in your text editor:
      - Copy and save the following:

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
  * In terminal, navigate into 'New_PebWack_Project'.
  * Run ' npm run build '.
  * In a new terminal tab, run ' live-server '.


Done! The folder 'New_Pebwack_Project' will have all modules/dependencies fully loaded.  Inside, src/components/app.jsx contains "Hello World". Change the root folder to your app name, and repeat Step 3 when you want to run your app.

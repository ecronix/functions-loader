# functions-loader

`functions-loader` is a utility package designed to automatically load Firebase Cloud Functions from files and folders within the `functions` directory. This simplifies the process of organizing and deploying your cloud functions by dynamically importing them based on the file structure. It specifically loads files with the `.f.js` extension.

## Installation

To install `functions-loader`, you can use npm or yarn:

## Usage

To use `functions-loader`, you need to require it in your `index.js` or `main.js` file where you initialize your Firebase functions. The package will automatically load all functions from the `functions` directory that have the `.f.js` extension.

### Example

1. **Create your functions directory structure:**

   ```
   functions/
   ├── index.js
   ├── helloWorld.f.js
   └── user/
       └── createUser.f.js
   ```

2. **Initialize `functions-loader` in your `index.js`:**

   ```javascript
   // functions/index.js
   const { loadFunctions } = require("firebase-function-tools-preview");

   // Load all functions from the 'functions' directory
   loadFunctions(__dirname, exports, true);
   ```

3. **Define your cloud functions in separate files with the `.f.js` extension:**

   ```javascript
   // functions/helloWorld.f.js
   const functions = require("firebase-functions");

   module.exports = {
     helloWorld: functions.https.onRequest((request, response) => {
       response.send("Hello, World!");
     }),
   };
   ```

   ```javascript
   // functions/user/createUser.f.js
   const functions = require("firebase-functions");

   module.exports = {
     createUser: functions.auth.user().onCreate((user) => {
       // Handle user creation
     }),
   };
   ```

### Demo

You can find a complete example of how to use `functions-loader` in the `demo` folder of this repository. The demo includes a sample project structure and demonstrates how to set up and use the package to load Firebase Cloud Functions.

With this setup, `functions-loader` will automatically import and register all the functions defined in the `functions` directory and its subdirectories that have the `.f.js` extension.

## License

This project is licensed under the MIT License.

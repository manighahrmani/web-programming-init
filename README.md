# Example of how to start Web Programming coursework

## Pre-requisites

- Install [Node.js](https://nodejs.org/en/)
- Install [Git](https://git-scm.com/)
- Install [Visual Studio Code](https://code.visualstudio.com/)

## (Optional) Clone the Staged Simple Message Board repository

1. Open Visual Studio Code.
2. Open Command Palette (Ctrl+Shift+P or Cmd+Shift+P).
3. Type `Git: Clone` and press Enter.
4. Enter `https://github.com/portsoc/staged-simple-message-board` and press Enter.
5. Select a location to save the repository and press Enter.
6. Open the repository in Visual Studio Code.
7. Open the Command Palette (Ctrl+Shift+P or Cmd+Shift+P).
8. Type `Terminal: New Terminal` and press Enter.
9. Type `npm install` and press Enter to install the dependencies.
10. Run stage 1 with `npm run stage1` and open the browser to `http://localhost:8080`.

## Starting your own project

1. Open Visual Studio Code.
2. Create a new folder for your project and open it in Visual Studio Code with `File > Open Folder`.
3. Recreate what you see in the Stage 1 folder of the Stage Simple Message Board repository. This means creating a server file (e.g., `server.js` or `svr.js` in the main folder) and a folder to serve your users (called `public` or `client`). Inside this folder, you need an `index.html` file and `index.js`. Here is what your folder should look like:
```
your-project-name/
├── public/ // or client/
│   ├── index.html
│   └── index.js
└── server.js // or svr.js
```
4. Copy the content of these files from stage 1 of the Simple Message Board repository (you may need to change some of the text e.g., the title of the HTML page). Note that `index.html` needs to link to `index.js` and your server file needs to serve the folder containing `index.html` and `index.js`. For instance, you need the following line in your `index.html`:
```html
<!doctype html>
<meta charset=utf-8>
<script defer src="index.js"></script> <!-- Matches the name of the .js file in the public/client folder -->
<title>Message Board</title> <!-- Change this to the title of your page -->

<h1>Message Board</h1> <!-- Change these too ... -->
<ul>
  <li>One day this will be a message board.</li>
  <li>Until then we can dream.</li>
</ul>
```
   The same goes for your server file. In the example below, our `server.js` file is serving the `public` folder over port 8080.
  ```javascript
  import express from "express";

  const app = express();
  app.use(express.static("public"));
  app.listen(8080);
  ```
5. Open the terminal in Visual Studio Code with `Terminal > New Terminal`.
6. Type `npm init -y` and press Enter to create a new `package.json` file.
7. Change the `scripts` section of the `package.json` file to include `"start": "node server.js"`. Make sure the second part matches the name of your server file (e.g., change it to `svr.js` if that's what you called it).
8. Type `npm install express` and press Enter to install the Express module. This creates a `node_modules` folder and a `package-lock.json` file.
    - **You must delete the `node_modules` folder before submitting your work.**
    - **You must add a `.gitignore` file to your project and include `node_modules` in it if you are pushing your work to GitHub.**
9. Type `npm start` and press Enter to start your server. Once it's running, you will not get any output in the terminal.
10. You may get an error message saying something like:
`
(node:47780) Warning: To load an ES module, set "type": "module" in the package.json or use the .mjs extension.
`
If you do, you need to change the `type` in the `package.json` file to `"type": "module"`. You need to add a new line to the `package.json` file so that it looks similar to this:
```json
{
  "name": "your-project-name",
  "version": "1.0.0",
  "description": "",
  "main": "server.js",
  "type": "module", // Add this line (remove this comment after adding it!)
  "scripts": {
    "start": "node server.js"
  },
  "author": "",
  "license": "ISC",
  "dependencies": {
    "express": "^4.17.1"
  }
}
```
11. Open your browser and go to `http://localhost:8080` to see your page (the number at the end corresponds to the port number you have in your server). End the server by pressing `Ctrl+C` in the terminal.
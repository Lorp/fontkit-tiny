## Fontkit tiny demo

We’re going to create a tiny demo web app that uses Fontkit to render a string in a given font as SVG. The font will be loaded from the web.

1. Install `npm` and `npx`. They’re included with Node.js, which you get here: `https://nodejs.org/en/download`

2. Download this repository, unzip it, and rename the enclosing folder from `fontkit-tiny-main` to `fontkit-tiny`. Place the folder somewhere it can be served as a website, e.g. as a subfolder of `~/Sites/``.

3. Change directory to `fontkit-tiny` and type:  
`npm install`
	* _This reads `package.json`, identifies all the Node modules required by your project (“the project’s dependencies”), and downloads them into a new folder `node_modules`. If you open `package.json`, you will see that only the `fontkit` module is explicitly required. All the others (“Fontkit’s dependencies”) are called for by Fontkit via its own `package.json` file._

4. We need one more thing, a “bundler”. This extracts all the required code from the modules, and “bundles” it together in one file. There are several bundlers available. We’re going to use the [Parcel](https://parceljs.org) bundler, written by the author of Fontkit, Devon Govett. You install Parcel via the command line. Type:  
`npm install --save-dev parcel`

5. Now we’re ready to create the final html file. This will create a `dist` folder containing the file `index.html`. Type:  
`npx parcel src/index.html`

6. Now go to this file in your web browser. If all is well, you should see “hello, world!”.

	* _If you open `index.html` in the `src` folder, you’ll see that string. Edit it and save the file. You can also see the font URL, the font size and the variation settings. Try changing those too, and refresh your browser. whenever you save `index.html`, Parcel detects the changes and rebuilds the bundle. You can stop Parcel via Ctrl-C._

	* _Notice the `transform` attribute in the SVG, which depends on the `fontSize` variable (try changing it) and the `upem` (units per em) of the font. Notice how the code gets Fontkit to supply this value, so you don’t normally need to touch this._

	* _You should never edit the `index.html` file in the `dist` folder. It is overwritten every time you run Parcel._

	* _A really neat thing about Parcel is that it has its own web server built in. When you run Parcel, you’ll see it gives you a URL to go to, probably `http://localhost:1234`. If you go there, and try editing and saving `index.html` (the one in the "src" subfolder), then not only does the bundled `index.html` in the `dist` folder (that you loaded with your web browser) update, but your browser gets triggered to reload the page. This cool feature isn’t entirely convenient, since its little web server does not know how to serve any other file apart from the bundled index.html. So if you have any local assets such as fonts and images, they won’t load._

7. When you’re ready to build your final web app, then you use an extra `build` commend when calling Parcel. Type:  
`npx parcel build src/index.html`

	* _This performs extra minification steps on the code. It’s not easily readable by humans._

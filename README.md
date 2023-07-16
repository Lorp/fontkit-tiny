## Fontkit tiny demo

We’re going to create a tiny demo web app that uses Fontkit to render a string in a given font as SVG. The font will be loaded from the web.

1. Make sure you have `npm` and `npx` installed. They’re included with Node.js, which you get here: https://nodejs.org/en/download

2. Create a folder that can be served by your computer’s localhost, e.g. "fontkit-tiny" served as http://localhost/fontkit-tiny . If you don’t have localhost set up, then you will need to upload the files to a web server.

3. Download this repository, unzip it, and place the files in the "`fontkit-tiny`" folder. So "`package.json`" at the top level, and "`index.html`" in the "`src`" folder.

4. cd to the "`fontkit-tiny`" folder.

5. Type "npm install" [Enter]. This reads "package.json" to identify and download all the Node modules required by your project (the "dependencies"). In this case that’s Fontkit itself and all the Node modules required by Fontkit ("Fontkit’s dependencies"). If you open "`package.json`", you will see that only the "fontkit" module is explicitly required. All the others are called for by Fontkit, via its own "package.json" file. Notice a new folder, "`node_modules`", that contains all these modules, including the "`fontkit`" folder.

6. We need one more thing, a "bundler". This extracts all the required code from each of the modules, and "bundles" it all together in one file. There are several bundlers available. We’re going to use the bundler written by the author of Fontkit itself, Devon Govett — it’s called Parcel. You install Parcel via the command line. Type "`npm install --save-dev parcel`" [Enter].

7. Now we’re ready to create the final html file. Type "`npx parcel src/index.html`" [Enter]. This creates a "`dist`" folder and an "`index.html`" inside it. Try visiting http://localhost/fontkit-tiny/dist/index.html (edit this according to the location you chose in Step 2).

8. If all is well, you should see "hello ,world!". If you open "`index.html`", you’ll see that string. Edit it and save the file. You can also see the font URL, the font size and the variation settings. Try changing those too, and refresh your browser. Notice the `"transform"` attribute in the SVG, which depends on the "`fontSize`" variable (try changing it) and the "`upem`" (units per em) of the font.

9. A very neat thing about Parcel is that it has its own web server built in. When you run Parcel, you’ll see it gives you a URL to go to, probably `http://localhost:1234`. If you go there,  you may have noticed is that when you edit and save "`index.html`"(the one in the "src" subfolder), the bundled "`index.html`" in the "`dist`" folder (that you loaded with your web browser) updates too. Not only that,  when you refresh your browser. That happens because Parcel watches your "src" folder, continually checking for changes. If it notices a change, it immediately creates a new bundle. You can stop Parcel via Ctrl-C. (Parcel also uses a built-in web server to make the bundled index.html available at http://localhost:1234, and uses WebSockets to trigger the browser to reload the page if you change the source code. This is very cool, but isn’t entirely convenient, since its little server does not know how to serve any other files apart from the bundled index.html. So if you have any local assets such as fonts and images, they won’t load.)


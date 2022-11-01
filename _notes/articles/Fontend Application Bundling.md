---
---

# Overview
[[Bundler|Bundling]] is the process of transforming source code + all required assest into a **web bundle**, which can be opened in a browser (with no additional modifications)

There are different bundlers out there
- webpack
- rollup
- esbuild
- vitejs
- parcel

## Why we need to create a bundle?
Back in the days a web application looked like this

```
// index.html
<html lang="en">  
<head>  
    <title>My webpage</title>  
    <script src="script.js"></script>
</head>  
<body>  
    <div id="root">  
        <button>My Button</button>  
    </div>  
</body>  
</html>

// script.js
var button = document.querySelector('#root > button');  
button.addEventListener('click', () => console.log('You clicked me!'));  
```

And there were no problems with this... until you have too much code

```
// index.html
<html lang="en">
<head>  
    <title>My webpage</title>  
    <script src="script1.js"></script>
    <script src="script2.js"></script>
    <script src="script3.js"></script>
    <script src="script4.js"></script>
    <script src="script5.js"></script>
    ...
</head>
...
```

It's not very easy to maintain - in order to organize your code you need to manually create these scripts, somehow share information between them (hoisting of `var`s). Imagine moving code from one script to another when performing refactoring. Also you need to manually include these scripts in correct order to HTML file.

### Too many HTTP requests problem
Another problem - each `scriptX.js` in HTML file is a new HTTP request. This is bad because each HTTP request creates a new connection with the server which takes some time.

> In other words it's faster to download *1 file of size 1Mb* than *100 files of size 10Kb*

The above is not always true, you need to consider many things like: browser caching, number of pages in your app, how frequently these pages (and scripts in them) update

> 🔍 google for "js chunking"

This whole topic is pretty deep and requires a separate article. Google for "js chunking" to understand more about it

### SPA vs MPA
https://kodytechnolab.com/single-page-apps-vs-multi-page-apps

Complex web apps today are mostly [SPA](https://en.wikipedia.org/wiki/Single-page_application)'s

And in order to create an SPA we use different technologies like:
- modular structure of files - `import`s and  `export`s
- TypeScript
- Scss or styled-components

Usually we use [webpack](https://webpack.js.org/), so we'll talk about it in this tutorial

# Webpack
Read about [concepts](https://webpack.js.org/concepts/) on webpacks web site - it's pretty well done 👍

Two main concepts to read and understand:
- `entry` - entry point to start bundling
- `output` - the output file (usually something like `bundle.js`, the name is not very important)
Very simple `webpack.config.js`  looks like this:
```js
{  
   entry: {  
      'chart-combined': './js/chart-combined-index.js',  
   },  
   output: {  
      filename: `./[name]${mode === 'production' ? '.min' : ''}.js`,  
      path: path.resolve(__dirname, 'dist'),
   },
   ...
}
```
Here it has `./js/chart-combined-index.js` file as entry point of your application - webpack will start resolving modules hierarchically from this file

Output is `./[name]...js`  where **[name]** is just a variable of `chart-combined` - this is the file which will contain all your application code

Here is the console output - in our case the output file is `~6Mb` because it's the development mode
![[Pasted image 20220825235830.png]]
> Webpack has also the production mode in which it will [[Obfuscation|obfuscate]] the output file

### Loaders
Describe the way webpack should treat different file extensions like `css`, `ts`, `txt` e.t.c

Most used loaders:
- `css-loader` - will replace `import` and `url` in your CSS
- `style-loader` - will combine the `css` files into one big `style.css` and inject it into DOM
- `babel-loader` - transpiles `js` to use ecmascript features before they are actually released; also has `@babel/preset-typescript` which compiles `ts => js`
- `esbuild-loader` - faster way of compiling `ts`

### Plugins
Additional logic to reduce the amount of hand work

Popular plugins:
- `HtmlWebpackPlugin` - created `index.html` and adds all assets like `<script>` and `<link>` with styles inside
- `CopyWebpackPlugin` - copy fonts, json files, images inside resulting app
- `ESLintPlugin` - performs eslint check during bundling

### Tree Shaking
Read about tree shaking [here](https://webpack.js.org/guides/tree-shaking/#root)

In short - it's a process of **dead-code elimination** from resulting bundle.

### Mode
Other important thing is `mode` is webpack, it can be either
- `development`
- `production`
The `developent` mode will allow you to support [[Source Maps|source maps]] which is a way to debug your code in DevTools in Chrome

### Hash content / caching
When developing bundle it is cached 

# Babel
Babel is a JS => JS compiler, or transpiler

@babel/template is a way to configure babel AST generator internally - so it's like an example of DI or I in SOLID, or middleware



links:
https://www.udemy.com/course/webpack-from-beginner-to-advanced/
https://www.freecodecamp.org/news/get-started-with-vite/

[Webpack features youtube](https://www.youtube.com/watch?v=IZGNcSuwBZs)
---
---

[[Bundler|Bundling]] is the process of transforming source code + all required assest into a **web bundle**, which can be opened in a browser (with no additional modifications)

Usually we use [webpack](https://webpack.js.org/), so we'll talk about it in this tutorial

## Webpack concepts
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


# Feri - Build

Build is the module dedicated to building destination files.

The build module lives in the file [code/6 - build.js](../../code/6 - build.js)

## Build Object

The build object is grouped into five categories.

### Build: Command and Control

* [processBuild](#buildprocessbuild)
* [processFiles](#buildprocessfiles)
* [processOneBuild](#buildprocessonebuild)

### Build: In Memory

* [coffeeScript](#buildcoffeescript)
* [css](#buildcss)
* [html](#buildhtml)
* [js](#buildjs)
* [jsx](#buildjsx)
* [markdown](#buildmarkdown)

### Build: On Disk

* [copy](#buildcopy)
* [gif](#buildgif)
* [jpg](#buildjpg)
* [png](#buildpng)

### Build: With Includes

* [concat](#buildconcat)
* [ejs](#buildejs)
* [jade](#buildjade)
* [less](#buildless)
* [pug](#buildpug)
* [sass](#buildsass)
* [stylus](#buildstylus)

### Build: Finishers

* [finalize](#buildfinalize)
* [gz](#buildgz)
* [map](#buildmap)

## Build: Command and Control

The following functions control building, setting up promise chains and concurrency.

### build.processBuild

Type: `function`

Find all source files or optionally use the files parameter to start a build process.

```
@param   {String,Object}  [files]     Optional. Glob search string like '*.html' or array of paths like ['/source/about.html', 'source/index.html']
@param   {Boolean}        [watching]  Optional and defaults to false. If true, log less information.
@return  {Promise}                    Promise that returns an array of file path strings for the files built like ['/dest/css/style.css', '/dest/index.html']
```

Note: This function is also aliased as `feri.action.build`.

### build.processFiles

Type: `function`

Create a promise chain of tasks for each file and control concurrency.

```
@param   {Object,String}  files  Array of paths like ['/source/path1', '/source/path2'] or a string like '/source/path'
@return  {Promise}               Promise that returns an array of file path strings for the files built like ['/dest/css/style.css', '/dest/index.html']
```

### build.processOneBuild

Type: `function`

Create a promise chain of building tasks based on a single file type.

```
@param   {String}   filePath  Full path to a file like '/web/source/rss.xml'
@return  {Promise}            Promise that returns a file path string if something was built otherwise undefined.
```

## Build: In Memory

The following functions do their primary task in memory.

### build.coffeeScript

Type: `function`

CoffeeScript using [coffeescript](https://www.npmjs.com/package/coffeescript).

```
@param   {Object}   obj  Reusable object originally created by build.processOneBuild
@return  {Promise}  obj  Promise that returns a reusable object.
```

### build.css

Type: `function`

Minify CSS using [clean-css](https://www.npmjs.com/package/clean-css).

```
@param   {Object}   obj  Reusable object originally created by build.processOneBuild
@return  {Promise}  obj  Promise that returns a reusable object.
```

### build.html

Type: `function`

Minify HTML using [html-minifier](https://www.npmjs.com/package/html-minifier).

```
@param   {Object}   obj  Reusable object originally created by build.processOneBuild
@return  {Promise}  obj  Promise that returns a reusable object.
```

### build.js

Type: `function`

Minify JavaScript using [uglify-js](https://www.npmjs.com/package/uglify-js).

```
@param   {Object}   obj  Reusable object originally created by build.processOneBuild
@return  {Promise}  obj  Promise that returns a reusable object.
```

### build.jsx

Type: `function`

Transform JSX files to JS using [babel-cli](https://www.npmjs.com/package/babel-cli).

```
@param   {Object}   obj  Reusable object originally created by build.processOneBuild
@return  {Promise}  obj  Promise that returns a reusable object.
```

### build.markdown

Type: `function`

Markdown using [markdown-it](https://www.npmjs.com/package/markdown-it).

```
@param   {Object}   obj  Reusable object originally created by build.processOneBuild
@return  {Promise}  obj  Promise that returns a reusable object.
```

## Build: On Disk

The following functions like working on disk based files.

### build.copy

Type: `function`

Copy source to destination.

```
@param   {Object}   obj  Reusable object originally created by build.processOneBuild
@return  {Promise}  obj  Promise that returns a reusable object.
```

### build.gif

Type: `function`

Losslessly optimize GIF files using [gifsicle](https://www.npmjs.com/package/gifsicle).

```
@param   {Object}   obj  Reusable object originally created by build.processOneBuild
@return  {Promise}  obj  Promise that returns a reusable object.
```

### build.jpg

Type: `function`

Losslessly optimize JPG files using [jpegtran-bin](https://www.npmjs.com/package/jpegtran-bin).

```
@param   {Object}   obj  Reusable object originally created by build.processOneBuild
@return  {Promise}  obj  Promise that returns a reusable object.
```

### build.png

Type: `function`

Losslessly optimize PNG files using [optipng-bin](https://www.npmjs.com/package/optipng-bin).

```
@param   {Object}   obj  Reusable object originally created by build.processOneBuild
@return  {Promise}  obj  Promise that returns a reusable object.
```

## Build: With Includes

The following functions are for file types that may contain includes.

### build.concat

Type: `function`

Concatenate files like `all.js.concat` which can contain globs and/or file path strings that point to other files.

```
@param   {Object}   obj  Reusable object originally created by build.processOneBuild
@return  {Promise}  obj  Promise that returns a reusable object.
```

### build.ejs

Type: `function`

Embedded JavaScript templates using [ejs](https://www.npmjs.com/package/ejs).

```
@param   {Object}   obj  Reusable object originally created by build.processOneBuild
@return  {Promise}  obj  Promise that returns a reusable object.
```

### build.jade

Type: `function`

Jade using [jade](https://www.npmjs.com/package/jade).

```
@param   {Object}   obj  Reusable object originally created by build.processOneBuild
@return  {Promise}  obj  Promise that returns a reusable object.
```

### build.less

Type: `function`

Less using [less](https://www.npmjs.com/package/less).

```
@param   {Object}   obj  Reusable object originally created by build.processOneBuild
@return  {Promise}  obj  Promise that returns a reusable object.
```

### build.pug

Type: `function`

Pug using [pug](https://www.npmjs.com/package/pug).

```
@param   {Object}   obj  Reusable object originally created by build.processOneBuild
@return  {Promise}  obj  Promise that returns a reusable object.
```

### build.sass

Type: `function`

Sass using [node-sass](https://www.npmjs.com/package/node-sass).

```
@param   {Object}   obj  Reusable object originally created by build.processOneBuild
@return  {Promise}  obj  Promise that returns a reusable object.
```

### build.stylus

Type: `function`

Stylus using [stylus](https://www.npmjs.com/package/stylus).

```
@param   {Object}   obj  Reusable object originally created by build.processOneBuild
@return  {Promise}  obj  Promise that returns a reusable object.
```

## Build: Finishers

The following functions are typically called at the end of a build chain. Unlike most build functions, they don't bother to check if a source file is newer than a destination file since that should have been handled already.

### build.finalize

Type: `function`

Finalize by writing memory to disk or copying source to dest, if needed.

```
@param   {Object}   obj  Reusable object originally created by build.processOneBuild
@return  {Promise}  obj  Promise that returns a reusable object.
```

### build.gz

Type: `function`

Create a gzipped version of a file to live alongside the original.

```
@param   {Object}          obj  Reusable object originally created by build.processOneBuild
@return  {Promise,Object}  obj  Promise that returns a reusable object or just the reusable object.
```

### build.map

Type: `function`

Build a map file and if needed, also make a gz version of said map file.

```
@param   {Object}          obj  Reusable object originally created by build.processOneBuild
@return  {Promise,Object}  obj  Promise that returns a reusable object or just the reusable object.
```

## License

MIT © [Daniel Gagan](https://forestmist.org)

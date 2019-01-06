## gulp-query-less
Less for [gulp-query](https://github.com/gulp-query/gulp-query)

Uses [cssnano](http://cssnano.co/) with autoprefixer for optimization

This plugin provides automatic source maps, compiling Less into CSS, autoprefixing and minification.
Write your CSS rules without vendor prefixes — autoprefixer will do everything itself

```text
npm install gulp-query gulp-query-less
```

### Example
Paste the code into your `gulpfile.js` and configure it
```javascript
let build = require('gulp-query')
  , less = require('gulp-query-less')
;
build((query) => {
    query.plugins([less])
      .less('src/less/app.less','css/','app')

      .less('src/less/admin.less','css/undercover.css',{
        paths: [
          ...
        ]
      })

      .less({
        from: 'src/less/main.less',
        to: 'css/',
        name: 'main'
      })
      ;
});
```
And feel the freedom
```
gulp
gulp --production // For production
gulp watch // Watching change
gulp less // Only for less
gulp less:app // Only for app.less
gulp less:admin less:main watch // Watching change only for admin and main
...
```

### Options
```javascript
.less({
    name: "task_name", // For gulp less:task_name 
    from: "less/app.less",
    to: "css/",
    source_map: true,
    source_map_type: 'inline',
    full: false, // if set true is without compress in prod
    paths: [
        //'../node_modules/compass-mixins/lib/', // relative path from gulpfile.js 
    ],
    autoprefixer: {
      browsers: ["> 1%", "last 2 versions"],
    }
})
```
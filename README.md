# gulp-static-php [![npm version](https://badge.fury.io/js/gulp-static-php.svg)](https://badge.fury.io/js/gulp-static-php)

A static site generator that uses php to render pages

## install
```bash
npm install --save gulp-static-php
```

## gulp task
```javascript
var gulp = require('gulp');
var gulpStaticPhp = require('gulp-static-php');

gulp.task('static-generator', function() {
	gulp.src('src/index.php')
		.pipe(gulpStaticPhp())
		.pipe(gulp.dest('./web'));
});
```

On first run the plugin will call the php file input in source with the default url index.html simular to the following command line execution

```bash
php src/index.php --url=/index.html
```
afterwards the plugin will crawl the html result for links starting with / to create pages for those as well, and those will call for new pages as well until all the pages are generated. 

Inside php additional runtime information can be found in 
```php
var_dump($GLOBALS["argv"]);
```
will result in 

```php
array(2) {
  [0]=>
  string(41) "/project/css-footprint-demo/src/index.php"
  [1]=>
  string(19) "--url=/index.html"
}
```

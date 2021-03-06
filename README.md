Requirements
------------
- PHP 5.6 CLI installed
- Download Ngn components
```bash
mkdir ngn-env
cd ngn-env
git clone https://github.com/majexa/ngn.git
git clone https://github.com/majexa/ngn-cs.git
git clone https://github.com/majexa/run.git
git clone https://github.com/mootools/mootools-core
git clone https://github.com/mootools/mootools-more
```

Usage
-----

Next example

- Parses `<script>` tags in index.html
- Builds NgnJs classes tree and collect relevant CSS files
- Places it `build/m/css` folder

Contents of index.html
```html
<script>
new Ngn.SomeClass();
</script>
```


```javascript
var gulp = require('gulp');
var ngnCss = require('gulp-ngn-css');

gulp.task('build', function () {
  var opt = {
    buildFolder: 'build/m',
    name: 'main'
  };
  var reportOptions = {
    err: true,
    stderr: true,
    stdout: true
  };
  gulp.src('index.html', {read: false})
    .pipe(ngnCss(opt))
    .pipe(ngnCss.reporter(reportOptions))
});
```

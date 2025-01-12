# gulp-bower
> Install Bower packages.

This task is designed for gulp 3.

## Usage

First, install `gulp-bower` as a development dependency:

```shell
npm install --save-dev gulp-bower
```

Then, add it to your `gulpfile.js`:

```javascript
var gulp = require('gulp');
var bower = require('gulp-bower');

gulp.task('bower', function() {
  return bower();
});
```

This defaults to the directory configured in `./.bowerrc` or to `./bower_components` when no `.bowerrc` could be found.

You can also specify a custom Bower directory:

```javascript
var gulp = require('gulp');
var bower = require('gulp-bower');

gulp.task('bower', function() {
  return bower('./my_bower_components')
    .pipe(gulp.dest('lib/'))
});
```

To set the current working directory, you must pass in an `options` object:

```javascript
var gulp = require('gulp');
var bower = require('gulp-bower');

gulp.task('bower', function() {
  return bower({ directory: './my_bower_components', cwd: './myapp' })
    .pipe(gulp.dest('lib/'))
});
```

By default `gulp-bower` runs `install` command for Bower.
Using `cmd` property, you can specify the custom command. (e.g. `update`)

```javascript
var bower = require('gulp-bower');

gulp.task('bower', function() {
  return bower({ cmd: 'update'});
});
```



## Changelog

### 0.0.13
- Forked from zont/gulp-bower.
- Fixed passing options to prune command.

### 0.0.12
- Fixed command passing to also handle nested commands (by mechanoid)

### 0.0.11
- Fixed dependencies (by serbrech)

### 0.0.10
- Fixed #28

### 0.0.9
- Fixed #19
- Fixed undefined cwd bug

### 0.0.8
- Fixed dependencies versions (by Karl-Gustav)
- Fixed cwd bug (by mlegenhausen)

### 0.0.7
- Added commands support (by Keksinautin)

### 0.0.6
- Added ability to pass in an initialization object that allows a cwd to be specified (by cb1kenobi)

### 0.0.5
- Emits "end", so the consumer knows when bower is done installing (by agzam)

### 0.0.4
- fixed custom bower directory bug

### 0.0.3
- add logging (by squarejaw)

### 0.0.2
- parse .bowerrc for the bower install directory or allow the user to specify the directory (by eboskma)

### 0.0.1
- initial release

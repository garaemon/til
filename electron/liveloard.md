# liveloading on electron
see http://qiita.com/Quramy/items/90d61ff37ca1b95a7f6d

## Setup
Use gulp and electron-connect
```sh
npm install gulp electron-connect --save-dev
```

## Filesystem
electron depends on:
1. css for rendering
2. html for rendering
3. js for render process
4. js for browser process

```
root/
   |
   +---src/
   |     +-- app.js
   |     +-- browser/
   |     |     +--- *.js
   |     +-- renderer/
   |           +--- *.html
   |           +--- *.js
   +---styles/
         +--- *css
```

### package.json
We need to update package.json for the filesystem mentioned above.
```json
{
...
  "scripts": {
  ...
  "start": "electron src/app.js"
  },
  "main": "src/app.js",
}
```

## Gulpfile.js
```js
'use strinct';

var gulp = require('gulp');
var electronServer = require('electron-connect').server;
gulp.task('serve', function () {
  var electron = electronServer.create();
  // Startup electron
  electron.start();

  // Restart electron when resources of browser process are updated
  gulp.watch(['src/app.js', 'src/browser/**/*.js'], electron.restart);

  // Reload render process when resources of render process are updated
  gulp.watch(['styles/**/*.css', 'src/renderer/**/*.{html,js}'], electron.reload);
});

```

## Run
```sh
$ gulp serve
```

# liveloading on electron with JSX
boilerplate is available on [garaemon/electron-liveload-jsx-sample](https://github.com/garaemon/electron-liveload-jsx-sample).

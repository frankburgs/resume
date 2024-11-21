# Setup from clone
- Run below commands and you should be able to save a nice pdf of the resume given you also have live server installed.

``` shell
$ git clone thisgitreponame
$ npm i # Given package.json is present with tailwindcss as devdependency.
```

# Setup from scratch
- Given Node installed, run below commands.

``` ruby
$ npm i tailwindcss
$ npx tailwindcss init # Creates tailwind.config.js
```

- Modify tailwind.config.json

``` js
/** @type {import('tailwindcss').Config} */
module.exports = {
  content: ["./dist/*.html"],
  theme: {
    extend: {},
  },
  plugins: [],
}
```

- 📁 Create dist folder in main, containing index.html

- 📁 Create src folder in main, containing input.css, paste the following

``` css
@tailwind base;
@tailwind components;
@tailwind utilities;
```

- Create output css file in dist folder and watch for changes.

``` shell
npx tailwindcss -i ./src/input.css -o ./dist/output.css --watch
```

- Add the following to index.html head

``` html
<link rel="stylesheet" href="output.css">
```

- In package.json, add the following "scripts" after "devdependencies"

``` js
  "scripts": {
    "dev": "npx tailwindcss -i ./src/input.css -o ./dist/output.css --watch"
  }
```
# Font
- Place scalable .ttf file in src folder
- Add to input.css
``` css
@layer base {
    @font-face {
      font-family: mulish;
      font-weight: 400;
      src: url(./mulish.ttf) format("ttf");
    }
}
```
- Add into theme/extend in tailwind.configjs
``` js
fontFamily: {
  'sans':['mulish', 'sans-serif']
}
```
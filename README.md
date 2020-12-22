# hello-electron-webpack

### vanilla electron-webpack boilerplate
- `mkdir -p src/{main,renderer}`
- `touch README.md .gitignore src/main/index.js src/renderer/index.js`
- `yarn init -y`
- `yarn add -D electron electron-builder electron-webpack webpack@4.42.0`
- add to .gitignore:
  ```
  dist/
  node_modules/
  .idea/  
  ```
- add to package.json:
  ```
  "scripts": {
    "dev": "electron-webpack dev",
    "compile": "electron-webpack",
    "dist": "yarn compile && electron-builder",
    "dist:dir": "yarn dist --dir -c.compression=store -c.mac.identity=null"
  }
  ```
- populate basic content for both index.js files in src
- `yarn dev`

### add eslint (! removed, in favor of lint-staged)
- `yarn add -D electron-webpack-eslint`
- `touch .eslintrc.js`
- add to .eslintrc.js:
  ```
  module.exports = {
    extends: 'eslint:recommended',
    parser: 'babel-eslint',
    parserOptions: { sourceType: 'module' },
    env: { browser: true, node: true }
  }
  ```
- `yarn dev` or `eslint src/main/index.js` to try out eslint

### add typescript
- `yarn add -D electron-webpack-ts typescript`
- `touch tsconfig.json`
- add to tsconfig.json:
  ```
  { "extends": "./node_modules/electron-webpack/tsconfig-base.json" }
  ```
- `mv src/main/index.js src/main/index.ts`
- `mv src/renderer/index.js src/renderer/index.ts`

### todo
- add prettier and eslint (remove electron-webpack-eslint)
- add and configure husky and lint-staged via `npx mrm lint-staged`
- add jest or mocha/chai/sinon
- add nyc
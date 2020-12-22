# electron-webpack-typescript-starter

## todo
- add tests. get to 100% coverage
- ci, auto-updater

## genesis

#### vanilla electron-webpack boilerplate
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

#### add typescript
- `yarn add -D electron-webpack-ts typescript`
- `touch tsconfig.json`
- add to tsconfig.json:
  ```
  { "extends": "./node_modules/electron-webpack/tsconfig-base.json" }
  ```
- `mv src/main/index.js src/main/index.ts`
- `mv src/renderer/index.js src/renderer/index.ts`

#### init git
- `git init && git add . && git commit -m "initial commit"`

#### add prettier, eslint, husky, lint-staged
- `yarn add -D prettier eslint`
- `npx mrm lint-staged`
- looks like artifact file left: `4`. delete it
- modify package.json to:
  ```
  "lint-staged": {
    "src/**/*.{js,ts,json,md}": [
      "prettier --write",
      "eslint --fix-dry-run"
    ]
  }
  ```
- `yarn add -D @typescript-eslint/parser @typescript-eslint/eslint-plugin`
- add to package.json:
  ```
  "eslintConfig": {
    "parser": "@typescript-eslint/parser",
    "plugins": ["@typescript-eslint"],
    "extends": ["plugin:@typescript-eslint/recommended"]
  }
  ```

#### add jest
- `yarn add -D jest @types/jest`
- add to package.json:
  ```
  "jest": {
    "collectCoverageFrom": [ "src/**/*.ts" ]
  }
  ```
- add to package.json scripts: `"test": "jest --coverage"`
- `mkdir -p src/__tests__/{main,renderer}`
- `touch src/__tests__/main/index.test.ts`
- add to .gitignore: `coverage/`
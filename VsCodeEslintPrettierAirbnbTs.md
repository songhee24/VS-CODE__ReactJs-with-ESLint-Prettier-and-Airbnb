# Setup React App with TypeScript, ESLint and Prettier

![image](https://user-images.githubusercontent.com/44497623/229729169-02e56c48-6d75-40fe-91dc-0e261b54150a.png)

### Let's create development configuration for a React application with TypeScript, ESLint and Prettier.

## Create React App

Let's create a new project with create-react-app tool.

```
npx create-react-app my-app --template typescript
```
## ESLint

ESLint will statically analyze our code to quickly find problems.
```
npm i --save-dev typescript @typescript-eslint/parser @typescript-eslint/eslint-plugin eslint-config-airbnb-typescript eslint-plugin-react-hooks eslint-plugin-jest eslint-plugin-import
```
Then we can install the packages for Airbnb config:

```
npx install-peerdeps --dev eslint-config-airbnb
```

## Prettier
Prettier is an opinionated code formatter. It enforces a consistent style by parsing your code and re-printing it with its own rules that take the maximum line length into account, wrapping code when necessary.

```
npm i --save-dev prettier eslint-config-prettier eslint-plugin-prettier
```

## ESLint config
Let's create .eslintrc file in the root of the project and paste next code:

```
// .eslintrc
{
  "parser": "@typescript-eslint/parser",
  "parserOptions": {
    "ecmaFeatures": {
      "jsx": true,
      "useJSXTextNode": true
    },
    "ecmaVersion": 2018,
    "sourceType": "module",
    "project": "./tsconfig.json"
  },
  "extends": [
    "airbnb-typescript",
    "airbnb/hooks",
    "plugin:@typescript-eslint/recommended",
    "plugin:jest/recommended",
    "prettier",
    "prettier/react",
    "prettier/@typescript-eslint",
    "plugin:prettier/recommended"
  ],
  "plugins": ["react", "react-hooks", "@typescript-eslint", "jest"],
  "env": {
    "browser": true,
    "es6": true,
    "jest": true
  },
  "globals": {
    "Atomics": "readonly",
    "SharedArrayBuffer": "readonly"
  },
  "rules": {
    "linebreak-style": "off",
    "react-hooks/rules-of-hooks": "error",
    "react-hooks/exhaustive-deps": "warn",
    "prettier/prettier": [
      "error",
      {
        "endOfLine": "auto"
      }
    ],
    "import/extensions": [
      "error",
      "ignorePackages",
      {
        "js": "never",
        "jsx": "never",
        "ts": "never",
        "tsx": "never"
      }
    ]
  }
}
```


![Ironhack Logo](https://i.imgur.com/1QgrNNw.png)

# React | Setup

## Chrome extesions

- [react-developer-tools](https://chrome.google.com/webstore/detail/react-developer-tools/fmkadmapgofadopljbjfkapdkoienihi?hl=en)

## Visual Studio Code

- [Debugger for Chrome](https://marketplace.visualstudio.com/items?itemName=msjsdiag.debugger-for-chrome)
- [ES7 React/Redux/GraphQL/React-Native snippets](https://marketplace.visualstudio.com/items?itemName=dsznajder.es7-react-js-snippets)

## ESlint

```
$ npm install --save-dev eslint eslint-config-airbnb-base eslint-plugin-import eslint-plugin-react
```

**.eslintrc.json**
```json
{
  "env": {
    "browser": true
  },
  "parserOptions": {
    "ecmaVersion": 6,
    "sourceType": "module",
    "ecmaFeatures": {
      "jsx": true
    }
  },
  "plugins": [
    "react",
    "import"
  ],
  "extends": [
    "airbnb-base",
    "plugin:react/recommended"
  ],
  "rules": {
    "max-len": "off",
    "object-curly-newline": ["error", {
      "ObjectExpression": { "multiline": true },
      "ObjectPattern": { "multiline": true }
    }],
    "react/prop-types": [ 2, { "ignore": ["children"]}]
  }
}
```
# react-native-sass-transformer

Load Sass files to [react native style objects](https://facebook.github.io/react-native/docs/style.html).

## Usage

### Step 1: Install

```sh
yarn add --dev react-native-sass-transformer node-sass
```

### Step 2: Configure the react native packager

Add this to your `rn-cli.config.js` (make one if you don't have one already):

```js
module.exports = {
  getTransformModulePath() {
    return require.resolve("react-native-sass-transformer");
  },
  getSourceExts() {
    return ["scss", "sass"];
  }
};
```

## How does it work?

Your `App.scss` file might look like this:

```scss
.myClass {
  color: blue;
}
.myOtherClass {
  color: red;
}
```

When you import your stylesheet:

```js
import styles from "./App.scss";
```

Your imported styles will look like this:

```js
var styles = {
  myClass: {
    color: "blue"
  },
  myOtherClass: {
    color: "red"
  }
};
```

You can then use that style object with an element:

```jsx
<MyElement style={styles.myClass} />
```

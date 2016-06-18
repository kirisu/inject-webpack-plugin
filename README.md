webpack Dependency Injection Plugin
===================

A simple webpack plugin for injecting dependencies.

Installation
------------
Install the plugin with npm:
```shell
$ npm install inject-webpack-plugin --save-dev
```

Basic Usage
-----------
In your `webpack.config.js`

```js
import InjectWebpackPlugin from 'webpack-inject-plugin';

export default {
    // ...
    plugins: [
      new InjectWebpackPlugin({
        'path/to/file.js': 'path/to/another/file.js',
        'react': 'replacing/react/like/a/boss.js'
      });
    ]
};
```

This will replace any instances of `path/to/file.js` with `path/to/file.dev.js` as well as allowing you to replace `react` if you so wish.

Useful for getting around things like [this](https://github.com/gaearon/redux-devtools/blob/master/docs/Walkthrough.md#storeconfigurestorejs-1) by combining with environment variables. For example:

```js
if (process.env.NODE_ENV === 'development') {
  plugins.push(
    new InjectWebpackPlugin({
      'configureStore.js': 'configureStore.dev.js'
    });
  )
}
```

This plugin has no tests and was the simplest implementation I could find. Any help with improving and creating tests is greatly appreciated.
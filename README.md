Favicons Webpack Plugin
========================================
[![npm version](https://badge.fury.io/js/favicons-webpack-plugin.svg)](http://badge.fury.io/js/favicons-webpack-plugin) [![Dependency Status](https://david-dm.org/jantimon/favicons-webpack-plugin.svg)](https://david-dm.org/jantimon/favicons-webpack-plugin) [![Build status](https://travis-ci.org/jantimon/favicons-webpack-plugin.svg)](https://travis-ci.org/jantimon/favicons-webpack-plugin) [![js-semistandard-style](https://img.shields.io/badge/code%20style-semistandard-brightgreen.svg?style=flat-square)](https://github.com/Flet/semistandard)

Allows to use the [favicons](https://github.com/haydenbleasel/favicons) generator with webpack

Installation
------------
You must be running webpack on node 4.x or higher as [favicons](https://github.com/haydenbleasel/favicons) requires this. 

Install the plugin with npm:
```shell
$ npm install --save-dev favicons-webpack-plugin
```

Basic Usage
-----------
Add the plugin to your webpack config as follows:

```javascript
plugins: [
  new FaviconsWebpackPlugin('my-logo.png')
]  
```

This basic configuration will generate [37 different icons](https://github.com/jantimon/favicons-webpack-plugin/tree/master/test/fixtures/expected/default/icons-366a3768de05f9e78c392fa62b8fbb80) for iOS devices, Android devices and the Desktop browser out of your `my-logo.png` file.
It can optionally also generate a [JSON file with all information about the icons](https://github.com/jantimon/favicons-webpack-plugin/blob/master/test/fixtures/expected/default/iconstats.json) for you.

If you are using with [html-webpack-plugin](https://github.com/ampedandwired/html-webpack-plugin) it will also inject the necessary html for you:

https://github.com/jantimon/favicons-webpack-plugin/blob/master/test/fixtures/expected/default-with-html/index.html

```html
  <link rel="apple-touch-icon" sizes="57x57" href="icons-366a3768de05f9e78c392fa62b8fbb80/apple-touch-icon-57x57.png">
  <link rel="apple-touch-icon" sizes="60x60" href="icons-366a3768de05f9e78c392fa62b8fbb80/apple-touch-icon-60x60.png">
  <link rel="apple-touch-icon" sizes="72x72" href="icons-366a3768de05f9e78c392fa62b8fbb80/apple-touch-icon-72x72.png">
  ...
  ...
  <link rel="apple-touch-startup-image" media="(device-width: 768px) and (device-height: 1024px) and (orientation: portrait) and (-webkit-device-pixel-ratio: 2)" href="icons-366a3768de05f9e78c392fa62b8fbb80/apple-touch-startup-image-1536x2008.png">
```


Advanced Usage
-----------

```javascript
plugins: [
  new FaviconsWebpackPlugin({
    logo: 'my-logo.png',                // Your source logo
    prefix: 'icons-[hash]/',            // The prefix for all image files (might be a folder or a name)
    filename: false,                     // if you set this to a String such as 'iconstats-[hash].json', the plugin will generate a json file with that name containing all favicon information
    inject: true,                       // Inject the html into the html-webpack-plugin
    background: '#fff',                 // favicon background color (see https://github.com/haydenbleasel/favicons#usage)
    title: 'Webpack App',               // favicon app title (see https://github.com/haydenbleasel/favicons#usage)

    // which icons should be generated (see https://github.com/haydenbleasel/favicons#usage)
    icons: {
      android: true,
      appleIcon: true,
      appleStartup: true,
      coast: false,
      favicons: true,
      firefox: true,
      opengraph: false,
      twitter: false,
      yandex: false,
      windows: false
    }
  })
]  
```


# Contribution

You're free to contribute to this project by submitting [issues](https://github.com/jantimon/favicons-webpack-plugin/issues) and/or [pull requests](https://github.com/jantimon/favicons-webpack-plugin/pulls). This project is test-driven, so keep in mind that every change and new feature should be covered by tests.
This project uses the [semistandard code style](https://github.com/Flet/semistandard).

# License

This project is licensed under [MIT](https://github.com/jantimon/favicons-webpack-plugin/blob/master/LICENSE).

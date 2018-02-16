---
title: Webpack плагины
description: Как добавить плагины в свое Nuxt.js приложение?
---

# Как добавить плагины для Webpack'а?

В вашем `nuxt.config.js` файле добавьте:

```js
const webpack = require('webpack')

module.exports = {
  build: {
    plugins: [
      new webpack.ProvidePlugin({
        '$': 'jquery',
        '_': 'lodash'
        // И т.д.
      })
    ]
  }
}
```

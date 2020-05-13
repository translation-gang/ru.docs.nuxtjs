---
title: PostCSS плагины
description: Как добавить PostCSS плагины?
---

# Добавление PostCSS плагинов

В вашем файле конфигурации `nuxt.config.js` укажите:

```js
module.exports = {
  build: {
    postcss: {
      'postcss-nested': {},
      'postcss-responsive-type': {},
      'postcss-hexrgba': {},
    }
  }
}
```

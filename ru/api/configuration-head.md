---
title: "API: Свойство head"
description: Nuxt.js позволяет определять все метаданные вашего приложения через nuxt.config.js
---

# Свйоство head

> Nuxt.js позволяет через `nuxt.config.js` определять метаданные вашего приложения, используя свойство `head`

- Тип: `Object`

```js
module.exports = {
  head: {
    titleTemplate: '%s - Nuxt.js',
    meta: [
      { charset: 'utf-8' },
      { name: 'viewport', content: 'width=device-width, initial-scale=1' },
      { hid: 'description', name: 'description', content: 'Meta description' }
    ]
  }
}
```

Список опций, которые можно передать в `head` можно посмотреть в документации к [vue-meta](https://github.com/declandewet/vue-meta#recognized-metainfo-properties).

<p class="Alert Alert--teal"><b>ИНФОРМАЦИЯ:</b> 
Вы так же можете использовать `head` внутри компонентов-страниц и обращаться к ним с помощью указателя `this`. Читайте раздел "Свойство head компонента"](/api/pages-head).
</p>

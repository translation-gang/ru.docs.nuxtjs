---
title: "API: Метод head"
description: Nuxt.js использует vue-meta для обновления заголовков и HTML атрибутов вашего приложения.
---

# Метод head

> Nuxt.js использует [vue-meta](https://github.com/declandewet/vue-meta) для обновления `заголовков` и `HTML атрибутов` вашего приложения.

- **Тип:** `Object` или `Function`

Используйте метод `head`, чтобы установить HTML Head теги для текущей страницы.

Ваши данные в компоненте доступны через `this` в методе `head`. Вы можете использовать данные страницы для установления пользовательских мета тегов.

```html
<template>
  <h1>{{ title }}</h1>
</template>

<script>
export default {
  data () {
    return {
      title: 'Hello World!'
    }
  },
  head () {
    return {
      title: this.title,
      meta: [
        { hid: 'description', name: 'description', content: 'My custom description' }
      ]
    }
  }
}
</script>
```

<p class="Alert">Для того, чтобы избежать дубликатов в компонентах потомках, пожалуйста устанавливайте уникальный идентификатор через ключ `hid`. [Подробно прочитать об этом](https://github.com/declandewet/vue-meta#lists-of-tags).</p>

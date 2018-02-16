---
title: "API: layout свойство"
description: Каждый файл (первого уровня) в директории `layouts` создаёт пользовательский layout, доступный с layout свойством в компонент страницы.
---

# layout свойство

> Каждый файл (первого уровня) в директории `layouts` создаёт пользовательский layout, доступный с layout свойством в компонент страницы.

- **Type:** `String` или `Function` (По-умолчанию: `'default'`)

Используйте `layout` ключ в ваших компонент страницах, чтобы определить, какой layout использовать: 

```js
export default {
  layout: 'blog',
  // ИЛИ
  layout (context) {
    return 'blog'
  }
}
```

В примере, Nuxt.js подключит `layouts/blog.vue` файл как layout для этой компонент страницы.

Просмотрите [демонстрационное видео](https://www.youtube.com/watch?v=YOKnSTp7d38) чтобы увидеть это в действии.

Чтобы понять, как layouts работают с Nuxt.js, взгляните на [layout документацию](/guide/views#layouts).

---
title: "API: Свойство scrollToTop"
description: Свойство `scrollToTop` позволяет вам сказать Nuxt.js скроллить к началу до рендеринга страницы
---

# Свойство scrollToTop

> Свойство `scrollToTop` позволяет вам сказать Nuxt.js скроллить к началу до рендеринга страницы

- **Тип:** `Boolean` (по-умолчанию: `false`)

По-умолчанию, Nuxt.js скроллит к началу, когда вы переходите на другую страницу, но с потомками маршрутов, Nuxt.js сохраняет скролл позицию. Если вы хотите сказать Nuxt.js, скролить к началу, когда рендерится ваш потомок маршрута, то установите `scrollToTop: true`: 

```html
<template>
  <h1>Мой компонент потомок</h1>
</template>

<script>
export default {
  scrollToTop: true
}
</script>
```

Если вы хотите переписать поведение скролла по-умолчанию nuxt.js, взгляните на [scrollBehavior опцию](/api/configuration-router#scrollBehavior).

---
title: "API: The <nuxt-link> Component"
description: Link the pages between them with nuxt-link.
---

# The &lt;nuxt-link&gt; Component

> Этот компонент используется для обеспечения навигации между компонентами страницы и повышения производительности с помощью интеллектуальной предварительной выборки.
  
Компонент `<nuxt-link>` является неотъемлемой частью Nuxt. Его следует использовать для навигации по вашему приложению, аналогично компоненту `<router-link>` в традиционном приложении Vue. Фактически, `<nuxt-link>` расширяет `<router-link>`. Это означает, что он принимает те же свойства и может использоваться таким же образом. Прочитайте документацию [Vue Router](https://router.vuejs.org/en/api/router-link.html) для получения дополнительной информации.

Example (`pages/index.vue`):

```html
<template>
  <div>
    <h1>Home page</h1>
    <nuxt-link to="/about">About (Внутренняя ссылка, которая принадлежит приложению Nuxt)</nuxt-link>
    <a href="https://nuxtjs.org">Внешняя ссылка на другую страницу</a>
  </div>
</template>
```

Aliases: `<n-link>`, `<NuxtLink>`, и `<NLink>`

Добавлено с Nuxt.js v2.4.0

Чтобы улучшить скорость отклика ваших приложений Nuxt.js, когда ссылка будет отображаться в области просмотра, Nuxt.js автоматически предварительно извлечет разделенную кодом страницу. Эта функция основана на файле [quicklink.js](https://github.com/GoogleChromeLabs/quicklink) от Google Chrome Labs.

Чтобы отключить предварительную выборку связанной страницы, вы можете использовать атрибут `no-prefetch`. Начиная с Nuxt.js v2.10.0, вы также можете использовать команду `:prefetch` со значением `false`:

```html
<n-link to="/about" no-prefetch>About page not pre-fetched</n-link>
<n-link to="/about" :prefetch="false">About page not pre-fetched</n-link>
```
Вы можете глобально настроить это поведение с [router.prefetchLinks](https://nuxtjs.org/api/configuration-router#prefetchlinks).

Начиная с Nuxt.js v2.10.0, если вы установили для [router.prefetchLinks](https://nuxtjs.org/api/configuration-router#prefetchlinks) значение `false` глобально, но хотите предварительно выбрать конкретную ссылку, вы можете использовать `prefetch` атрибут:

```html
<n-link to="/about" prefetch>О предварительно загруженной странице</n-link>
```

`prefetched-class` также доступен для настройки добавляемого класса, когда разделенная по коду страница была предварительно выбрана. Обязательно настройте эту функцию глобально с [router.linkPrefetchedClass](https://nuxtjs.org/api/configuration-router#linkprefetchedclass).

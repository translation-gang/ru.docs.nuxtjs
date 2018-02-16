---
title: "API: Свойство middleware"
description: Устанавливает middleware для конкретной страницы приложения.
---

# Свойство middleware

- Type: `String` или `Array`
  - Items: `String`

Устанавливает middleware для конкретной страницы приложения.

Пример:

`pages/secret.vue`:

```html
<template>
  <h1>Секретная страница</h1>
</template>

<script>
export default {
  middleware: 'authenticated'
}
</script>
```

`middleware/authenticated.js`:

```js
export default function ({ store, redirect }) {
  // Если пользователь не аутентифицирован
  if (!store.state.authenticated) {
    return redirect('/login')
  }
}
```

Чтобы узнать больше о middleware, смотрите [middleware документация](/guide/routing#middleware).

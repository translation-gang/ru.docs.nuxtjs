---
title: "API: Метод validate"
description: Nuxt.js позволяет определить метод валидации в вашем динамическом компоненте
---

# Метод validate

> Nuxt.js позволяет определить метод валидации в вашем динамическом компоненте

- **Type:** `Function`

```js
validate({ params, query, store }) {
  return true // Ничего не произойдет
  return false // Остановит рендер и покажет страницу ошибки 404
}
```

Рассмотрим на примере: `pages/users/_id.vue`.

Если метод не вернет `true`, Nuxt.js автоматически покажет страницу с ошибкой 404

```js
export default {
  validate ({ params }) {
    // Должно быть цифрой
    return /^\d+$/.test(params.id)
  }
}
```

Пример того что вы также можете использовать данные из [хранилища состояния](/guide/vuex-store) предварительно заполненное в [`nuxtServerInit`](/guide/vuex-store#the-nuxtserverinit-action)):

```js
export default {
  validate ({ params, store }) {
    // Проверяем что `params.id` является существующей категорией
    return store.state.categories.some((category) => category.id === params.id)
  }
}
```

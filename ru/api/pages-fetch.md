---
title: "API: Метод fetch"
description: Метод `fetch` используется для заполнения хранилища до рендеринга страницы. Он работает аналогично `asyncData` методу, за исключением того, что не устанавливает data в компоненте.
---

# Метод fetch

> Метод `fetch` используется для заполнения хранилища до рендеринга страницы. Он работает аналогично методу `asyncData`, за исключением того, что не устанавливает data в компоненте.

- **Тип:** `Function`

Метод `fetch`, *если установлен*, вызывается каждый раз до загрузки компонента (**только для компонентов страниц**). Он может быть вызван на стороне сервера или до перехода на соответствующий маршрут.

Метод `fetch` получает [`контекст`](/api/context) первым аргументом и мы можем это использовать, чтобы получать какие-то данные и заполнять хранилище. Чтобы сделать метод `fetch` асинхронным, **возвращайте Promise**, тогда nuxt.js будет ждать, пока метод не будет выполнен полностью до рендеринга компонента.

Пример `pages/index.vue`:

```html
<template>
  <h1>Звёзды: {{ $store.state.stars }}</h1>
</template>

<script>
export default {
  fetch ({ store, params }) {
    return axios.get('http://my-api/stars')
    .then((res) => {
      store.commit('setStars', res.data)
    })
  }
}
</script>
```

Вы также можете использовать `async`/`await`, чтобы сделать Ваш код чище:

```html
<template>
  <h1>Звёзды: {{ $store.state.stars }}</h1>
</template>

<script>
export default {
  async fetch ({ store, params }) {
    let { data } = await axios.get('http://my-api/stars')
    store.commit('setStars', data)
  }
}
</script>
```

## Vuex

Если вы хотите вызывать действия хранилища, то используйте `store.dispatch` внутри `fetch`, не забывая дождаться конца действия, используя `async`/`await`:

```html
<script>
export default {
  async fetch ({ store, params }) {
    await store.dispatch('GET_STARS');
  }
}
</script>
```

`store/index.js`

```js
// ...
export const actions = {
  async GET_STARS ({ commit }) {
    const { data } = await axios.get('http://my-api/stars')
    commit('SET_STARS', data)
  }
}
```

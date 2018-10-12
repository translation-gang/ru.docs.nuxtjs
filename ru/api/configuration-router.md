---
title: "API: Свойство router"
description: Параметр router позволяет конфигурировать роутер NuxtJS.
---

#  Параметр route

> Параметр router позволяет конфигурировать роутер NuxtJS. ([vue-router](https://router.vuejs.org/en/)).

## base

- Тип: `String`
- По-умолчанию: `'/'`

Основной адрес приложения. Наприме, если все одностраничное приложение расположено в `/app/`,  то свойство base должно иметь значение  `'/app/'`.

Пример (`nuxt.config.js`):
```js
module.exports = {
  router: {
    base: '/app/'
  }
}
```

<p class="Alert Alert-blue">Когда `base` задан, nuxt.js добавляет `<base href="{{ router.base }}"/>` в <head> .</p>

> Это свойство предоставлятеся из vue-router [Router constructor](https://router.vuejs.org/en/api/options.html).

## extendRoutes

- Тип: `Function`

Вы можете расширять роуты, сгенерированные nuxt.js с помощью параметра `extendRoutes`.
Пример добавления произвольного пути

`nuxt.config.js`
```js
module.exports = {
  router: {
    extendRoutes (routes, resolve) {
      routes.push({
        name: 'custom',
        path: '*',
        component: resolve(__dirname, 'pages/404.vue')
      })
    }
  }
}
```
Схема объекта пути должна соответствовать схеме [vue-router](https://router.vuejs.org/en/).

## linkActiveClass

- Type: `String`
- Default: `'nuxt-link-active'`

Глобальнная настройка [`<nuxt-link>`](/api/components-nuxt-link). Указывает, какой класс будет применяться к ссылке на активный путь. 

Example (`nuxt.config.js`):
```js
module.exports = {
  router: {
    linkActiveClass: 'active-link'
  }
}
```

> Это свойство предоставлятеся из vue-router[vue-router Router constructor](https://router.vuejs.org/en/api/options.html).

## linkExactActiveClass

- Тип: `String`
- По-умолчанию: `'nuxt-link-exact-active'`

Глобальнная настройка [`<nuxt-link>`](/api/components-nuxt-link). Указывает, какой класс будет применяться к ссылке на активный в данный момент путь

Пример (`nuxt.config.js`):
```js
module.exports = {
  router: {
    linkExactActiveClass: 'exact-active-link'
  }
}
```

> Это свойство предоставлятеся из vue-router[vue-router Router constructor](https://router.vuejs.org/en/api/options.html).

## middleware

- Тип: `String` или `Array`
  - Элементы: `String`

Задает дефолтное промежуточное ПО для каждой страницы приложения

Пример:

`nuxt.config.js`
```js
module.exports = {
  router: {
    // Запускать промежуточное ПО middleware/user-agent.j на каждорй странице
    middleware: 'user-agent'
  }
}
```

`middleware/user-agent.js`
```js
export default function (context) {
  // Добавить свойство userAgent в контекст(Доступен в `data` и `fetch`)
  context.userAgent = context.isServer ? context.req.headers['user-agent'] : navigator.userAgent
}
```


Чтобы больше узнать о Миддлвейрах (Промежуточное ПО), прочитайте [middleware guide](/guide/routing#middleware).

## mode

- Тип: `String`
- По-умолчанию: `'history'`

Режим работы роутера. Не рекомендуется изменять из-за серверного рендеринга

Пример (`nuxt.config.js`):
```js
module.exports = {
  router: {
    mode: 'hash'
  }
}
```

> This option is given directly to the vue-router [Router constructor](https://router.vuejs.org/en/api/options.html).

## scrollBehavior

- Тип: `Function`


Параметр `scrollBehavior` позволяет определить позицию прокрутки между маршрутами. Этот метод вызывается каждый раз, когда страница загружается.

По-умолчанию свойство  scrollBehavior выглядит так:

```js
const scrollBehavior = function (to, from, savedPosition) {
  // Если возвращенная позиция отрицательна или пустой объект,
  // сохранит текущую позицию
  let position = false

  // Если дочерние элементы не найдены
  if (to.matched.length < 2) {
    // Проскроллить до верха страницы
    position = { x: 0, y: 0 }
  } else if (to.matched.some((r) => r.components.default.options.scrollToTop)) {
    // Если у одного из детей scrollTop: true
    position = { x: 0, y: 0 }
  }

  // savedPosition доступен только для браузерной навигации (Кнопки вперед и назад)
  if (savedPosition) {
    position = savedPosition
  }

  return new Promise(resolve => {
    // Дождаться окончания эффекта перехода (если требуется(
    window.$nuxt.$once('triggerScroll', () => {
      // Если нет селектора, будут использовать координаты
      // Или если селектор не возвращает ни одного элемента
      if (to.hash && document.querySelector(to.hash)) {
        // Прокрутка до якоря
        position = { selector: to.hash }
      }
      resolve(position)
    })
  })
}
```


Пример форсированной прокрутки к верху страницы для каждого пути: 
`nuxt.config.js`
```js
module.exports = {
  router: {
    scrollBehavior: function (to, from, savedPosition) {
      return { x: 0, y: 0 }
    }
  }
}
```

> Это свойство предоставлятеся из vue-router [Router constructor](https://router.vuejs.org/en/api/options.html).

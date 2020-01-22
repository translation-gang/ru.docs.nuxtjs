---
title: "API: Свойство router"
description: Свойство router позволяет вам кастомизировать nuxt.js роутер.
---

# Свойство router

> Свойство router позволяет вам кастомизировать nuxt.js роутер  ([vue-router](https://router.vuejs.org/en/)).

## base

- Тип: `String`
- По умолчанию: `'/'`

Базовый URL приложения. Например, если одностраничное приложение доступно через путь `/app/`, тогда основной базовый URL должет иметь вид `'/app/'`.

Пример (`nuxt.config.js`):
```js
module.exports = {
  router: {
    base: '/app/'
  }
}
```

<p class="Alert Alert-blue">Когда `base` указано, nuxt.js добавит на страницу так же и заголовок: `<base href="{{ router.base }}"/>`.</p>

> Эта опция передаётся напрямую во vue-router [Router конструктор](https://router.vuejs.org/en/api/options.html).

## extendRoutes

- Тип: `Function`

Вам так же может потребоваться расширить возможности путей ('routes') созданных самим nuxt.js. Вы сможете сделать это через свойство `extendRoutes`.

Пример того как добавить кастомный путь:

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

Схема пути должна удовлетворять требованиям [vue-router](https://router.vuejs.org/en/) схемы.

## linkActiveClass

- Тип: `String`
- По умолчанию: `'nuxt-link-active'`

Глобально установленный по умолчанию [`<nuxt-link>`](/api/components-nuxt-link) активный класс.

Пример (`nuxt.config.js`):
```js
module.exports = {
  router: {
    linkActiveClass: 'active-link'
  }
}
```

> Эта опция передаётся напрямую во [vue-router Router конструктор](https://router.vuejs.org/en/api/options.html).

## linkExactActiveClass

- Тип: `String`
- По умолчанию: `'nuxt-link-exact-active'`

Глобально установленный по умолчанию [`<nuxt-link>`](/api/components-nuxt-link) 'точный' активный класс.

Пример (`nuxt.config.js`):
```js
module.exports = {
  router: {
    linkExactActiveClass: 'exact-active-link'
  }
}
```

> Эта опция передаётся напрямую во [vue-router Router конструктор](https://router.vuejs.org/en/api/options.html).

## middleware

- Тип: `String` или `Array`
- Элементы: `String`

Устанавливает middleware по умолчанию для каждой из страниц приложения.

Пример:

`nuxt.config.js`
```js
module.exports = {
  router: {
    // Запускает middleware/user-agent.js на каждой странице
    middleware: 'user-agent'
  }
}
```

`middleware/user-agent.js`
```js
export default function (context) {
  // Добавляет свойство userAgent в контекст (доступно в `data` и `fetch` разделах компонента)
  context.userAgent = context.isServer ? context.req.headers['user-agent'] : navigator.userAgent
}
```

Узнать больше о middleware вы можете на странице: [Гайд по middleware](/guide/routing#middleware).

## mode

- Тип: `String`
- По умолчанию: `'history'`

Настроить режим роутера, не рекомендуется менять в режиме SSR (рендеринга на стороне сервера).

Пример (`nuxt.config.js`):
```js
module.exports = {
  router: {
    mode: 'hash'
  }
}
```

> Эта опция передаётся напрямую во vue-router [Конструктор Router](https://router.vuejs.org/en/api/options.html).

## scrollBehavior

- Тип: `Function`

Свойство `scrollBehavior` позволяет вам определять кастомное поведение для положения скролла, при переходе между путями (routes). Этот метод вызывается каждый раз при рендеринге каждой страницы.

По умолчнию, свойство scrollBehavior установлено как:

```js
const scrollBehavior = function (to, from, savedPosition) {
  // Если возвращаемая позиция это пустой или нечитаемый объект,
  // будет сохранять текущую позицию.
  let position = false

  // если дочерних элементов не найдено.
  if (to.matched.length < 2) {
    // Скроллировать наверх страницы
    position = { x: 0, y: 0 }
  } else if (to.matched.some((r) => r.components.default.options.scrollToTop)) {
    // если кто то из дочерних элементов имеет свойство scrollToTop установленное как true
    position = { x: 0, y: 0 }
  }

  // savedPosition доступно только для события popstate навигации (событие изменяющее активную запись истории переходов браузера) (кнопка назад например)
  if (savedPosition) {
    position = savedPosition
  }

  return new Promise(resolve => {
    // ожидает когда анимация выхода завершится (если необходимо)
    window.$nuxt.$once('triggerScroll', () => {
      // будет использовано если не передавалось ни одного селектора,
      // или если по селектору не находится ни одного элемента.
      if (to.hash && document.querySelector(to.hash)) {
        // скролл к якорю возвращая селектор
        position = { selector: to.hash }
      }
      resolve(position)
    })
  })
}
```

Пример принудительной установки позиции скролла на самый верх страницы:

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

> Эта опция передаётся напрямую во vue-router [Router конструктор](https://router.vuejs.org/en/api/options.html).

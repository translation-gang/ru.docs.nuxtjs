---
title: "API: Nuxt(опции)"
description: Вы можете программно использовать Nuxt.js, чтобы использовать его как middleware. Это даёт вам свободу создания своего собственного сервера для рендеринга ваших веб-приложений.
---

# Программное использование Nuxt.js

Возможно, вы захотите использовать свой собственный сервер с вамиши middleware и вашим API. Вот почему вы можете программно использовать Nuxt.js .

Вы можете импортировать Nuxt.js следующим образом:

```js
const { Nuxt, Builder } = require('nuxt')
```

## Nuxt конструктор

Чтобы узнать о возможных опциях для Nuxt.js, см. раздел конфигурации.


```js
// Импорт `Nuxt` и `Builder` модулей
const { Nuxt, Builder } = require('nuxt')

// Импорт Nuxt опций 
const config = require('./nuxt.config.js')

// Создать новый экземпляр Nuxt
const nuxt = new Nuxt(config)

// Включить live сборку и перезагрузить в режим разработки
if (nuxt.options.dev) {
  new Builder(nuxt).build()
}

// Мы можем использовать `nuxt.render(req, res)` или `nuxt.renderRoute(route, context)`
```

Вы можете взглянуть на [nuxt-express](https://github.com/nuxt/express) и [adonuxt](https://github.com/nuxt/adonuxt) стартовые шаблоны для быстрого старта.

### Debug логи

Если вы хотите отображать nuxt.js логи, то вы можете добавить наверх вашего файла следующее выражение: 

```js
process.env.DEBUG = 'nuxt:*'
```

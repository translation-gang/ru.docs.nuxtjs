---
title: PostCSS плагины
description: Как добавить PostCSS плагины?
---

# Добавление PostCSS плагинов

### Рекомендуемый способ

Если в корне вашего проекта находится файл `postcss.config.js`, то удалите или переименуйте его. Затем в файле `nuxt.config.js` пропишите следующее:

```js
export default {
  build: {
    postcss: {
      // В качестве ключа укажите имя плагина, а в качестве значения - аргументы
      // Предварительно установите необходимые плагины через npm или yarn
      plugins: {
        // Отключить нужный плагин можно указав false в качестве значения имени объекта
        'postcss-url': false,
        'postcss-nested': {},
        'postcss-responsive-type': {},
        'postcss-hexrgba': {}
      },
      preset: {
        // Пример изменение настроек postcss-preset-env
        autoprefixer: {
          grid: true
        }
      }
    }
  }
}
```

### Традиционный способ
Используйте `postcss.config.js`, например:

```
const join = require('path').join
const tailwindJS = join(__dirname, 'tailwind.js')

module.exports = {
  plugins: [require('tailwindcss')(tailwindJS), require('autoprefixer')]
}
```

>
> **ВНИМАНИЕ!!!**
>
> Данный способ считается устаревшим и будет исключен в версии Nuxt3
> При использовании данного способа при компиляции в консоль будет выводится соответствующее предупреждение
>

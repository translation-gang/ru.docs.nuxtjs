---
title: "API: Компонент <no-ssr>"
description: Пропускает создание компонента на стороне сервера
---

# Компонент &lt;no-ssr&gt;

> Это компонент используется для намеренного удаления из рендеринга на стороне сервера

**Props**:
- placeholder: `string`
  - То что вы напишите в этом пропсе будет отображаться в момент рендера на стороне сервере вместо обернутого компонента

```html
<template>
  <div>
    <ssrfrendly-component />
    <no-ssr>
      <not-ssrfrendly />
    </no-ssr>
  </div>
</template>
```

Этот компонент является клоном [egoist/vue-no-ssr](https://github.com/egoist/vue-no-ssr). Выражаем благодарность [@egoist](https://github.com/egoist)!

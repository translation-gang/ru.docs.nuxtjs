---
title: Публикация через сервис Now
description: Как развернуть Nuxt.js приложение через Now.sh?
---

# Развертывание с Now.sh

Для публикации с помощью [now.sh](https://zeit.co/now) в `package.json` рекомендуется следующее:

```json
{
  "name": "my-app",
  "dependencies": {
    "nuxt": "latest"
  },
  "scripts": {
    "dev": "nuxt",
    "build": "nuxt build",
    "start": "nuxt start"
  }
}
```

Затем запустите команду `now` и наслаждайтесь!

Заметка: мы рекомендуем добавить директорию `.nuxt` в `.npmignore` или `.gitignore`.

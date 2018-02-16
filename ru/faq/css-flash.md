---
title: CSS Flash
description: Почему появляется CSS Flash?
---

# Почему появляется CSS Flash?

![cssflash](/flash_css.gif)

Это происходит потому, что в **режиме разработки** CSS находится в javascript сборке для возможности горячей перезагрузки с помощью Webpack. Эта "вспышка" называется [FOUC](https://en.wikipedia.org/wiki/Flash_of_unstyled_content).

Не переживайте, в **production режиме** CSS разделяется и помещается в заголовок страницы, поэтому эта "вспышка" контента без стилей больше не появится.

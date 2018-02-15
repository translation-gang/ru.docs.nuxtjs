---
title: CSS Flash
description: Почему появляется CSS Flash?
---

# Почему появляется CSS Flash?

![cssflash](/flash_css.gif)

Это происходит потому, что CSS находится в javascript сборке в **режиме разработки**, чтобы Webpack мог производить "горячую перезагрузку". Эта "вспышка" называется [FOUC](https://en.wikipedia.org/wiki/Flash_of_unstyled_content).

Не переживайте, в **production режиме**, CSS разделяется и помещается в заголовок, поэтому эта "вспышка" контента без стилей больше не появляется.

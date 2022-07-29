#border-box
===========

`border-box` говорит браузеру учитывать любые границы и внутренние отступы в значениях, которые вы указываете в ширине и высоте элемента. 
Если вы выставите элементу ширину 100 пикселей, то эти 100 пикселей будут включать в себя границы и внутренние отступы, 
а контент сожмётся, чтобы выделить для них место. Обычно это упрощает работу с размерами элементов.

Выставление box-sizing: border-box полезно для размещения элементов. 
Оно сильно упрощает работу с размерами элементов, и как правило устраняет ряд подводных камней, на которые вы можете наткнуться, размещая контент.

```
*,
*::before,
*::after {
  box-sizing: border-box;
}

html {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
```

#object-fit
===========
Свойство `object-fit` определяет, как содержимое заменяемого элемента, такого как `<img>` или `<video>`, 
должно заполнять контейнер относительно его высоты и ширины.

```
img {
  max-width: 100%;

  object-fit: cover;
  object-position: center;
}
```

#list-reset
===========
Даннаягруппа свойств сбрасывает стили по умолчанию у списков
```
.list-reset {
  margin: 0;
  padding: 0;

  list-style: none;
}
```

#visyally-hidden
================
Скрывает элементы, но они доступны для скрин ридеров. 
(Не путать с `display: none;` - это свойство, как бы удаляет элемент со страницы и не скрин ридеры ни tab с клавиатуры до него не смогут добраться)
```
.visually-hidden {
  position: absolute;

  width: 1px;
  height: 1px;
  margin: -1px;
  padding: 0;
  overflow: hidden;

  white-space: nowrap;

  border: 0;

  clip: rect(0 0 0 0);
  -webkit-clip-path: inset(100%);
          clip-path: inset(100%);
}
```
Если в проекте используется autoprefix, то свойство `-webkit-clip-path: inset(100%);` лучше удалить, autoprefix сам его проставит при сборке проекта

#Подключение шрифтов
====================

В css. `font-family: "Rouble";` в каждом подключении одно, а `font-weight` разное.
```
@font-face {
  font-style: normal;
  font-weight: 400;
  font-family: "Rouble";

  font-display: swap;
  src:
    url("../fonts/rouble.woff2") format("woff2"),
    url("../fonts/rouble.woff") format("woff");
}

@font-face {
  font-style: normal;
  font-weight: 700;
  font-family: "Rouble";

  font-display: swap;
  src:
    url("../fonts/rouble-bold.woff2") format("woff2"),
    url("../fonts/rouble-bold.woff") format("woff");
}
```

В html

```
<link rel="preload" href="fonts/rouble.woff2" as="font" crossorigin>
```

#Подключаем favicon
===================
```
  <link rel="icon" href="favicon.ico">
  <link rel="icon" type="image/png" href="images/favicon.png">
```

#@media для отключения ховеров на тач устройствах
=================================================
❗ обязательно используйте @media для отключения ховеров на тач устройствах, но не используем для текстовых полей ( input, textarea )
```
@media (hover: hover), screen and (min-width: 0\0) {
  &:hover,
  &:focus {
    color: $color-default-white;
  }
}
```

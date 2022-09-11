#border-box
===========

`border-box` говорит браузеру учитывать любые границы и внутренние отступы в значениях, которые вы указываете в ширине и высоте элемента. 
Если вы выставите элементу ширину 100 пикселей, то эти 100 пикселей будут включать в себя границы и внутренние отступы, 
а контент сожмётся, чтобы выделить для них место.

Выставление box-sizing: border-box полезно для размещения элементов. 
Оно сильно упрощает работу с размерами элементов, и как правило устраняет ряд подводных камней, на которые вы можете наткнуться, размещая контент.

```
*,
*::before,
*::after {
  box-sizing: border-box;
}

html,
body {
  margin: 0;
  padding: 0;
  min-height: 100vh;
}

html {
  font-style: normal;
  font-weight: 400;
  font-size: 16px;
  line-height: 24px;
  font-family: "Placeholder", "Arial", sans-serif;
  color: #000000;

  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  // оптимизация выравнивания шрифта относительно центра строки
  text-rendering: optimizeLegibility;
  // если по прежнему есть проблемы с выравниванием
  // https://transfonter.org/ - включите настройку https://prnt.sc/12rnt6g и переконвертируйте шрифт
}

body {
  width: 100%;
  height: 100%;

  background-color: #ffffff;
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

#mixin для подключения шрифтов
=================
```
@mixin font($font_name, $file_name, $weight, $style) {
  font-style: #{$style};
  font-weight: #{$weight};
  font-family: $font_name;

  font-display: swap;
  src: url("../fonts/#{$file_name}.woff2") format("woff2"),
    url("../fonts/#{$file_name}.woff") format("woff");
}
```

// В файле fonts.scss
```
@font-face {
  @include font("Montserrat", Montserrat-Regular, 400, normal);
}
```

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
#mixin для ретины
=================
```
@mixin retina {
  @media (min-resolution: $retina-dpi), (min-resolution: $retina-dppx) {
    @content;
  }
}
```

#transition
===========
```
для любых transition обязательно указывайте transition-property
transition: $trans-default ❌ ---> transition: color $trans-default ✅
```

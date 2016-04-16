# Social Buttons

Готовое решение для добавления кнопок социальных сетей на сайт.

[![](http://m-ulyanov.github.io/social-buttons/social-buttons-promo.png)](https://github.com/M-Ulyanov/SocialButtons)

## Быстрый старт
- Подключить SocialButtons.css и SocialButtons.js или их минифицированные версии
- Создать экземпляр кнопок с помощью вызова new SocialButtons, передав нужные параметры
- При необходимости подключить es6-promise.js
- Никакие дополнительные библиотеки (например jQuery) для работы не требуются
- Установить можно так же из NPM:<br>
`npm install social-buttons`

## Какие сервисы поддерживаются?
На данный момент это - Вконтакте, Facebook, Google+, Одноклассники, Twitter, Мой Мир, Livejournal, Linkedin<br>
Функциональные названия:<br>
`['facebook', 'vkontakte', 'odnoklassniki', 'googleplus', 'twitter', 'moimir', 'lj', 'linkedin']`

## Параметры
`services` - Массив сервисов, кнопки которых должны быть сгенерированы в текущем виджете<br>
`components` - Какие элементы кнопки должны быть отрисованы. <br>
Доступные значения: `icon`, `text`, `count` (положение элементов в массиве не имеет значения)<br>
`counter` - Отображать ли счетчики публикаций. По умолчанию `false`<br>
`outputCountCallback` - Функция для изменения отображения счетчика, ожидается, что будет возращен результат модификации.<br>
 В единственном параметре можно получить текущий счетчик.
`theme` - Варианты отображения кнопок. Изначально доступно несколько тем: `default`, `color`<br>
Вы так же можете создать свою тему, добавив соответствующие стили, сами кнопки получат постфикс вида - `b-social-button--yourtheme`<br>
`showZeros` - Показывать ли счетчики, если они равны нулю. По умолчанию - `false`<br>
`buttonSize` - Размер кнопок: `small`, `middle`, `large` или любое другое значение, которое может быть преобразовано в число<br>
`id` - Уникальный идентификатор DOM элемента, к которому будет привязан и отрисован виджет кнопок<br>
`url` - URL расшариваемой публикации, параметр имеет наивысшей приоритет, если он не указан значение берется из meta тега `property="og:url`, по умолчанию текущий `url`<br>
`title` - Заголовок расшариваемой публикации, параметр имеет наивысше йприоритет, если он не указан значение берется из meta тега `property="og:url`, по умолчанию `title` текущей страницы<br>
`description` - Описание расшариваемой публикации, параметр имеет наивысшей приоритет, если он не указан значение берется из meta тега `property="og:description`<br>
`image` - Изображение расшариваемой публикации, параметр имеет наивысшей приоритет, если он не указан значение берется из meta тега `property="property="og:image`<br>
`helpers` - Объект кастомизации кнопок виджета, для каждой социальной сети содержит дочерний объект, который доступен по ключу (названию сервиса), например "vkontakte", который в свою очередь имеет следующее поля:<br>
  - `text` - Текст кнопки
  - `title` - Тег `title` для кнопки
  - `customClass` - Дополнительный класс для кастомизации<br>

`callbacks` - Объект с функциями, которые будут вызваны при наступлении определенных событий, по-умолчанию все функции объекта `callbacks` равны - `NULL`.
  - `create` - виджет успешно создан<br>
  - `share` - попытка расшаривания публикации<br>
Так же Для каждой функции при создании в параметре можно получить полезные данные о событии<br>

## Рекомендации
Используйте Open Graph разметку на странице. <br>
Это поможет подхватывать социальным сетям правильные данные при публикации.<br>
`<meta property="og:url" content="share url">`<br>
`<meta property="og:title" content="share title">`<br>
`<meta property="og:description" content="share content">`<br>
`<meta property="og:image" content="share image">`

## Проблемы и решения
#### Скрипт не работает, не отображается ни одна кнопка
Стоит проверить консоль:<br>
Ошибка: `#yourID not found!`<br>
Решение: <br>
- Вызов new SocialButtons необходимо осуществить после загрузки DOM дерева - DOMContentLoaded<br>
- Проверьте наличие элемента c ID - yourID на вашей странице<br>

Ошибка: `Uncaught ReferenceError: Promise is not defined`<br>
Решение: Подключите файл `es6-promise.js`

#### Не отображается счетчик публикаций
Некоторые социальные сети не позволяют получить количество публикаций (шаринга), например у Twitter, такая возможность отсутствует<br>
#### Публикуется неправильный контент

Выполните рекомендации из предыдущего раздела

## Кроссбраузерность
Все современные браузеры.<br>
IE начиная с 9 версии и выше.

## Демонстрация
 <a href="https://m-ulyanov.github.io/social-buttons/">Посмотреть пример</a>

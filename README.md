# 📅 Отзывчивая таблица

**Задача** – сделать таблицу со следующим функционалом:

- **Транспонирование**: при нажатии на кнопку происходит смена строк и столбцов местами
- **Пагинация столбцов**: на экране отображается N столбцов, при переключении страницы показываются следующие N столбцов и т.д.

## Особенности проекта

### Таблица рассчитана на любые входные данные

В качестве тестовых данных был выбран список праздников на каждый день с разбивкой по дням.

Данные подтягиваются из [./src/data/holidays.ts](./src/data/holidays.ts). Вместо него можно использовать любые данные в аналогичном формате (для таблицы `M x N`):

```
{
  <Заголовок строки 1>: {
    <Заголовок столбца 1>: <Текст столбца 1>,
    <Заголовок столбца 2>: <Текст столбца 2>,
    ...,
    <Заголовок столбца N>: <Текст столбца N>,
  },

  ...,

  <Заголовок строки M>: {
    <Заголовок столбца 1>: <Текст столбца 1>,
    <Заголовок столбца 2>: <Текст столбца 2>,
    ...,
    <Заголовок столбца N>: <Текст столбца N>,
  },
}
```

**Важно!** Предполагается, что данные – это выгрузка из существующей таблицы, то есть в каждой строке задано одинаковое количество столбцов с одинаковыми названиями. Если не выполнить это условие, данные могут отображаться некорректно.

### Таблица полностью отзывчива

- При ширине экрана до `768px` таблица отображается полностью с возможностью скроллинга, т.к. переключать по одному столбцу через кнопки было бы совсем не удобно

- При ширине экрана до `1024px` отображается по 3 столбца (плюс первый, с заголовками)

- При ширине экрана до `1200px` отображается по 4 столбца (плюс первый)

- В остальных случаях отображается по 5 столбцов на странице

При желании эти значения можно изменить в [./src/utils/columnsPerPage.ts](./src/utils/columnsPerPage.ts)

### Реализована «прилипающая» шапка с заголовками таблицы

На экранах шириной от `768px` при скроллинге вниз шапка фиксируется в верхней части экрана для более удобной навигации по таблице.

### Учтены возможные нюансы взаимодействия с таблицей

- При изменении доступного количества страниц текущая страница сбрасывается на первую, чтобы не выйти за пределы массива

- При изменении ширины экрана в реальном времени пересчитывается количество страниц, а также «прилипчивость» заголовков таблицы

## Сборка проекта

Перед началом работы необходимо установить зависимости через `npm`:

```
npm i
```

### Сборка проекта в режиме разработки с запуском локального сервера:

```
npm start
```

### Сборка проекта в режиме Production:

```
npm run build
```

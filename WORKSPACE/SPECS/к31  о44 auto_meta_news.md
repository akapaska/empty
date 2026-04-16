# СПЕЦИФИКАЦИЯ: Автогенерация Title/Description для новостей и статей (K31 / O44)

> Статус: ГОТОВО К ВНЕДРЕНИЮ
> Для: Сайфудинов (Руслан)
> Подготовил: Алёна
> Дата: 11.04.2026

## Задача

Настроить автоматическую генерацию Title и Description для ВСЕХ внутренних страниц: новости, пресс-релизы, статьи. Сейчас на этих страницах мета-теги отсутствуют или дублируют заголовок без контекста.

## Формулы генерации

### kirillitsa.ru

**Title:**
```
{Заголовок новости} — ГК «Кириллица»
```

**Description:**
```
{Первые 150 символов превью-текста}
```

**Пример:**
- Title: `Выручка группы за 2024 год составила 24,4 млрд рублей — ГК «Кириллица»`
- Description: `АО «Кириллица» подвела итоги 2024 года. Выручка группы компаний выросла до 24,4 млрд рублей, чистая прибыль составила 450 млн рублей...`

### oilresource.ru

**Title:**
```
{Заголовок новости} — «Оил Ресурс»
```

**Description:**
```
{Первые 150 символов превью-текста}
```

**Пример:**
- Title: `Выручка «Оил Ресурс» по итогам 2025 года выросла в 2 раза — «Оил Ресурс»`
- Description: `ООО «Оил Ресурс» (входит в ГК «Кириллица») по итогам 2025 года продемонстрировало значительный рост финансовых показателей по РСБУ...`

## Реализация в Битрикс

В шаблоне компонента `news.detail` (файл `template.php` или `header.php` раздела):

```php
<?php
// Автогенерация Title
$newsTitle = $arResult['NAME'];
$siteTitle = 'ГК «Кириллица»'; // или '«Оил Ресурс»' для OR
$APPLICATION->SetTitle($newsTitle . ' — ' . $siteTitle);
$APPLICATION->SetPageProperty("title", $newsTitle . ' — ' . $siteTitle);

// Автогенерация Description
$previewText = $arResult['PREVIEW_TEXT'];
$description = mb_substr(strip_tags($previewText), 0, 150);
if (mb_strlen(strip_tags($previewText)) > 150) {
    $description .= '...';
}
$APPLICATION->SetPageProperty("description", $description);

// OG-теги
$currentUrl = 'https://' . $_SERVER['HTTP_HOST'] . $arResult['DETAIL_PAGE_URL'];
$APPLICATION->AddHeadString('<meta property="og:title" content="'.htmlspecialchars($newsTitle . ' — ' . $siteTitle).'"/>');
$APPLICATION->AddHeadString('<meta property="og:description" content="'.htmlspecialchars($description).'"/>');
$APPLICATION->AddHeadString('<meta property="og:url" content="'.$currentUrl.'"/>');
$APPLICATION->AddHeadString('<meta property="og:type" content="article"/>');
?>
```

## Где применить

| Сайт | Раздел | Компонент | Кол-во страниц |
|------|--------|-----------|:--------------:|
| kirillitsa.ru | /press-center/ | news.detail | ~20-30 |
| oilresource.ru | /press-center/ | news.detail | ~50+ |
| oilresource.ru | /press-releases/ | news.detail | ~100+ |

## Проверка

1. Открыть любую новость → Ctrl+U → проверить `<title>` и `<meta name="description">`
2. Проверить 3-5 новостей выборочно
3. Убедиться что Description не обрезается посреди слова (функция `mb_substr` должна обрезать по словам — можно доработать)

## Важно

- Не перетирать вручную заданные Title/Description на ключевых страницах (/, /about/, /investors/ и т.д.)
- Автогенерация только для элементов инфоблоков (новости, пресс-релизы)
- Если у новости нет превью-текста — использовать первые 150 символов детального текста
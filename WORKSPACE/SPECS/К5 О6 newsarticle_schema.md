# СПЕЦИФИКАЦИЯ: Schema.org NewsArticle (K5 / O6)

> Статус: ГОТОВО К ВНЕДРЕНИЮ
> Для: Ширкевич (kirillitsa), Ширкевич + Сайфудинов (oilresource)
> Подготовил: Алёна
> Дата: 02.04.2026

## Задача

Добавить JSON-LD разметку `NewsArticle` на все пресс-релизы и новости обоих сайтов. Цель — попадание в Яндекс.Новости и Rich Snippets.

## Шаблон JSON-LD

Вставить в `<head>` каждой страницы пресс-релиза/новости:

### Для oilresource.ru

```json
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "NewsArticle",
  "headline": "{ЗАГОЛОВОК_НОВОСТИ}",
  "description": "{ПЕРВЫЕ_150_СИМВОЛОВ_ТЕКСТА}",
  "datePublished": "{ДАТА_В_ФОРМАТЕ_ISO}",
  "dateModified": "{ДАТА_ИЗМЕНЕНИЯ_ISO}",
  "author": {
    "@type": "Organization",
    "name": "ООО «Оил Ресурс»",
    "url": "https://oilresource.ru"
  },
  "publisher": {
    "@type": "Organization",
    "name": "ООО «Оил Ресурс»",
    "url": "https://oilresource.ru",
    "logo": {
      "@type": "ImageObject",
      "url": "https://oilresource.ru/local/templates/oil_resource/images/footer-logo.svg"
    }
  },
  "mainEntityOfPage": {
    "@type": "WebPage",
    "@id": "{ПОЛНЫЙ_URL_СТРАНИЦЫ}"
  },
  "image": "{URL_ИЗОБРАЖЕНИЯ_ЕСЛИ_ЕСТЬ}"
}
</script>
```

### Для kirillitsa.ru

```json
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "NewsArticle",
  "headline": "{ЗАГОЛОВОК_НОВОСТИ}",
  "description": "{ПЕРВЫЕ_150_СИМВОЛОВ_ТЕКСТА}",
  "datePublished": "{ДАТА_В_ФОРМАТЕ_ISO}",
  "dateModified": "{ДАТА_ИЗМЕНЕНИЯ_ISO}",
  "author": {
    "@type": "Organization",
    "name": "АО «Кириллица»",
    "url": "https://kirillitsa.ru"
  },
  "publisher": {
    "@type": "Organization",
    "name": "АО «Кириллица»",
    "url": "https://kirillitsa.ru",
    "logo": {
      "@type": "ImageObject",
      "url": "https://kirillitsa.ru/local/templates/kirilitsa/images/logo.svg"
    }
  },
  "mainEntityOfPage": {
    "@type": "WebPage",
    "@id": "{ПОЛНЫЙ_URL_СТРАНИЦЫ}"
  },
  "image": "{URL_ИЗОБРАЖЕНИЯ_ЕСЛИ_ЕСТЬ}"
}
</script>
```

## Подстановка данных

| Переменная | Откуда брать | Пример |
|-----------|-------------|--------|
| `{ЗАГОЛОВОК_НОВОСТИ}` | Тег `<h1>` или `<h3>` карточки | Выручка «Оил Ресурс» по итогам 2025 года выросла в 2 раза |
| `{ПЕРВЫЕ_150_СИМВОЛОВ_ТЕКСТА}` | Первый `<p>` на странице | ООО «Оил Ресурс» (входит в ГК «Кириллица»)... |
| `{ДАТА_В_ФОРМАТЕ_ISO}` | Тег `<time>` или дата публикации | 2026-04-01T00:00:00+03:00 |
| `{ДАТА_ИЗМЕНЕНИЯ_ISO}` | Если нет — то же что datePublished | 2026-04-01T00:00:00+03:00 |
| `{ПОЛНЫЙ_URL_СТРАНИЦЫ}` | Текущий URL | https://oilresource.ru/press-releases/413/ |
| `{URL_ИЗОБРАЖЕНИЯ_ЕСЛИ_ЕСТЬ}` | `<img>` в карточке. Если нет — логотип | https://oilresource.ru/.../footer-logo.svg |

## Реализация в Битрикс

1. Создать шаблон компонента `news.detail` (или аналогичного)
2. В `template.php` добавить JSON-LD блок с подстановкой из `$arResult`:
   - `$arResult['NAME']` → headline
   - `$arResult['PREVIEW_TEXT']` → description (обрезать до 150 символов)
   - `$arResult['ACTIVE_FROM']` → datePublished (конвертировать в ISO 8601)
   - `$arResult['DETAIL_PAGE_URL']` → mainEntityOfPage @id
   - `$arResult['PREVIEW_PICTURE']` → image
3. Шаблон применится автоматически ко всем пресс-релизам (100+ на OR)

## Проверка

1. После внедрения: [Google Rich Results Test](https://search.google.com/test/rich-results)
2. Проверить 3–5 пресс-релизов выборочно
3. В Яндекс.Вебмастер → Турбо-страницы и Новости → проверить появление
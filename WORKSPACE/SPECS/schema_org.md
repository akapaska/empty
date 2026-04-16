# СПЕЦИФИКАЦИЯ: Schema.org Organization

> Статус: ЧЕРНОВИК
> Для: Ширкевич, Сайфудинов
> Подготовил: Алёна

## kirillitsa.ru — JSON-LD

Вставить в `<head>` на главной странице и /about/:

```json
{
  "@context": "https://schema.org",
  "@type": "Organization",
  "name": "ГК «Кириллица»",
  "legalName": "АО «Кириллица»",
  "url": "https://kirillitsa.ru",
  "logo": "https://kirillitsa.ru/logo.png",
  "description": "Независимая группа компаний. Инвестиции в нефтегазовую промышленность, АПК, IT.",
  "foundingDate": "2014",
  "address": {
    "@type": "PostalAddress",
    "addressLocality": "Москва",
    "addressRegion": "Калужская область",
    "addressCountry": "RU"
  },
  "contactPoint": {
    "@type": "ContactPoint",
    "telephone": "+7-XXX-XXX-XX-XX",
    "contactType": "general"
  },
  "sameAs": [
    "TODO: ссылки на соцсети если есть"
  ],
  "numberOfEmployees": {
    "@type": "QuantitativeValue",
    "value": "TODO"
  }
}
```

> ⚠️ TODO: уточнить телефон, путь к логотипу, соцсети, кол-во сотрудников

## oilresource.ru — JSON-LD

Вставить в `<head>` на главной и /about-company/:

```json
{
  "@context": "https://schema.org",
  "@type": "Organization",
  "name": "Оил Ресурс",
  "legalName": "ООО «Оил Ресурс»",
  "url": "https://oilresource.ru",
  "logo": "https://oilresource.ru/logo.png",
  "description": "Трейдинг и логистика нефтепродуктов. 14 НПЗ-партнёров, 520 тыс. тонн поставок.",
  "foundingDate": "2012",
  "parentOrganization": {
    "@type": "Organization",
    "name": "ГК «Кириллица»",
    "url": "https://kirillitsa.ru"
  },
  "address": [
    {
      "@type": "PostalAddress",
      "name": "Головной офис",
      "streetAddress": "ул. Тимура Фрунзе",
      "addressLocality": "Москва",
      "addressCountry": "RU"
    },
    {
      "@type": "PostalAddress",
      "name": "Офис Калуга",
      "addressLocality": "Кондрово",
      "addressRegion": "Калужская область",
      "addressCountry": "RU"
    },
    {
      "@type": "PostalAddress",
      "name": "Офис Башкортостан",
      "addressRegion": "Республика Башкортостан",
      "addressCountry": "RU"
    }
  ],
  "contactPoint": {
    "@type": "ContactPoint",
    "telephone": "8-800-600-29-44",
    "contactType": "customer service",
    "availableLanguage": ["Russian"]
  },
  "sameAs": [
    "https://oilresource.com",
    "https://oilresource.cn"
  ]
}
```

## Инструкция

1. Вставить как `<script type="application/ld+json">` в `<head>`
2. После внедрения — проверить: [Google Rich Results Test](https://search.google.com/test/rich-results)
3. Логотип: должен быть реальный путь к файлу на сервере (PNG/SVG, мин. 112x112px)

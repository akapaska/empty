# Инструкция для разработчика: JSON-LD для ГК «Кириллица»

## Цель
Вставить `Organization` JSON-LD в `<head>` главной страницы и страницы `/about/`.

## Страницы
- обязательно: `/`
- обязательно: `/about/`
- не обязательно: `/about/disclosure/`, `/about/documents/`, `/about/governance/`, `/about/ratings/`
- если выводите на всех `/about/*`, то один и тот же объект без изменений.

## Что нужно заполнить
- `name`: `ГК «Кириллица»`
- `legalName`: `АО «Кириллица»`
- `url`: `https://kirillitsa.ru`
- `logo`: `https://kirillitsa.ru/local/templates/kirilitsa/images/logo.svg`
- `description`: `Независимая группа компаний. Инвестиции в нефтегазовую промышленность, АПК, IT.`
- `foundingDate`: `2014`
- `addressLocality`: `Москва`
- `addressRegion`: `Москва`
- `addressCountry`: `RU`
- `postalCode`: `123112`
- `streetAddress`: `Пресненская наб., 12, Башня Федерация`
- `contactPoint.telephone`: `8-800-600-29-44` (доб. 2528)
- `sameAs`: `https://t.me/kirillitsa`, `https://max.ru/id4004021785_biz`, `https://vk.com/gk_kirillitsa`
- `numberOfEmployees.value`: уточнить у клиента (оставить `TODO` в инструкции можно только до получения данных)

## Формат вставки
```html
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "Organization",
  "name": "ГК «Кириллица»",
  "legalName": "АО «Кириллица»",
  "url": "https://kirillitsa.ru",
  "logo": "https://kirillitsa.ru/local/templates/kirilitsa/images/logo.svg",
  "description": "Независимая группа компаний. Инвестиции в нефтегазовую промышленность, АПК, IT.",
  "foundingDate": "2014",
  "address": {
    "@type": "PostalAddress",
    "addressLocality": "Москва",
    "addressRegion": "Калужская область",
    "postalCode": "123112",
    "streetAddress": "Пресненская наб., 12, Башня Федерация",
    "addressCountry": "RU"
  },
  "contactPoint": {
    "@type": "ContactPoint",
    "telephone": "8-800-600-29-44",
    "contactType": "general"
  },
  "sameAs": [
    "https://t.me/kirillitsa",
    "https://max.ru/id4004021785_biz",
    "https://vk.com/gk_kirillitsa"
  ],
  "numberOfEmployees": {
    "@type": "QuantitativeValue",
    "value": "TODO"
  }
}
</script>
```

## Примечания
- Нельзя оставлять `TODO` в продакшн-коде. Все поля должны быть заполнены реальными значениями.
- Если нет соцсетей, можно убрать `sameAs` или оставить пустой массив.
- `Organization` schema можно выводить глобально в шаблоне `<head>` для всех страниц, но достаточно `/` и `/about/`.
- Если на сайте уже есть другой `Organization` schema, убедиться, что не создаётся конфликт.

## Что уточнить у клиента
- реальный номер телефона
- путь к логотипу на сервере
- ссылки на соцсети
- актуальное количество сотрудников

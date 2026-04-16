# СПЕЦИФИКАЦИЯ: OG-теги (K29 / O32)

> Статус: ГОТОВО К ВНЕДРЕНИЮ
> Для: Сайфудинов (Руслан)
> Подготовил: Алёна
> Дата: 11.04.2026

## Что такое OG-теги

Open Graph теги — мета-теги для корректного отображения превью страницы в соцсетях и мессенджерах (VK, Telegram, WhatsApp и т.д.). Без них превью формируется некорректно или не формируется вообще.

## Какие теги нужны

Для каждой страницы в `<head>` добавить:

```html
<meta property="og:title" content="{TITLE СТРАНИЦЫ}">
<meta property="og:description" content="{DESCRIPTION СТРАНИЦЫ}">
<meta property="og:url" content="{CANONICAL URL СТРАНИЦЫ}">
<meta property="og:image" content="{URL ИЗОБРАЖЕНИЯ}">
<meta property="og:type" content="website">
<meta property="og:site_name" content="{НАЗВАНИЕ САЙТА}">
<meta property="og:locale" content="ru_RU">
```

## Откуда брать данные

- **og:title** = то же что `<title>` страницы (уже внедрён)
- **og:description** = то же что `<meta name="description">` (уже внедрён)
- **og:url** = canonical URL страницы (уже внедрён)
- **og:image** = логотип компании (пока нет уникальных превью для страниц)
- **og:site_name** = название сайта (см. ниже)

## kirillitsa.ru

| Страница | og:title | og:description | og:url | og:image |
|----------|---------|---------------|--------|---------|
| / | ГК Кириллица — инвестиции в нефтегаз, АПК и IT — Облигации | ГК «Кириллица»: нефтегазовый холдинг, АПК, IT. Выручка 24,4 млрд ₽. Облигации на Мосбирже. Рейтинг BB\|\|ru. → Узнать больше | https://kirillitsa.ru/ | https://kirillitsa.ru/local/templates/kirilitsa/images/logo.svg |
| /about/ | О компании — ГК Кириллица — Нефтегазовый инвестиционный холдинг | АО «Кириллица» — независимый инвестиционный холдинг. Нефтегаз, АПК, IT. Работаем с 2014 года. Чистая прибыль 450 млн ₽. | https://kirillitsa.ru/about/ | https://kirillitsa.ru/local/templates/kirilitsa/images/logo.svg |
| /investors/ | Инвесторам — Облигации ГК Кириллица — Доходность и рейтинги | Облигации АО «Кириллица» на Мосбирже. Кредитный рейтинг BB\|\|ru. EBITDA, выручка, финансовая отчётность. Купить облигации → | https://kirillitsa.ru/investors/ | https://kirillitsa.ru/local/templates/kirilitsa/images/logo.svg |
| /branch/petroleum/ | Нефтегазовая отрасль — ГК Кириллица — 520 тыс. тонн поставок | Оптовые поставки нефти и нефтепродуктов. 14 НПЗ-партнёров, 520 тыс. тонн/год. Выручка 21,5 млрд ₽. По всей России. | https://kirillitsa.ru/branch/petroleum/ | https://kirillitsa.ru/local/templates/kirilitsa/images/logo.svg |
| /branch/agro/ | Агропромышленный комплекс — ГК Кириллица — Инвестиции в АПК | Инвестиции в сельское хозяйство и агропром. Земельный банк, растениеводство, зерноперевалка. Стратегия развития АПК. | https://kirillitsa.ru/branch/agro/ | https://kirillitsa.ru/local/templates/kirilitsa/images/logo.svg |
| /branch/it/ | IT-направление — ГК Кириллица — Технологические инвестиции | IT-инвестиции ГК «Кириллица»: патенты, технология МТТ, цифровые продукты. Инновации в нефтегазовой отрасли. | https://kirillitsa.ru/branch/it/ | https://kirillitsa.ru/local/templates/kirilitsa/images/logo.svg |
| /press-center/ | Пресс-центр ГК «Кириллица» — новости и публикации в СМИ | Последние новости ГК «Кириллица»: пресс-релизы, публикации в Forbes, РБК, Коммерсантъ. Облигации, финансы, проекты. | https://kirillitsa.ru/press-center/ | https://kirillitsa.ru/local/templates/kirilitsa/images/logo.svg |
| /contacts/ | Контакты АО Кириллица — Москва — Телефон, адрес, реквизиты | Адрес: Москва. Телефон, email, реквизиты АО «Кириллица». Юридический адрес: Калужская обл. Схема проезда → | https://kirillitsa.ru/contacts/ | https://kirillitsa.ru/local/templates/kirilitsa/images/logo.svg |

**og:site_name** = `Кириллица`
**og:type** = `website` (для всех страниц)
**og:locale** = `ru_RU`

## oilresource.ru

| Страница | og:title | og:description | og:url | og:image |
|----------|---------|---------------|--------|---------|
| / | Оил Ресурс — оптовые поставки нефти и нефтепродуктов — Трейдинг | ООО «Оил Ресурс»: оптовые поставки дизеля, бензина, мазута, СУГ. 14 НПЗ-партнёров, 520 тыс. тонн/год. Рейтинг BBB\|\|ru. → Заявка | https://oilresource.ru/ | https://oilresource.ru/local/templates/oil_resource/images/footer-logo.svg |
| /about-company/ | О компании Оил Ресурс — нефтяная компания с 2012 года | Оил Ресурс — трейдинг нефтепродуктов с 2012 г. Геология, бурение, добыча, переработка, нефтехимия. Выручка +67% г/г. | https://oilresource.ru/about-company/ | https://oilresource.ru/local/templates/oil_resource/images/footer-logo.svg |
| /business-directions/ | Трейдинг нефтепродуктов — Оил Ресурс — Оптовые поставки | Оптовые поставки нефтепродуктов от Оил Ресурс: дизель, бензин, мазут, СУГ, керосин. 14 НПЗ, по всей России. → Заявка | https://oilresource.ru/business-directions/ | https://oilresource.ru/local/templates/oil_resource/images/footer-logo.svg |
| /investors/esg/ | ESG-стратегия — Оил Ресурс — Устойчивое развитие | ESG-стратегия компании Оил Ресурс: экология, социальная ответственность, корпоративное управление. Отчётность. | https://oilresource.ru/investors/esg/ | https://oilresource.ru/local/templates/oil_resource/images/footer-logo.svg |
| /press-center/ | Пресс-центр Оил Ресурс — новости и пресс-релизы | Последние новости Оил Ресурс: пресс-релизы, облигации, рыночные обзоры. 100+ публикаций, СМИ. Подписаться → | https://oilresource.ru/press-center/ | https://oilresource.ru/local/templates/oil_resource/images/footer-logo.svg |
| /contacts/ | Контакты Оил Ресурс — Москва, Калуга, Башкортостан | 3 офиса: Москва (ул. Тимура Фрунзе), Кондрово (Калуга), Башкортостан. Телефон, email, реквизиты. → Написать нам | https://oilresource.ru/contacts/ | https://oilresource.ru/local/templates/oil_resource/images/footer-logo.svg |

**og:site_name** = `Оил Ресурс`
**og:type** = `website`
**og:locale** = `ru_RU`

## Реализация в Битрикс

### Вариант 1 — через шаблон (рекомендуемый)

В `header.php` шаблона сайта добавить автогенерацию:

```php
<?php
$title = $APPLICATION->GetTitle();
$description = $APPLICATION->GetProperty('description');
$currentUrl = 'https://' . $_SERVER['HTTP_HOST'] . $_SERVER['REQUEST_URI'];
$siteName = 'Кириллица'; // или 'Оил Ресурс' для OR
$logo = 'https://kirillitsa.ru/local/templates/kirilitsa/images/logo.svg'; // путь к логотипу

$APPLICATION->AddHeadString('<meta property="og:title" content="'.htmlspecialchars($title).'"/>');
$APPLICATION->AddHeadString('<meta property="og:description" content="'.htmlspecialchars($description).'"/>');
$APPLICATION->AddHeadString('<meta property="og:url" content="'.$currentUrl.'"/>');
$APPLICATION->AddHeadString('<meta property="og:image" content="'.$logo.'"/>');
$APPLICATION->AddHeadString('<meta property="og:type" content="website"/>');
$APPLICATION->AddHeadString('<meta property="og:site_name" content="'.$siteName.'"/>');
$APPLICATION->AddHeadString('<meta property="og:locale" content="ru_RU"/>');
?>
```

### Вариант 2 — вручную на каждой странице

Если шаблон трогать нельзя — прописать через свойства страницы в Битрикс (как мы делали с Title/Description).

## Важно

- **На kirillitsa.ru /about/ уже есть OG-теги** (мы видели в коде `openGraph` компонент). Проверить — не будет ли дубля.
- **og:image** — пока используем логотип. В идеале нужны уникальные превью (1200×630px). Это на потом.
- **Для пресс-релизов** — og:type = `article`, og:image = изображение новости (если есть).

## Проверка

1. [Facebook Sharing Debugger](https://developers.facebook.com/tools/debug/) — проверить превью
2. Или просто вставить ссылку в Telegram — посмотреть как отображается превью
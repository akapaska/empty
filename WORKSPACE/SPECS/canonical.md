# СПЕЦИФИКАЦИЯ: Canonical-теги

> Статус: ЧЕРНОВИК
> Для: Ширкевич, Сайфудинов
> Подготовил: Алёна

## Правило

Каждая страница обоих сайтов должна содержать в `<head>`:

```html
<link rel="canonical" href="https://ДОМЕН/ПУТЬ/" />
```

## Правила формирования canonical URL

1. **Всегда HTTPS** (не http)
2. **Со слешем** в конце: `/about/` а не `/about`
3. **Без параметров**: `/press-center/` а не `/press-center/?page=1`
4. **Без www**: `https://kirillitsa.ru/` а не `https://www.kirillitsa.ru/`
5. **Самоссылающийся**: canonical указывает на саму страницу

## kirillitsa.ru — карта canonical

| Страница | Canonical URL |
|----------|--------------|
| Главная | `https://kirillitsa.ru/` |
| О компании | `https://kirillitsa.ru/about/` |
| Инвесторам | `https://kirillitsa.ru/investors/` |
| Нефтегаз | `https://kirillitsa.ru/branch/petroleum/` |
| АПК | `https://kirillitsa.ru/branch/agro/` |
| IT | `https://kirillitsa.ru/branch/it/` |
| Пресс-центр | `https://kirillitsa.ru/press-center/` |
| Контакты | `https://kirillitsa.ru/contacts/` |
| Каждая новость | `https://kirillitsa.ru/press-center/{slug}/` |

## oilresource.ru — карта canonical

| Страница | Canonical URL |
|----------|--------------|
| Главная | `https://oilresource.ru/` |
| О компании | `https://oilresource.ru/about-company/` |
| Трейдинг | `https://oilresource.ru/business-directions/trading/` |
| Логистика | `https://oilresource.ru/business-directions/logistics/` |
| ESG | `https://oilresource.ru/investors/esg/` |
| Пресс-центр | `https://oilresource.ru/press-center/` |
| Контакты | `https://oilresource.ru/contacts/` |
| Каждая новость | `https://oilresource.ru/press-center/{slug}/` |
| Каждый пресс-релиз | `https://oilresource.ru/press-releases/{slug}/` |

## Важно для oilresource.ru

Сейчас существуют 3 домена: `.ru`, `.com`, `.cn`. Canonical для русской версии **всегда** указывает на `.ru`:

```html
<!-- На oilresource.ru -->
<link rel="canonical" href="https://oilresource.ru/about-company/" />

<!-- На oilresource.com (EN-версия) — отдельный canonical на себя -->
<link rel="canonical" href="https://oilresource.com/about-company/" />
```

hreflang (отдельная спецификация) дополнительно свяжет версии между собой.

## Инструкция

1. Добавить `<link rel="canonical">` в шаблон Битрикс (чтобы генерировалось автоматически)
2. В Битрикс: компонент `bitrix:main.include` или прямая вставка в `header.php`
3. Проверить: каждая страница — один canonical, указывает на себя
4. Проверить инструментом: [Google Search Console → Покрытие]

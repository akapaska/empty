# СПЕЦИФИКАЦИЯ: hreflang (oilresource)

> Статус: ЧЕРНОВИК
> Для: Ширкевич, Сайфудинов
> Подготовил: Алёна
> Только для oilresource (3 домена)

## Задача

Настроить hreflang между тремя доменами oilresource, чтобы устранить каннибализацию:
- `oilresource.ru` — русская версия
- `oilresource.com` — английская версия
- `oilresource.cn` — китайская версия

## Код для каждой страницы

В `<head>` каждой страницы на ВСЕХ трёх доменах:

```html
<link rel="alternate" hreflang="ru" href="https://oilresource.ru/{path}/" />
<link rel="alternate" hreflang="en" href="https://oilresource.com/{path}/" />
<link rel="alternate" hreflang="zh" href="https://oilresource.cn/{path}/" />
<link rel="alternate" hreflang="x-default" href="https://oilresource.ru/{path}/" />
```

## Пример для главной

```html
<link rel="alternate" hreflang="ru" href="https://oilresource.ru/" />
<link rel="alternate" hreflang="en" href="https://oilresource.com/" />
<link rel="alternate" hreflang="zh" href="https://oilresource.cn/" />
<link rel="alternate" hreflang="x-default" href="https://oilresource.ru/" />
```

## Правила

1. `x-default` указывает на `.ru` (основной домен)
2. Теги должны быть **на всех трёх доменах** (взаимные ссылки)
3. Пути должны совпадать: `/about-company/` на .ru = `/about-company/` на .com
4. Если страница не существует на каком-то домене — не включать этот hreflang

## Инструкция

1. Внедрить в шаблон Битрикс (header.php) с автоподстановкой текущего пути
2. Проверить: [hreflang Tag Testing Tool](https://technicalseo.com/tools/hreflang/)
3. Также добавить в XML Sitemap (опционально, но рекомендуется)

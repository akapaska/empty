# СПЕЦИФИКАЦИЯ: robots.txt + Sitemap (K11 / O8, O10, O33, O34)

> Статус: ГОТОВО К ВНЕДРЕНИЮ
> Для: Ширкевич
> Подготовил: Алёна
> Дата: 02.04.2026

---

## oilresource.ru — КРИТИЧЕСКИЕ ИСПРАВЛЕНИЯ

### robots.txt

**Текущая проблема:** Sitemap указан через HTTP вместо HTTPS.

**Что исправить:**

```
# БЫЛО:
Sitemap: http://oilresource.ru/sitemap.xml

# СТАЛО:
Sitemap: https://oilresource.ru/sitemap.xml
```

**Добавить:**

```
Disallow: /auth/
Disallow: /search.php
```

> `/auth/` сейчас не закрыт как отдельный путь (есть только `/*auth=`). Страница авторизации не должна индексироваться.

### Sitemap

**Проблема 1:** Все URL в sitemap используют `http://` вместо `https://`. Нужно перегенерировать.

**Как перегенерировать в Битрикс:**
1. Админка → Настройки → Поисковая оптимизация → Карта сайта
2. Или: Маркетинг → SEO → Карта сайта
3. Перед генерацией убедиться что в настройках домен = `https://oilresource.ru`
4. Нажать «Перегенерировать»

**Проблема 2:** В sitemap присутствуют мусорные URL. Убрать:

| URL | Проблема | Действие |
|-----|---------|---------|
| `/404.php` | Страница ошибки в sitemap | Убрать. Возможно отдаёт 200 вместо 404 — проверить |
| `/auth/` | Страница авторизации | Убрать + закрыть в robots.txt |
| `/search.php` | Страница поиска | Убрать + закрыть в robots.txt |
| `/business-directions/%20sales/` | Битый URL (пробел в пути) | Убрать. Проверить — есть ли /business-directions/sales/ |
| `/press_center/index.php?ID=1` | Технический URL без ЧПУ | Убрать. Настроить ЧПУ для инфоблока |

**Как убрать из sitemap в Битрикс:**
- В настройках генерации sitemap есть список исключений
- Или: добавить эти URL в robots.txt через Disallow, тогда при перегенерации они не попадут

### Итоговый robots.txt для oilresource.ru

```
User-Agent: *
Disallow: */index.php
Disallow: /bitrix/
Disallow: /auth/
Disallow: /search.php
Disallow: /*show_include_exec_time=
Disallow: /*show_page_exec_time=
Disallow: /*show_sql_stat=
Disallow: /*bitrix_include_areas=
Disallow: /*clear_cache=
Disallow: /*clear_cache_session=
Disallow: /*ADD_TO_COMPARE_LIST
Disallow: /*ORDER_BY
Disallow: /*PAGEN
Disallow: /*?print=
Disallow: /*&print=
Disallow: /*print_course=
Disallow: /*?action=
Disallow: /*&action=
Disallow: /*register=
Disallow: /*forgot_password=
Disallow: /*change_password=
Disallow: /*login=
Disallow: /*logout=
Disallow: /*auth=
Disallow: /*backurl=
Disallow: /*back_url=
Disallow: /*BACKURL=
Disallow: /*BACK_URL=
Disallow: /*back_url_admin=
Disallow: /*?utm_source=
Disallow: /*?bxajaxid=
Disallow: /*&bxajaxid=
Disallow: /*?view_result=
Disallow: /*&view_result=

Allow: /bitrix/components/
Allow: /bitrix/cache/
Allow: /bitrix/js/
Allow: /bitrix/templates/
Allow: /bitrix/panel/

Host: oilresource.ru
Sitemap: https://oilresource.ru/sitemap.xml
Clean-param: company&lang&q&s&set_filter&smartFilter_49_2586937876&cache-buster&erid
```

---

## kirillitsa.ru — МЕЛКИЕ ПРАВКИ

**Текущий robots.txt:** В целом ОК. Sitemap уже на HTTPS. ✅

**Проверить:**
- Есть ли `/auth/` как отдельный путь (сейчас только `/*auth=`)
- Если есть страница авторизации — добавить `Disallow: /auth/`

**Sitemap:**
- Проверить что все URL в sitemap используют HTTPS (у Kirillitsa скорее всего ОК)
- Проверить отсутствие мусорных URL

---

## Проверка после внедрения

1. Открыть `https://oilresource.ru/robots.txt` — проверить изменения
2. Открыть `https://oilresource.ru/sitemap.xml` — все URL должны быть HTTPS
3. Проверить что `/404.php`, `/auth/`, `/search.php`, `%20sales/`, `index.php?ID=1` отсутствуют в sitemap
4. В Яндекс.Вебмастер: Индексирование → Файлы Sitemap → отправить на переобход
5. В GSC: Sitemaps → Submit updated sitemap
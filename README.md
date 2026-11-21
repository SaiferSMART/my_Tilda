# 🤖 Tilda Space AI

> Chrome-расширение для автоматической генерации посадочных страниц в Tilda с помощью Gemini AI

![Chrome Extension](https://img.shields.io/badge/Chrome-Extension-4285F4?logo=google-chrome&logoColor=white)
![Gemini AI](https://img.shields.io/badge/Gemini-AI-8E75B2?logo=google&logoColor=white)
![TypeScript](https://img.shields.io/badge/TypeScript-5.x-3178C6?logo=typescript&logoColor=white)

---

## ✨ Что умеет

- **Мастер-агент (Оркестратор)** — получает ваш промпт и составляет план страницы: дизайн-систему (цвета, шрифты, отступы) + список блоков с реальным русскоязычным контентом
- **Параллельная генерация** — каждый блок генерируется отдельным AI-агентом одновременно, ускоряя процесс в разы
- **Авто-вставка в Tilda** — готовый HTML автоматически вставляется прямо в редактор Tilda через T123 (HTML-блок)
- **Выбор модели** — поддержка Gemini 2.0 Flash, 2.5 Pro, 3.1 Pro и других моделей
- **SVG-генератор** — создание анимированных SVG-иконок и декоративных элементов
- **Пресеты** — готовые шаблоны промптов для AI-сервисов, стартапов, кафе, портфолио, фитнеса

---

## 🏗️ Архитектура

```
popup.js          — UI + Оркестратор + Агенты блоков (параллельно)
background.ts     — Service Worker: SVG-генерация, ACE-инъекция, CDP
content.ts        — Взаимодействие с Tilda: поиск редактора, вставка HTML
```

**Флоу генерации:**
1. Пользователь вводит промпт → Оркестратор создаёт JSON-план (дизайн-система + описания блоков с реальным текстом)
2. Все блоки генерируются параллельно через `Promise.all`
3. Пользователь нажимает «Вставить в Tilda» → content script открывает блок T123 и вставляет HTML в Ace Editor

---

## 🚀 Установка

### 1. Сборка расширения

```bash
npm install
npm run build:ext
```

### 2. Загрузка в Chrome

1. Открыть `chrome://extensions/`
2. Включить **Режим разработчика**
3. Нажать **Загрузить распакованное**
4. Выбрать папку `dist-ext/`

### 3. Настройка

1. Открыть расширение (иконка в тулбаре)
2. Вставить API-ключ Gemini ([получить здесь](https://aistudio.google.com/apikey))
3. Выбрать модель
4. Нажать **Сохранить**

---

## 💡 Использование

1. Перейдите в редактор Tilda на свою страницу
2. Откройте расширение
3. Введите описание сайта (или выберите пресет)
4. Нажмите **Запустить агентов**
5. После генерации нажмите **Вставить в Tilda** для каждого блока

---

## 🛠️ Разработка

```bash
npm run dev          # Vite dev server
npm run build:ext    # Сборка Chrome extension → dist-ext/
npm run build        # Сборка web app → dist/
```

---

## 📦 Стек

| Технология | Назначение |
|---|---|
| TypeScript | Background + Content scripts |
| JavaScript | Popup логика |
| Gemini API | Генерация HTML-блоков и SVG |
| Chrome Extensions API | Tabs, Storage, Scripting, Debugger |
| Vite | Сборка проекта |

---

## 📄 Лицензия

MIT © Horosheff

<!-- SAIFER_REPO_PASSPORT_BEGIN: #435 -->
## Паспорт

- **Что это:** > Chrome-расширение для автоматической генерации посадочных страниц в Tilda с помощью Gemini AI.
- **Статус:** не знаю (работает / пауза / заморожено ❄️ / брошено — нет runtime-проверки).
- **Где работает:** не знаю (сервер/ПК/сайт/облако не подтверждены).
- **Как запустить или открыть:** [репозиторий](https://github.com/SaiferSMART/my_Tilda); запуск приложения — не знаю (ищите инструкции в README).
- **Связанные открытые PR:** [актуальный список](https://github.com/SaiferSMART/my_Tilda/pulls?q=is%3Apr+is%3Aopen).
- **Связанные открытые Issue:** [актуальный список](https://github.com/SaiferSMART/my_Tilda/issues?q=is%3Aissue+is%3Aopen).
- **Дата последнего изменения GitHub:** 2026-03-06T23:03:30Z (поле `pushed_at`, любая ветка; не равно проверке эксплуатации).
- **Кто ведёт:** не знаю; владелец репозитория GitHub — `SaiferSMART`.
- **Вопрос к владелице:** подтвердить статус, площадку, точку входа и фактического ведущего.
- **Задание:** [Issue №435](https://github.com/SaiferSMART/saifer-ai-ops/issues/435).
<!-- SAIFER_REPO_PASSPORT_END -->

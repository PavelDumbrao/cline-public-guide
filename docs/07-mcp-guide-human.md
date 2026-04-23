# 07. MCP Guide

> Этот файл отвечает на практический вопрос: **какие внешние инструменты стоит подключать к Cline, а какие пока не трогать**.

Сначала полезно прочитать:
- [`00-start-here.md`](00-start-here.md)
- [`23-system-map-rules-skills-hooks-mcp.md`](23-system-map-rules-skills-hooks-mcp.md)
- [`../ai/rules/05-search-tools.md`](../ai/rules/05-search-tools.md)

---

## Что такое MCP простыми словами

MCP — это способ дать агенту внешние “руки и глаза”.

Без MCP агент работает в основном с:
- локальными файлами;
- локальными командами;
- тем, что уже есть в его контексте.

С MCP он может получать:
- актуальную документацию;
- веб-поиск;
- браузер;
- GitHub;
- доступ к отдельным сервисам и API.

Главная мысль:
**MCP — это не ещё один слой правил, а внешний инструмент.**

---

## Три вопроса перед установкой любого MCP

### 1. Какую конкретную боль он закрывает?
Примеры:
- нужна docs lookup → `context7`
- нужен web search → `tavily`
- нужен браузер → `playwright`
- нужна работа с GitHub repo → `github`

### 2. Не дублирует ли он уже существующий MCP?
Если у тебя уже есть рабочий `tavily`, не надо тащить ещё три search MCP без причины.

### 3. Какой у него уровень доступа?
Одно дело — docs search.
Другое — MCP, который может менять GitHub, деплоить или управлять хостингом.

---

## С чего начать большинству людей

### Базовый MCP-набор
- `context7`
- `tavily`

### Когда сразу добавить `playwright`
Только если тебе реально нужны:
- UI;
- формы;
- браузерные сценарии;
- проверка страницы после изменений.

### Когда сразу добавить `github`
Если ты реально работаешь с:
- репозиториями;
- issues;
- PR;
- code search на GitHub.

---

## Минимальные наборы по ролям

| Роль / задача | Что взять первым |
|---|---|
| **Новичок** | `context7`, `tavily` |
| **Frontend / Fullstack** | `context7`, `tavily`, `playwright`, опционально `github` |
| **Работа с GitHub** | `context7`, `tavily`, `github` |
| **n8n** | `context7`, `tavily`, `n8n-docs`, при необходимости `n8n-mcp` |
| **Большой локальный repo** | `context7`, `tavily`, `cocoindex-code`, опционально `github` |

---

## Частые MCP и когда они нужны

| MCP | Для чего нужен | Уровень доступа | Когда подключать позже |
|---|---|---|---|
| `context7` | Актуальная документация библиотек и SDK | Низкий | Почти всегда стоит подключать рано |
| `tavily` | Web search, extract, research | Средний | Почти всегда полезен рано |
| `playwright` | Браузер, UI, консоль, сеть | Низкий / локальный runtime | Если не работаешь с UI |
| `github` | Repo, issues, PR, code search | Средний / высокий | Если не используешь GitHub |
| `exa` | Альтернативный чистый search / code context | Средний | Если `tavily` уже закрывает задачу |
| `cocoindex-code` | Семантический поиск по локальному коду | Низкий / локальный | Если repo маленький |
| `n8n-docs` | Docs и валидация n8n | Средний | Если не работаешь с n8n |
| `n8n-mcp` | Live-работа с n8n instance | Высокий | Если нет live n8n use-case |
| `hostinger-api` | Хостинг, DNS, домены, VPS | Высокий | Почти всегда не для новичка |

---

## Marketplace first: нормальная стратегия для новичка

У Cline есть MCP Marketplace.

Практическое правило:
если нужен популярный MCP вроде `tavily`, `context7`, `github`, `playwright` —
**сначала смотри Marketplace и официальный setup flow**, а не собирай конфиг из случайных статей.

Полезные ссылки:
- [Cline MCP Marketplace](https://docs.cline.bot/mcp/mcp-marketplace)
- [Adding & Configuring Servers](https://docs.cline.bot/mcp/adding-mcp-servers-from-github)

---

## Когда нужен логин, ключ или чувствительный доступ

Чаще всего доступы нужны для:
- `tavily`
- `exa`
- `github`
- `n8n-mcp`
- `hostinger-api`

Практическое правило:
1. сначала реши, нужен ли MCP вообще;
2. потом открой официальный install flow;
3. только потом заводи API key / логин;
4. сразу после подключения делай маленький smoke test.

Не собирай ключи “на будущее”.

---

## Как безопасно подключать MCP

Подключай по одному.

После каждого MCP делай 4 проверки:
1. запись в конфиг есть;
2. runtime реально читает этот конфиг;
3. MCP виден в интерфейсе / Configured;
4. есть целевой smoke test по назначению MCP.

### Примеры smoke tests
- `context7` → найти docs по библиотеке
- `tavily` → сделать веб-поиск по технической теме
- `playwright` → открыть страницу и проверить консоль
- `github` → прочитать repo / issue / PR
- `n8n-docs` → найти ноду и её обязательные поля

---

## Как не утонуть в MCP-стеке

Не ставь MCP:
- “на всякий случай”;
- потому что он звучит модно;
- потому что у автора их много;
- если не можешь объяснить, какую боль он закрывает.

### Признаки, что MCP-стек уже стал мусорным
- у тебя несколько MCP с одинаковой ролью без понятной причины;
- ты не помнишь, зачем нужен половина стека;
- новые MCP не дают заметной пользы;
- стало сложнее проверять, что реально работает.

---

## Быстрый выбор MCP по типу задачи

| Задача | Что брать первым |
|---|---|
| Документация библиотеки / SDK | `context7` |
| Актуальная информация из веба | `tavily` |
| Чистый search / code context | `exa` |
| UI, формы, браузер | `playwright` |
| GitHub repo / PR / issues | `github` |
| Большой локальный repo | `cocoindex-code` |
| n8n docs / validation | `n8n-docs` |
| Live n8n operations | `n8n-mcp` |

---

## Связка с install-процессом

MCP не надо ставить в отрыве от проверки среды.

Нормальный порядок такой:
1. [`13-install-and-adapt.md`](13-install-and-adapt.md)
2. [`25-cross-platform-installation-paths.md`](25-cross-platform-installation-paths.md)
3. подключение MCP по одному
4. [`27-setup-self-check-and-recovery.md`](27-setup-self-check-and-recovery.md)

Если setup собирает AI-агент, добавь:
- [`26-mega-prompt-for-ai-installer.md`](26-mega-prompt-for-ai-installer.md)

---

## ✅ Чек-лист для самопроверки
- [ ] Я понимаю, что MCP — это внешний инструмент, а не rule и не skill
- [ ] Я начинаю с минимального набора, а не с коллекции интеграций
- [ ] Я могу объяснить пользу каждого подключённого MCP
- [ ] Я подключаю MCP по одному и делаю smoke test
- [ ] Я понимаю, какие MCP требуют чувствительный доступ

---

## Куда идти дальше

- Для карты всей системы — [`23-system-map-rules-skills-hooks-mcp.md`](23-system-map-rules-skills-hooks-mcp.md)
- Для переноса setup — [`13-install-and-adapt.md`](13-install-and-adapt.md)
- Для validation — [`14-validation-checklists.md`](14-validation-checklists.md)
- Для AI install flow — [`26-mega-prompt-for-ai-installer.md`](26-mega-prompt-for-ai-installer.md)

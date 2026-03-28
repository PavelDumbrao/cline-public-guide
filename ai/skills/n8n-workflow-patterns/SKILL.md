---
name: n8n-workflow-patterns
description: Выбор архитектурного паттерна workflow в n8n: webhook, router, validation, branching, scheduled jobs.
---

# n8n Workflow Patterns

## Когда использовать
- Нужно выбрать структуру workflow
- Нужно разложить большой сценарий на понятные узлы

## Базовые паттерны
- Webhook → Normalize → Validate → Process → Respond
- Trigger → Fetch → Transform → Store → Notify
- Router → Branches → Join / finish

## Типичные ошибки
- Слишком много логики в одном node
- Нет нормализации входа
- Нет явного error path

## Как проверить
- По workflow можно глазами понять путь данных
- Ветки логичны
- Есть обработка невалидных входов

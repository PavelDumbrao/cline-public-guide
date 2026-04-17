# 12. n8n Workflow Examples

Сначала полезно прочитать:
- [`00-start-here.md`](00-start-here.md) — если ты только входишь в систему Cline
- [`04-skills-guide-human.md`](04-skills-guide-human.md) — если хочешь понять, как skills помогают в n8n-задачах
- [`15-example-prompts-and-calls.md`](15-example-prompts-and-calls.md) — если хочешь формулировать запросы для Cline по n8n

---

## Важно
Найденные JSON-артефакты — это **не Cline Workflows**.
Это примеры **n8n workflows / промежуточных артефактов**.

## Что попало в публичный набор
В этот репозиторий стоит включать только учебные и очищенные примеры:
- `lead-magnet-workflow-minimal.json`
- `workflow-batch1.json`
- `workflow-batch2-updated.json`
- `workflow-batch3.json`
- `workflow-batch4.json`

## Почему именно они
Потому что они образуют понятную учебную прогрессию:
1. минимальный каркас
2. первые узлы
3. расширение логики
4. сложная ветвящаяся логика
5. почти полный учебный workflow

## Что обязательно чистить перед публикацией
- `credentials`
- bot tokens
- file IDs
- private URLs
- user-specific names

## Как использовать batch progression

### Batch 1
Понять вход событий и базовую маршрутизацию.

### Batch 2
Добавить больше логики и состояний.

### Batch 3
Добавить внешние действия и проверки.

### Batch 4
Собрать почти полный учебный кейс.

## Как проверить, что пример безопасен
1. Нет блока `credentials`
2. Нет секретов
3. Нет приватных endpoint
4. Понятно, что нужно заменить вручную

---

## Куда идти дальше
- Для следующего шага — [`15-example-prompts-and-calls.md`](15-example-prompts-and-calls.md) — если хочешь учиться через запросы к Cline
- Для следующего шага — [`07-mcp-guide-human.md`](07-mcp-guide-human.md) — если хочешь понять полезные MCP для n8n-задач
- Для следующего шага — [`21-learning-path-for-students.md`](21-learning-path-for-students.md) — если хочешь встроить это в общий маршрут обучения

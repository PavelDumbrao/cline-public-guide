# 10. Troubleshooting

Сначала полезно прочитать:
- [`00-start-here.md`](00-start-here.md) — если проблема началась из-за слабой базы
- [`14-validation-checklists.md`](14-validation-checklists.md) — если хочешь проверять setup по чек-листам
- [`20-model-glitches-and-recovery.md`](20-model-glitches-and-recovery.md) — если проблема похожа на drift модели

---

## Типичная проблема 1. Всё смешалось
### Симптом
Ты не понимаешь, что лежит в rules, что в skills, а что в hooks.
### Решение
Сначала разложи по ролям:
- rule = поведение
- skill = экспертиза
- hook = событие + скрипт
- MCP = инструмент

## Типичная проблема 2. Агент делает не то
### Причина
Слабые rules или отсутствующий skill.
### Решение
Уточни инструкцию и проверь, нужен ли специализированный skill.

## Типичная проблема 3. Секреты утекают в repo
### Причина
Скопирован живой конфиг как есть.
### Решение
Прогони полный sanitization review.

## Типичная проблема 4. Слишком много MCP
### Причина
Подключены все подряд.
### Решение
Вернись к минимуму: context7 + tavily + playwright.

## Типичная проблема 5. Путаются Cline Workflows и n8n workflows
### Решение
Запомни:
- Cline Workflow = markdown-процесс
- n8n workflow = JSON для импорта

---

## Куда идти дальше
- Для следующего шага — [`14-validation-checklists.md`](14-validation-checklists.md) — если хочешь проверять себя более системно
- Для следующего шага — [`20-model-glitches-and-recovery.md`](20-model-glitches-and-recovery.md) — если проблема связана с самой моделью
- Для следующего шага — [`15-example-prompts-and-calls.md`](15-example-prompts-and-calls.md) — если хочешь улучшить формулировку запросов к Cline

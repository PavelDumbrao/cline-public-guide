# 21. Learning Path for Students

Если ты запутался в названиях файлов и не понимаешь, что читать первым — сначала открой:
- [`29-beginner-friendly-table-of-contents.md`](29-beginner-friendly-table-of-contents.md) — простое оглавление и маршруты для новичка

---

## Как пользоваться этим маршрутом
Этот документ — **не просто список файлов**, а понятный порядок.

Главное правило:
- не читать всё подряд;
- не пытаться настроить всё за один проход;
- сначала выбрать свой режим.

### Режим A — я человек и хочу понять систему
Иди по человеческому маршруту.

### Режим B — я человек, но хочу, чтобы мой Cline помог собрать setup
Иди по человеческому маршруту + используй отдельный AI sync/install маршрут.

### Режим C — я уже даю repo самому AI-агенту как источник для синка
Сразу смотри:
- [`docs/30-ai-agent-sync-pack.md`](30-ai-agent-sync-pack.md)
- [`ai/README_FOR_CLINE.md`](../ai/README_FOR_CLINE.md)

---

## Шаг 1. Понять сущности
### Что изучить
- [`00-start-here.md`](00-start-here.md)
- [`CONCEPTS.md`](../CONCEPTS.md)
- [`23-system-map-rules-skills-hooks-mcp.md`](23-system-map-rules-skills-hooks-mcp.md)

### Что нужно понять
- что такое rule;
- что такое skill;
- что такое hook;
- что такое MCP;
- что такое workflow.

### Домашка
Объясни своими словами разницу между rule, skill и hook.

### Типичный провал
Ученик сваливает всё в rules или начинает путать hooks с skills.

---

## Шаг 2. Собрать базовый setup без перегруза
### Что сделать
- взять 5–7 rules;
- взять 3–4 skills;
- поставить 2–3 MCP;
- hooks пока не трогать.

### Что открыть
- [`03-rules-guide-human.md`](03-rules-guide-human.md)
- [`04-skills-guide-human.md`](04-skills-guide-human.md)
- [`07-mcp-guide-human.md`](07-mcp-guide-human.md)
- [`13-install-and-adapt.md`](13-install-and-adapt.md)

### Критерий понимания
Ты понимаешь, зачем нужен каждый слой, а не просто копируешь всё подряд.

### Типичный провал
Сразу пытаться поставить весь стек автора.

---

## Шаг 3. Научиться проверять setup
### Что сделать
Прогнать smoke tests на:
- language/style;
- docs search;
- skills;
- MCP.

### Что открыть
- [`14-validation-checklists.md`](14-validation-checklists.md)
- [`15-example-prompts-and-calls.md`](15-example-prompts-and-calls.md)
- [`../examples/prompts/smoke-tests.md`](../examples/prompts/smoke-tests.md)

### Критерий понимания
Ты умеешь доказать, что setup работает, а не просто «кажется, что работает».

### Типичный провал
Ничего не проверять после переноса.

---

## Шаг 4. Только теперь — hooks
### Что сделать
Понять hooks не как «прикольные скрипты», а как отдельный automation/enforcement слой.

### Что открыть
- [`05-hooks-guide-human.md`](05-hooks-guide-human.md)
- [`13-install-and-adapt.md`](13-install-and-adapt.md)
- [`14-validation-checklists.md`](14-validation-checklists.md)

### Что нужно усвоить
- hooks ставятся **после** rules/skills/MCP;
- hook = реакция на событие;
- один hook = одна роль;
- зрелая система использует helper scripts и checkpoint/restore patterns.

### Домашка
Сделай осознанный выбор:
- нужен ли тебе вообще hook-слой сейчас;
- если нужен — начни с `TaskStart`, `PreToolUse`, `PostToolUse`.

### Критерий понимания
Ты можешь объяснить, зачем тебе каждый hook и что он делает.

### Типичный провал
Ставить hooks до того, как понят базовый setup.

---

## Шаг 5. Если setup собирает AI-агент
Это отдельный режим, и его нельзя смешивать с обычным чтением markdown вручную.

### Что открыть
- [`30-ai-agent-sync-pack.md`](30-ai-agent-sync-pack.md)
- [`25-cross-platform-installation-paths.md`](25-cross-platform-installation-paths.md)
- [`26-mega-prompt-for-ai-installer.md`](26-mega-prompt-for-ai-installer.md)
- [`27-setup-self-check-and-recovery.md`](27-setup-self-check-and-recovery.md)
- [`../ai/README_FOR_CLINE.md`](../ai/README_FOR_CLINE.md)

### Что это даёт
Ты можешь дать repo своему Cline, и он будет:
- читать human docs как обучение;
- читать `ai/` как syncable source;
- переносить rules/hooks/skills/MCP по слоям;
- делать visibility check после каждого шага.

### Критерий понимания
Ты понимаешь разницу между:
- «прочитать repo как человек»;
- «дать repo AI-агенту как source of truth для синка».

---

## Шаг 6. Сделать первый мини-проект
### Что сделать
Собери маленький рабочий кейс с rules + skills + MCP.
Если hooks уже нужны — добавь минимальный hook-layer только после smoke tests.

### Домашка
Например:
- мини-репозиторий с README;
- одним своим skill;
- одним workflow;
- одним минимальным hook, если есть понятная причина.

### Критерий понимания
Ты можешь довести маленькую задачу до результата и проверить её.

### Типичный провал
Брать слишком большой проект первым кейсом.

---

## Шаг 7. Научиться делать self-check и review
### Что сделать
После любой задачи отдельно проверять:
- результат;
- риски;
- утечки;
- слабые места;
- был ли drift между тем, что ты хотел, и тем, что реально получилось.

### Что открыть
- [`14-validation-checklists.md`](14-validation-checklists.md)
- [`27-setup-self-check-and-recovery.md`](27-setup-self-check-and-recovery.md)

### Типичный провал
Считать первый ответ агента финальным.

---

## Шаг 8. Научиться строить свои skills и workflows
### Что сделать
Понять, когда тема достойна отдельного skill или workflow.

### Домашка
Сделать:
- один свой skill из повторяющейся задачи;
- один workflow из повторяющейся процедуры.

### Критерий понимания
Ты не просто копируешь шаблон, а адаптируешь систему под себя.

### Типичный провал
Создавать десятки навыков без реальной необходимости.

---

## Шаг 9. Научиться эволюционировать систему без хаоса
### Что сделать
Понять, как система учится на повторяющихся ошибках:
- когда добавлять новый rule;
- когда обновлять skill;
- когда нужен hook;
- когда достаточно project note.

### Домашка
Возьми один повторяющийся баг или паттерн и классифицируй его как:
- Rule
- Skill
- Hook
- Workflow
- note

### Типичный провал
После каждой ошибки плодить новый rule, skill и hook одновременно.

---

## Шаг 10. Научиться вести длинные задачи
### Что сделать
Прочитать:
- [`28-three-level-planning-in-cline.md`](28-three-level-planning-in-cline.md)

Понять 3 слоя:
- глобальный план;
- средний план;
- точечный исполнимый slice.

### Домашка
Возьми одну длинную задачу и оформи её в:
- `implementation_plan.md`
- `cline_docs/project-state.md`
- `task_progress`

### Типичный провал
Писать весь проект в один TODO-список.

---

## Самый короткий маршрут, если не хочешь перегруза
Если тебе нужно совсем коротко, иди так:
1. [`00-start-here.md`](00-start-here.md)
2. [`23-system-map-rules-skills-hooks-mcp.md`](23-system-map-rules-skills-hooks-mcp.md)
3. [`03-rules-guide-human.md`](03-rules-guide-human.md)
4. [`04-skills-guide-human.md`](04-skills-guide-human.md)
5. [`07-mcp-guide-human.md`](07-mcp-guide-human.md)
6. [`05-hooks-guide-human.md`](05-hooks-guide-human.md)
7. [`13-install-and-adapt.md`](13-install-and-adapt.md)
8. [`14-validation-checklists.md`](14-validation-checklists.md)
9. [`30-ai-agent-sync-pack.md`](30-ai-agent-sync-pack.md) — если хочешь подключить AI-агента к установке

---

## Куда идти дальше
- Для практики через реальные запросы — [`15-example-prompts-and-calls.md`](15-example-prompts-and-calls.md)
- Для Zoom-разбора — [`22-zoom-session-summary.md`](22-zoom-session-summary.md)
- Для установки setup через AI-агента — [`30-ai-agent-sync-pack.md`](30-ai-agent-sync-pack.md)
- Для карты всей системы — [`23-system-map-rules-skills-hooks-mcp.md`](23-system-map-rules-skills-hooks-mcp.md)

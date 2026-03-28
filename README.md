# Cline Public Guide

Публичный, обезличенный и новичковый репозиторий по настройке Cline.

Этот репозиторий собран как **шаблон**, а не как копия живой системы автора.
Здесь нет секретов, приватных URL, токенов, IP-адресов и личной инфраструктуры.

## Куда идти дальше

### Я новичок
1. Открой `docs/00-start-here.md`
2. Сразу потом `docs/13-install-and-adapt.md`
3. Потом `docs/01-cline-mental-model.md`
4. Потом `docs/07-mcp-guide-human.md`

### Я уже что-то настраивал
1. Открой `docs/02-official-vs-pavel-setup.md`
2. Потом `docs/03-rules-guide-human.md`
3. Потом `docs/11-best-practices.md`
4. Потом `docs/14-validation-checklists.md`

### Я хочу только перенести rules / skills
- Rules: `ai/rules/`
- Skills: `ai/skills/`
- Хуки: `ai/hooks/`
- Порядок переноса: `docs/13-install-and-adapt.md`

### Я хочу собрать систему с нуля
1. `docs/00-start-here.md`
2. `docs/13-install-and-adapt.md`
3. `docs/07-mcp-guide-human.md`
4. `ai/README_FOR_CLINE.md`
5. `REPORT.md`

### Я хочу использовать GPT + Cline связку
- `docs/09-gpt-cline-collaboration.md`

### Я работаю через n8n / Telegram / Mini Apps
- `docs/12-n8n-workflow-examples.md`
- `ai/skills/n8n-http-request/`
- `ai/skills/n8n-workflow-patterns/`
- `ai/skills/n8n-validation/`
- `ai/skills/telegram-mini-apps-safe/`

---

## Важно: не путай сущности

| Сущность | Что это | Где в репозитории |
|---|---|---|
| Rule | Правило поведения AI | `ai/rules/` |
| Skill | Специализированная инструкция для конкретной задачи | `ai/skills/` |
| Hook | Bash-скрипт, который срабатывает на событиях Cline | `ai/hooks/` |
| Cline Workflow | Markdown-процесс для Cline | `ai/workflows/` |
| n8n Workflow | JSON-файл для импорта в n8n | `examples/n8n/` |

**Cline Workflows и n8n workflows — это разные вещи.**

---

## Структура репозитория

```text
cline-public-guide/
├── README.md
├── REPORT.md
├── docs/
├── ai/
│   ├── README_FOR_CLINE.md
│   ├── rules/
│   ├── skills/
│   ├── hooks/
│   └── workflows/
└── examples/
    ├── n8n/
    ├── prompts/
    └── templates/
```

---

## Что здесь сознательно НЕ включено

- личный `USER.md`
- личный `tech-stack.md`
- приватные incident notes
- реальные Telegram токены
- реальные VPS/IP/domain
- живые credential-блоки из workflow JSON

Если ты хочешь использовать этот репозиторий у себя, **адаптируй всё под свои значения**.

# Cline Public Guide

> Публичный учебный репозиторий по настройке Cline для людей и AI-агентов.

![Cline demo](https://media.githubusercontent.com/media/cline/cline/main/assets/docs/demo.gif)

---

## Что это за repo

Этот репозиторий нужен, чтобы не собирать Cline хаотично.

Он помогает ответить на три практических вопроса:
- **что мне реально нужно для старта**;
- **в каком порядке это ставить**;
- **как проверить, что setup реально работает, а не просто “где-то записан”**.

Здесь собраны:
- human docs — чтобы человек понял систему;
- `ai/` — syncable public layer для AI-агента;
- шаблоны rules / skills / hooks / MCP без секретов и приватной инфраструктуры.

---

## Сначала выбери свой режим

| Режим | Для кого | С чего начать |
|---|---|---|
| **1. Human learning mode** | Хочешь понять Cline как человек | [`docs/29-beginner-friendly-table-of-contents.md`](docs/29-beginner-friendly-table-of-contents.md) |
| **2. AI-assisted install mode** | Хочешь, чтобы твой Cline помог собрать setup | [`docs/26-mega-prompt-for-ai-installer.md`](docs/26-mega-prompt-for-ai-installer.md) |
| **3. AI sync mode** | Даёшь repo агенту как source of truth для переноса setup | [`docs/30-ai-agent-sync-pack.md`](docs/30-ai-agent-sync-pack.md) + [`ai/README_FOR_CLINE.md`](ai/README_FOR_CLINE.md) |

Если сомневаешься — начинай с **Human learning mode**.

---

## Самый безопасный старт для новичка

Открой по порядку всего 4 файла:

1. [`docs/29-beginner-friendly-table-of-contents.md`](docs/29-beginner-friendly-table-of-contents.md) — простая карта repo
2. [`docs/00-start-here.md`](docs/00-start-here.md) — честная точка входа
3. [`docs/21-learning-path-for-students.md`](docs/21-learning-path-for-students.md) — учебный маршрут по фазам
4. [`docs/13-install-and-adapt.md`](docs/13-install-and-adapt.md) — как переносить setup под себя без хаоса

Если ты уже дошёл до переноса setup, не пропусти связку:
- [`docs/25-cross-platform-installation-paths.md`](docs/25-cross-platform-installation-paths.md)
- [`docs/26-mega-prompt-for-ai-installer.md`](docs/26-mega-prompt-for-ai-installer.md)
- [`docs/27-setup-self-check-and-recovery.md`](docs/27-setup-self-check-and-recovery.md)

Это install-protocol слой:
- **куда писать**;
- **как ставить**;
- **как проверять видимость**;
- **как восстанавливаться, если слой записан, но не работает**.

---

## Если setup будет собирать AI-агент

Не проси его просто: **«настрой мне всё»**.

Правильная модель такая:
1. агент сначала делает аудит среды;
2. потом предлагает минимальный setup;
3. потом ставит слоями;
4. после каждого слоя делает read-back и visibility check.

Для этого используй:
- [`docs/26-mega-prompt-for-ai-installer.md`](docs/26-mega-prompt-for-ai-installer.md)
- [`docs/30-ai-agent-sync-pack.md`](docs/30-ai-agent-sync-pack.md)
- [`ai/README_FOR_CLINE.md`](ai/README_FOR_CLINE.md)

---

## В каком порядке собирать систему

Нормальная последовательность почти всегда такая:

1. **Rules** — always-on поведение
2. **Skills** — on-demand экспертиза
3. **MCP** — внешние инструменты
4. **Hooks** — событийная автоматика
5. **Workflows** — повторяемые процедуры

Почему так:
- без rules всё остальное будет использоваться хаотично;
- skills и MCP полезны только когда уже понятны задачи;
- hooks лучше ставить позже, потому что они автоматические и ошибаются больнее;
- workflows имеют смысл, когда у тебя уже есть повторяемый процесс.

---

## Быстрые маршруты по целям

| Что тебе нужно сейчас | Куда идти |
|---|---|
| Я вообще не понимаю, с чего начать | [`docs/29-beginner-friendly-table-of-contents.md`](docs/29-beginner-friendly-table-of-contents.md) |
| Хочу первую понятную точку входа | [`docs/00-start-here.md`](docs/00-start-here.md) |
| Хочу идти как по учебной программе | [`docs/21-learning-path-for-students.md`](docs/21-learning-path-for-students.md) |
| Хочу собрать минимальный setup | [`docs/13-install-and-adapt.md`](docs/13-install-and-adapt.md) |
| Хочу понять всю карту слоёв | [`docs/23-system-map-rules-skills-hooks-mcp.md`](docs/23-system-map-rules-skills-hooks-mcp.md) |
| Хочу понять MCP без перегруза | [`docs/07-mcp-guide-human.md`](docs/07-mcp-guide-human.md) |
| Хочу безопасно подключить AI-установщика | [`docs/26-mega-prompt-for-ai-installer.md`](docs/26-mega-prompt-for-ai-installer.md) |
| Хочу дать repo самому агенту для синка | [`docs/30-ai-agent-sync-pack.md`](docs/30-ai-agent-sync-pack.md) |

---

## Что лежит в repo

```text
cline-public-guide/
├── README.md
├── REPORT.md
├── docs/                   ← обучение для человека
├── ai/
│   ├── README_FOR_CLINE.md ← инструкция для самого агента
│   ├── rules/              ← public rules layer
│   ├── skills/             ← public skills layer
│   ├── hooks/              ← public hook pack
│   ├── workflows/          ← reusable markdown workflows
│   └── mcp/                ← MCP template layer
└── examples/
    ├── n8n/
    ├── prompts/
    └── templates/
```

---

## Что здесь специально НЕ включено

Это шаблон, а не слепок живой приватной системы.

Поэтому здесь нет:
- реальных токенов и ключей;
- личных IP, доменов, chat id;
- приватного `USER.md` автора;
- project-specific инфраструктуры без sanitization;
- planning/handoff файлов из живых задач.

Правильная модель такая:
- **структуру** можно переносить;
- **секреты и project-specific значения** подставляются вручную.

---

## Нормальный следующий шаг после README

Если ты человек:
- иди в [`docs/29-beginner-friendly-table-of-contents.md`](docs/29-beginner-friendly-table-of-contents.md)

Если тебе нужен уже install-flow:
- иди в [`docs/13-install-and-adapt.md`](docs/13-install-and-adapt.md)

Если setup будет собирать агент:
- иди в [`docs/26-mega-prompt-for-ai-installer.md`](docs/26-mega-prompt-for-ai-installer.md)

Если агент будет использовать repo как sync-pack:
- иди в [`docs/30-ai-agent-sync-pack.md`](docs/30-ai-agent-sync-pack.md)

---

## Дополнительно

- Запись и summary Zoom-разбора: [`docs/22-zoom-session-summary.md`](docs/22-zoom-session-summary.md)
- История и цель репозитория: [`REPORT.md`](REPORT.md)
- Контакт автора: **@paveldumbrao**

---

*Идея repo простая: не “поставить всё”, а собрать понятную, проверяемую и устойчивую систему работы с Cline.*

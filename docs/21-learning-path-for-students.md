# 21. Learning Path for Students

Если ты не понимаешь, в каком порядке читать repo, сначала открой:
- [`29-beginner-friendly-table-of-contents.md`](29-beginner-friendly-table-of-contents.md)

Этот документ нужен, чтобы превратить набор файлов в **понятный маршрут по фазам**.

Главная идея:
- не читать всё подряд;
- не пытаться настроить всё за один проход;
- не переходить к следующей фазе, пока предыдущая не стала понятной.

---

## Сначала выбери режим

### Режим A — Human learning mode
Ты сам изучаешь систему как человек.

### Режим B — AI-assisted install mode
Ты хочешь, чтобы твой Cline помог собрать setup, но под твоим контролем.

### Режим C — AI sync mode
Ты даёшь repo агенту как source of truth для синка слоёв.

Для режимов B и C дополнительно нужны:
- [`docs/26-mega-prompt-for-ai-installer.md`](26-mega-prompt-for-ai-installer.md)
- [`docs/30-ai-agent-sync-pack.md`](30-ai-agent-sync-pack.md)
- [`../ai/README_FOR_CLINE.md`](../ai/README_FOR_CLINE.md)

---

## Маршрут по фазам

| Фаза | Что читать | Что должно стать понятно | Что пока рано делать |
|---|---|---|---|
| **Фаза 1. Ориентация** | `00`, `01`, `23` | Что такое Cline и из каких слоёв состоит система | Не ставить hooks и много MCP |
| **Фаза 2. Минимальный setup** | `03`, `04`, `07`, `13` | Как выбрать минимальные rules / skills / MCP | Не копировать весь repo |
| **Фаза 3. Доказательство, что setup работает** | `14`, `15`, `27`, `examples/prompts/smoke-tests.md` | Как отличить “файл записан” от “runtime реально видит слой” | Не усложнять систему поверх неподтверждённого setup |
| **Фаза 4. Расширение и зрелость** | `05`, `06`, `17`, `28`, `30` | Когда нужны hooks, workflows, continuity и AI sync mode | Не автоматизировать сырой процесс |

---

## Фаза 1. Ориентация

### Что читать
- [`00-start-here.md`](00-start-here.md)
- [`01-cline-mental-model.md`](01-cline-mental-model.md)
- [`23-system-map-rules-skills-hooks-mcp.md`](23-system-map-rules-skills-hooks-mcp.md)

### Что надо понять
- Cline — это исполнитель, а не просто чат;
- rules, skills, hooks, MCP и workflows — это разные слои;
- система строится не сразу вся, а по порядку.

### Домашка
Объясни своими словами:
- чем rule отличается от skill;
- чем hook отличается от workflow;
- зачем MCP — это отдельный слой.

### Типичный провал
Человек прочитал пару файлов и сразу полез ставить hooks или 10 MCP.

---

## Фаза 2. Минимальный setup

### Что читать
- [`03-rules-guide-human.md`](03-rules-guide-human.md)
- [`04-skills-guide-human.md`](04-skills-guide-human.md)
- [`07-mcp-guide-human.md`](07-mcp-guide-human.md)
- [`13-install-and-adapt.md`](13-install-and-adapt.md)

### Что надо сделать
- выбрать 5–7 базовых rules;
- выбрать 3–4 нужных skills;
- подключить 2–3 MCP;
- hooks пока не трогать, если их роль не ясна.

### Критерий понимания
Ты можешь объяснить, зачем нужен каждый выбранный слой.

### Типичный провал
Сразу тянуть весь стек автора и потом не понимать, что из этого реально нужно.

---

## Фаза 3. Доказательство и self-check

### Что читать
- [`14-validation-checklists.md`](14-validation-checklists.md)
- [`15-example-prompts-and-calls.md`](15-example-prompts-and-calls.md)
- [`27-setup-self-check-and-recovery.md`](27-setup-self-check-and-recovery.md)
- [`../examples/prompts/smoke-tests.md`](../examples/prompts/smoke-tests.md)

### Что надо понять
- запись файла ≠ рабочий слой;
- после каждого слоя нужен read-back;
- после read-back нужен runtime visibility check.

### Критерий понимания
Ты умеешь доказать, что setup работает, а не просто “выглядит установленным”.

### Типичный провал
Поверить ответу агента «готово» без проверки в UI и без smoke tests.

---

## Фаза 4. Расширение и зрелость

### Что читать
- [`05-hooks-guide-human.md`](05-hooks-guide-human.md)
- [`06-cline-workflows-guide-human.md`](06-cline-workflows-guide-human.md)
- [`17-context-memory-and-compact.md`](17-context-memory-and-compact.md)
- [`28-three-level-planning-in-cline.md`](28-three-level-planning-in-cline.md)
- [`30-ai-agent-sync-pack.md`](30-ai-agent-sync-pack.md)

### Что надо понять
- hooks нужны не сразу, а когда понятен runtime и есть явная automation pain;
- workflow нужен для повторяемой процедуры, а не вместо skill или rule;
- длинные задачи требуют planning + continuity;
- AI sync mode — это отдельный режим, а не просто “дай агенту ссылку на repo”.

### Критерий понимания
Ты расширяешь систему осознанно, а не из желания сделать её “покруче”.

### Типичный провал
Автоматизировать сырой процесс и потом не понимать, почему всё стало менее предсказуемо.

---

## Отдельная ветка: если setup помогает собирать AI-агент

Это не замена основного маршрута, а отдельный operational слой.

### Что читать
- [`25-cross-platform-installation-paths.md`](25-cross-platform-installation-paths.md)
- [`26-mega-prompt-for-ai-installer.md`](26-mega-prompt-for-ai-installer.md)
- [`27-setup-self-check-and-recovery.md`](27-setup-self-check-and-recovery.md)
- [`30-ai-agent-sync-pack.md`](30-ai-agent-sync-pack.md)
- [`../ai/README_FOR_CLINE.md`](../ai/README_FOR_CLINE.md)

### Что надо понять
- agent должен сначала определить ОС, runtime и scope;
- слой ставится маленьким батчем;
- после каждого батча нужен proof: file written / read-back / runtime visibility;
- без visibility check следующий шаг делать нельзя.

---

## Самый короткий маршрут без перегруза

Если хочешь прям очень коротко:
1. [`00-start-here.md`](00-start-here.md)
2. [`23-system-map-rules-skills-hooks-mcp.md`](23-system-map-rules-skills-hooks-mcp.md)
3. [`13-install-and-adapt.md`](13-install-and-adapt.md)
4. [`14-validation-checklists.md`](14-validation-checklists.md)
5. [`../examples/prompts/smoke-tests.md`](../examples/prompts/smoke-tests.md)

Если setup будет собирать AI-агент, добавь:
6. [`26-mega-prompt-for-ai-installer.md`](26-mega-prompt-for-ai-installer.md)
7. [`30-ai-agent-sync-pack.md`](30-ai-agent-sync-pack.md)

---

## Как понять, что можно переходить к следующей фазе

Переходи дальше, только если:
- текущая фаза стала понятной на словах;
- у тебя есть один конкретный proof, что предыдущий слой реально работает;
- ты понимаешь, зачем тебе следующий слой.

Не переходи дальше, если:
- ты просто устал и хочешь “нажать газ”; 
- у тебя уже есть сомнения, видит ли runtime текущий слой;
- хочется добавить hooks до завершения базового smoke suite.

---

## Куда идти дальше

- Для первой точки входа — [`00-start-here.md`](00-start-here.md)
- Для карты системы — [`23-system-map-rules-skills-hooks-mcp.md`](23-system-map-rules-skills-hooks-mcp.md)
- Для переноса setup — [`13-install-and-adapt.md`](13-install-and-adapt.md)
- Для проверки setup — [`14-validation-checklists.md`](14-validation-checklists.md)
- Для AI sync режима — [`30-ai-agent-sync-pack.md`](30-ai-agent-sync-pack.md)

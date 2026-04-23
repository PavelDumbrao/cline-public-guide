# 30. AI Agent Sync Pack

Этот документ нужен для режима, когда repo читает не только человек, но и **AI-агент**, который должен помочь собрать setup.

Если коротко:
- человек читает `docs/` как обучение и operational guidance;
- агент читает `ai/` как syncable public layer;
- перенос идёт по слоям и подтверждается visibility check.

---

## Когда нужен этот режим

Этот режим нужен, если ты хочешь не просто изучать repo, а использовать его как:
- source of truth для переноса setup;
- public mirror layer для rules / skills / hooks / MCP;
- install-pack для своего Cline или другого AI-агента.

Если ты пока сам изучаешь систему как человек — сначала иди сюда:
- [`00-start-here.md`](00-start-here.md)
- [`21-learning-path-for-students.md`](21-learning-path-for-students.md)

---

## Главная ошибка AI sync режима

Плохой сценарий выглядит так:
1. агент читает README;
2. видит много файлов;
3. начинает хаотично копировать всё подряд;
4. объявляет “готово”, хотя runtime visibility не доказана.

Так делать нельзя.

Правильный сценарий такой:
1. агент сначала понимает карту системы;
2. определяет, что пользователю нужно минимально;
3. использует `ai/` как syncable layer;
4. переносит слоями;
5. после каждого слоя делает read-back и visibility proof.

---

## Что в repo использовать как syncable source

### Rules
- `ai/rules/`

### Skills
- `ai/skills/`

### Hooks
- `ai/hooks/`

### MCP template layer
- `ai/mcp/README.md`
- `ai/mcp/mcp-config.template.json`

### Инструкция для самого агента
- `ai/README_FOR_CLINE.md`

Важно:
- это **public mirror**, а не слепок приватной production-системы;
- здесь нет живых секретов;
- здесь есть структура, safe templates и понятный порядок синка.

---

## Что нельзя копировать вслепую

Нельзя переносить буквально:
- токены;
- chat id;
- приватные URL и IP;
- project-specific USER / tech-stack слои;
- placeholders как реальные значения;
- private-only интеграции без своего use-case.

Правильная модель:
- **структура копируется**;
- **секреты и project-specific values подставляются вручную**;
- **лишние слои не переносятся**.

---

## Канонический порядок синка

Почти всегда правильный порядок такой:
1. `ai/rules/`
2. `ai/skills/`
3. `ai/mcp/`
4. `ai/hooks/`
5. smoke / visibility checks

Почему так:
- rules задают policy;
- skills добавляют on-demand глубину;
- MCP дают внешние возможности;
- hooks автоматизируют lifecycle и потому опаснее всего при раннем включении.

---

## Как агент должен работать с этим repo

Если ты AI-агент, твой safe-порядок такой:

### Шаг 1. Прочитай карту и install protocol
Сначала изучи:
- `README.md`
- `docs/23-system-map-rules-skills-hooks-mcp.md`
- `docs/13-install-and-adapt.md`
- `docs/25-cross-platform-installation-paths.md`
- `docs/26-mega-prompt-for-ai-installer.md`
- `docs/27-setup-self-check-and-recovery.md`
- `ai/README_FOR_CLINE.md`

### Шаг 2. Определи минимальный нужный набор
Ответь:
- что пользователю реально нужно сейчас;
- какие слои можно пока не трогать;
- какие project-specific values он должен заменить вручную.

### Шаг 3. Ставь по слоям
Не копируй весь repo механически.
Переноси только релевантные слои и только маленькими батчами.

### Шаг 4. После каждого батча доказывай результат
После каждого слоя отдельно проверь:
- файл записан;
- файл прочитан обратно;
- runtime реально видит слой;
- есть proof через prompt / UI / event / tool call.

---

## Минимальный visibility contract для агента

После каждого слоя агент должен уметь ответить:
- `file_written: yes/no`
- `file_read_back: yes/no`
- `runtime_visibility_confirmed: yes/no`
- `proof_used: ...`
- `unresolved_risks: ...`

Без этого следующий слой ставить нельзя.

---

## Hooks: что уже можно брать как готовую public основу

В `ai/hooks/` лежит public hook pack, близкий к реальной рабочей архитектуре:
- `TaskStart`
- `PreToolUse`
- `PostToolUse`
- `PreCompact`
- `SessionStart`
- `TaskComplete`
- `scripts/project_identity.py`
- `scripts/context_guard.py`

Что это даёт:
- агенту не нужно сочинять hooks с нуля;
- можно брать public-safe архитектуру как основу;
- потом адаптировать env и project-specific значения.

Но даже этот слой нельзя ставить раньше, чем подтверждён базовый rule / skill / MCP runtime.

---

## Для человека: как использовать этот режим правильно

Если хочешь, чтобы твой Cline собрал setup по этому repo, дай ему не абстрактную просьбу, а install-task с ограничениями.

Минимальная связка для старта:
- `README.md`
- `docs/26-mega-prompt-for-ai-installer.md`
- `docs/27-setup-self-check-and-recovery.md`
- `ai/README_FOR_CLINE.md`
- этот файл

---

## Что считать хорошим результатом AI sync режима

Хороший результат — это когда агент:
- не копирует repo хаотично;
- идёт по слоям;
- не ставит hooks слишком рано;
- не хардкодит секреты;
- использует `ai/` как sync-pack слой;
- после каждого слоя делает visibility check;
- не говорит “готово”, пока обязательные слои не подтверждены.

---

## Куда идти дальше

- Для инструкции самому агенту — [`../ai/README_FOR_CLINE.md`](../ai/README_FOR_CLINE.md)
- Для hooks глазами человека — [`05-hooks-guide-human.md`](05-hooks-guide-human.md)
- Для install/adapt — [`13-install-and-adapt.md`](13-install-and-adapt.md)
- Для путей и runtime — [`25-cross-platform-installation-paths.md`](25-cross-platform-installation-paths.md)
- Для install prompt — [`26-mega-prompt-for-ai-installer.md`](26-mega-prompt-for-ai-installer.md)
- Для recovery и visibility — [`27-setup-self-check-and-recovery.md`](27-setup-self-check-and-recovery.md)

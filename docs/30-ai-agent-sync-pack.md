# 30. AI Agent Sync Pack

Этот документ нужен для режима, когда репозиторий читаешь **не только ты**, но и **твой AI-агент**.

Если коротко:
- человек читает human docs;
- агент читает `ai/` как syncable source;
- потом переносит setup по слоям.

---

## Зачем нужен отдельный sync pack
Обычная ошибка такая:
- ученик даёт агенту ссылку на repo;
- агент читает README;
- потом начинает хаотично копировать всё подряд.

Так делать не надо.

Нужен отдельный режим:
1. агент сначала понимает систему;
2. потом видит, какие артефакты можно синкать почти 1-в-1;
3. потом переносит их по порядку;
4. после каждого слоя делает visibility check.

---

## Что в repo можно использовать как syncable source

### Для rules
- `ai/rules/`

### Для skills
- `ai/skills/`

### Для hooks
- `ai/hooks/`

### Для AI-агента как install guide
- `ai/README_FOR_CLINE.md`

### Для MCP
- `ai/mcp/README.md`
- `ai/mcp/mcp-config.template.json`

Важно:
- это **public mirror**;
- здесь нет живых секретов;
- здесь есть структура, safe templates и понятный порядок переноса.

---

## Что нельзя копировать вслепую
Нельзя буквально копировать:
- токены;
- chat id;
- приватные URL;
- IP;
- project-specific USER/TECH_STACK слои;
- любые placeholders как реальные значения.

Правильная модель:
- структура копируется;
- секреты и project-specific значения подставляются вручную.

---

## Канонический порядок синка для AI-агента
1. `ai/rules/`
2. `ai/skills/`
3. `ai/mcp/`
4. `ai/hooks/`
5. smoke / visibility check

Почему именно так:
- rules задают policy;
- skills дают on-demand экспертизу;
- MCP добавляют внешние возможности;
- hooks автоматизируют события и потому опаснее всего для раннего включения.

---

## Hooks: что уже можно копировать почти 1-в-1
В `ai/hooks/` лежит public hook pack, который уже ближе к реальной рабочей архитектуре:
- `TaskStart`
- `PreToolUse`
- `PostToolUse`
- `PreCompact`
- `SessionStart`
- `TaskComplete`
- `scripts/project_identity.py`
- `scripts/context_guard.py`

Что это даёт агенту:
- он может не сочинять hooks с нуля;
- он может копировать готовую public архитектуру;
- потом адаптировать только env и project-specific values.

---

## Как AI-агенту работать с этим repo правильно
Если ты Cline или другой агент, твой порядок такой:

1. Сначала прочитай:
   - `README.md`
   - `docs/23-system-map-rules-skills-hooks-mcp.md`
   - `docs/13-install-and-adapt.md`
   - `docs/25-cross-platform-installation-paths.md`
   - `docs/26-mega-prompt-for-ai-installer.md`
   - `docs/27-setup-self-check-and-recovery.md`
   - `ai/README_FOR_CLINE.md`

2. Потом определи:
   - что пользователю нужно минимально;
   - какие layers реально нужны сейчас;
   - какие project-specific values он должен заменить вручную.

3. Потом устанавливай по слоям.

4. После каждого слоя проверяй:
   - layer реально записан туда, куда надо;
   - Cline действительно его видит;
   - пользователь видит это в интерфейсе;
   - только после этого переходи дальше.

---

## Минимальный visibility check для AI-агента
После каждого слоя агент должен доказать результат.

### Rules
- перечислить, какие rules поставлены;
- попросить пользователя проверить их в интерфейсе.

### Skills
- показать, какие skill-папки созданы;
- убедиться, что у каждой есть `SKILL.md`;
- попросить пользователя проверить Skills UI.

### MCP
- подключать по одному;
- после каждого сервера проверить visibility;
- если нужен reload/reopen — сказать прямо.

### Hooks
- показать, какие hook-файлы перенесены;
- показать, executable ли они;
- прогнать safe smoke test.

---

## Для человека: как использовать этот режим
Если хочешь, чтобы твой Cline собрал setup по этому repo, давай ему не абстрактную просьбу, а чёткий install task.

Минимальная связка для старта:
- `README.md`
- `docs/26-mega-prompt-for-ai-installer.md`
- `ai/README_FOR_CLINE.md`
- этот файл

---

## Что считать хорошим результатом
Хороший результат — это когда агент:
- не копирует хаотично весь repo;
- идёт по слоям;
- ставит hooks не раньше времени;
- не хардкодит секреты;
- использует public hook pack как готовую основу;
- после каждого слоя делает visibility check.

---

## Куда идти дальше
- Для hooks глазами человека — [`05-hooks-guide-human.md`](05-hooks-guide-human.md)
- Для карты всей системы — [`23-system-map-rules-skills-hooks-mcp.md`](23-system-map-rules-skills-hooks-mcp.md)
- Для установки и адаптации — [`13-install-and-adapt.md`](13-install-and-adapt.md)
- Для install paths — [`25-cross-platform-installation-paths.md`](25-cross-platform-installation-paths.md)
- Для AI install prompt — [`26-mega-prompt-for-ai-installer.md`](26-mega-prompt-for-ai-installer.md)
- Для recovery / self-check — [`27-setup-self-check-and-recovery.md`](27-setup-self-check-and-recovery.md)

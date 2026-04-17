# 25. Cross-Platform Installation Paths

Сначала полезно прочитать:
- [`13-install-and-adapt.md`](13-install-and-adapt.md) — если ты уже дошёл до этапа переноса setup
- [`24-rules-mega-guide.md`](24-rules-mega-guide.md) — если до этого проходил rules по порядку
- [`23-system-map-rules-skills-hooks-mcp.md`](23-system-map-rules-skills-hooks-mcp.md) — если хочешь держать в голове всю карту системы

---

> Этот файл нужен, чтобы ученик и AI-установщик **не угадывали пути** для rules, skills, hooks, workflows и MCP, а сначала определяли ОС, тип окружения и только потом записывали файлы.

---

## 1. Главное правило этого документа

Не считай путь правильным только потому, что он часто встречается в статьях, старых заметках или чужом setup.

Правильный подход такой:
1. Определи ОС и runtime.
2. Пойми, нужен **global** или **workspace** scope.
3. Выбери наиболее вероятный путь.
4. Запиши маленький батч файлов.
5. Прочитай их обратно.
6. Проверь, что Cline **реально видит** этот слой, а не просто что файл лежит на диске.

Если уверенность по пути низкая — остановись и уточни.

---

## 2. Что определить до записи файлов

### ОС и среду
Нужно понять, где именно работает Cline:
- macOS
- Windows
- Linux
- WSL
- VS Code local
- VS Code remote / server-side runtime

### Scope
Перед записью всегда решай отдельно:
- **global** — слой должен работать почти везде;
- **workspace** — слой относится только к конкретному проекту.

### Что особенно важно
Частая ошибка — правильно определить тип файла, но перепутать **global vs workspace**.

Например:
- общий language/style rule обычно global;
- project-specific tech stack обычно workspace;
- hooks часто лучше сначала держать global only в понятном наборе;
- workflows чаще безопаснее держать ближе к проекту.

---

## 3. Общий install-порядок по слоям

Практически безопаснее всего такой порядок:
1. Rules
2. Skills
3. MCP settings
4. Hooks
5. Workflows

После каждого слоя:
- read-back файлов;
- smoke test;
- только потом следующий слой.

---

## 4. Path matrix: rules

## macOS

| Тип | Scope | Частый путь | Fallback / альтернатива | Как проверить |
|---|---|---|---|---|
| Rules | global | `~/Documents/Cline/Rules/` | `~/Cline/Rules/` | Агент держит язык/стиль и проходит smoke prompt |
| Rules | workspace | `.clinerules/` | project-specific rules file рядом с проектом, если так устроен твой runtime | Поведение меняется только внутри текущего проекта |

**Как проверить ОС:**
```bash
uname -s
```

**Как проверить user path:**
```bash
whoami
pwd
```

**Симптомы неправильного пути:**
- файлы существуют, но агент ведёт себя как раньше;
- workspace rule не влияет на текущий проект;
- global rule не виден в новой задаче.

**Recovery:**
- не копируй rule во все папки подряд;
- выбери один global path и один workspace path;
- сделай smoke test на language/style;
- если не сработало — проверь runtime path конкретной версии Cline.

---

## Windows

| Тип | Scope | Частый путь | Fallback / альтернатива | Как проверить |
|---|---|---|---|---|
| Rules | global | `C:\Users\<YOU>\Documents\Cline\Rules\` | `C:\Users\<YOU>\Cline\Rules\` | Агент проходит smoke prompt на язык/стиль |
| Rules | workspace | `.clinerules\` | project-local rules path, если setup читает его иначе | Правило влияет только в этом workspace |

**Как проверить ОС:**
```powershell
$env:OS
```

**Как проверить текущего пользователя:**
```powershell
whoami
```

**Симптомы и recovery:** те же, что и на macOS: сначала один путь, потом read-back и smoke, а не массовое копирование по всем возможным директориям.

---

## Linux

| Тип | Scope | Частый путь | Fallback / альтернатива | Как проверить |
|---|---|---|---|---|
| Rules | global | `~/Documents/Cline/Rules/` | `~/Cline/Rules/` | Smoke test на язык, стиль, docs behavior |
| Rules | workspace | `.clinerules/` | project-local path по runtime version | Правило видно только в текущем проекте |

**Как проверить ОС:**
```bash
uname -a
```

**Симптомы неправильного пути:**
- rule лежит на диске, но runtime его не подхватывает;
- agent в новой сессии ведёт себя так, будто файла нет.

**Recovery:**
- перепроверь, local это runtime или server-side;
- отдельно проверь global path и workspace path;
- не считай `Documents/Cline/Rules` автоматически рабочим без smoke на твоём runtime.

---

## WSL

| Тип | Scope | Частый путь | Fallback / альтернатива | Как проверить |
|---|---|---|---|---|
| Rules | global | `/home/<you>/Documents/Cline/Rules/` | `/home/<you>/Cline/Rules/` | Smoke test внутри WSL runtime |
| Rules | workspace | `.clinerules/` в Linux-side workspace | project-local path по WSL runtime | Правило влияет только в текущем Linux-side workspace |

**Критический момент:**
В WSL нельзя автоматически считать, что runtime читает Windows-пути. Сначала проверь, где реально живёт runtime Cline: на Windows-стороне или внутри WSL.

---

## 5. Path matrix: skills

| ОС | Scope | Частый путь | Fallback / альтернатива | Как проверить |
|---|---|---|---|---|
| macOS | global | `~/.agents/skills/` | `~/Documents/Cline/Skills/` если твой setup так устроен | Skill можно явно вызвать |
| macOS | workspace | `.agents/skills/` | project-local skills dir | Агент видит skill только в проекте |
| Windows | global | `C:\Users\<YOU>\.agents\skills\` | `Documents\Cline\Skills\` если так устроен setup | Явный вызов skill работает |
| Windows | workspace | `.agents\skills\` | project-local dir | Skill виден в этом проекте |
| Linux | global | `~/.agents/skills/` | `~/Documents/Cline/Skills/` если runtime так настроен | Skill callable |
| Linux | workspace | `.agents/skills/` | project-local dir | Skill виден только локально |
| WSL | global | `/home/<you>/.agents/skills/` | `/home/<you>/Documents/Cline/Skills/` | Проверка внутри WSL runtime |
| WSL | workspace | `.agents/skills/` | project-local dir | Skill виден в Linux-side workspace |

**Что особенно проверить:**
- каждая папка = один skill;
- внутри есть `SKILL.md`;
- skill реально вызывается, а не просто лежит в папке.

---

## 6. Path matrix: hooks

| ОС | Scope | Частый путь | Fallback / альтернатива | Как проверить |
|---|---|---|---|---|
| macOS | global | `~/Documents/Cline/Hooks/` | `~/Cline/Hooks/` | Hook реально срабатывает на событии |
| macOS | workspace | `.clinerules/hooks/` | project-local hooks dir | Hook срабатывает только в проекте |
| Windows | global | `C:\Users\<YOU>\Documents\Cline\Hooks\` | `C:\Users\<YOU>\Cline\Hooks\` | Event smoke test |
| Windows | workspace | `.clinerules\hooks\` | project-local hooks dir | Hook локально активен |
| Linux | global | `~/Documents/Cline/Hooks/` | `~/Cline/Hooks/` | Hook event test |
| Linux | workspace | `.clinerules/hooks/` | project-local hooks dir | Hook local only |
| WSL | global | `/home/<you>/Documents/Cline/Hooks/` | `/home/<you>/Cline/Hooks/` | WSL-side event test |
| WSL | workspace | `.clinerules/hooks/` | project-local hooks dir | Event test в Linux runtime |

**Что особенно проверить:**
- stdout hook'а = только валидный JSON;
- логирование идёт в stderr, а не в stdout;
- hook быстрый и не ломает happy-path сценарий.

---

## 7. Path matrix: workflows

> Для workflows path чаще плавает сильнее, чем для rules/skills/hooks. Самый безопасный подход — держать их ближе к проекту, если runtime не требует отдельной глобальной директории.

| ОС | Scope | Частый путь | Fallback / альтернатива | Как проверить |
|---|---|---|---|---|
| All | workspace | `.agents/workflows/` | `workflows/` или project-local dir, который ты сам используешь как workflow layer | Агент может опираться на workflow markdown внутри проекта |
| All | global | `~/.agents/workflows/` | `~/Documents/Cline/Workflows/` если setup так устроен | Workflow реально используется как reusable procedure |

**Важно:**
Если твой runtime не имеет специального workflow loader, safest path — project-local reusable markdown workflows.

---

## 8. Path matrix: MCP settings

> Здесь риск ошибки особенно высок, потому что путь зависит не только от ОС, но и от того, где хранит данные само расширение/клиент.

| ОС | Частый путь | Что проверить |
|---|---|---|
| macOS | `~/Library/Application Support/Code/User/globalStorage/saoudrizwan.claude-dev/settings/cline_mcp_settings.json` | Файл реально читается текущим Cline setup |
| Windows | `%APPDATA%\Code\User\globalStorage\saoudrizwan.claude-dev\settings\cline_mcp_settings.json` | MCP entries реально видны и используются |
| Linux | `~/.config/Code/User/globalStorage/saoudrizwan.claude-dev/settings/cline_mcp_settings.json` | MCP поднимается текущим runtime |
| WSL | часто Linux-side VS Code Server storage path, а не Windows path | Отдельно проверь, где живёт runtime extension |

**Как проверять MCP после записи:**
- MCP не просто есть в JSON;
- он реально подключён;
- его можно вызвать по назначению;
- он не дублирует уже существующий MCP.

---

## 9. Общая процедура safe install

### Шаг 1 — detect
Определи:
- ОС;
- local vs remote runtime;
- global vs workspace scope.

### Шаг 2 — install small batch
Положи маленький батч:
- 1–2 rules;
- потом 1 skill;
- потом 1 MCP;
- потом только hooks/workflows.

### Шаг 3 — read-back
Сразу перечитай записанные файлы.

### Шаг 4 — visibility check
Проверь не только наличие файла, но и поведение:
- rule реально влияет;
- skill реально вызывается;
- hook реально срабатывает;
- MCP реально используется.

### Шаг 5 — only then expand
Только после этого расширяй систему.

---

## 10. Симптомы, что слой положен не туда

### Rules
- агент игнорирует style/language rule;
- поведение не меняется между задачами;
- workspace rule не влияет в проекте.

### Skills
- skill folder есть, а вызвать его нельзя;
- агент ведёт себя так, будто skill не существует.

### Hooks
- hook не срабатывает;
- stdout засорён;
- workflow ломается странным образом.

### MCP
- запись в settings есть, а вызова нет;
- MCP числится, но реально не работает;
- непонятно, какой runtime читает этот JSON.

---

## 11. Что делать, если path не сработал

1. Не разбрасывай копии файлов по 5–6 путям сразу.
2. Проверь runtime и scope ещё раз.
3. Откати лишние копии.
4. Снова поставь **один** слой маленьким батчем.
5. Сразу сделай read-back и smoke test.
6. Только потом переходи к следующему candidate path.

---

## 12. Мини-чеклист cross-platform install

- [ ] Я сначала определил ОС и runtime
- [ ] Я отдельно решил global vs workspace scope
- [ ] Я не копировал систему вслепую в несколько путей сразу
- [ ] Я записывал файлы маленькими батчами
- [ ] Я после записи перечитал файлы обратно
- [ ] Я проверил не только наличие файла, но и реальную видимость слоя

---

## 13. Куда идти дальше

- Для мегагайда по rules — [`24-rules-mega-guide.md`](24-rules-mega-guide.md)
- Для install/adapt логики — [`13-install-and-adapt.md`](13-install-and-adapt.md)
- Для промпта AI-установщику — следующий слой: `docs/26-mega-prompt-for-ai-installer.md`
- Для recovery и self-check — следующий слой: `docs/27-setup-self-check-and-recovery.md`

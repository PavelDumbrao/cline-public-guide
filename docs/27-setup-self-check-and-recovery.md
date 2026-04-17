# 27. Setup Self-Check and Recovery

Сначала полезно прочитать:
- [`25-cross-platform-installation-paths.md`](25-cross-platform-installation-paths.md) — если сначала хочешь понять, куда класть файлы
- [`26-mega-prompt-for-ai-installer.md`](26-mega-prompt-for-ai-installer.md) — если хочешь увидеть сам install-промпт для агента
- [`14-validation-checklists.md`](14-validation-checklists.md) — если хочешь дополнительно проверять себя по чек-листам

---

> Этот файл нужен, чтобы ученик и AI-установщик различали две разные вещи:
> **«файл записан»** и **«Cline реально видит и использует этот слой»**.

---

## 1. Зачем нужен отдельный self-check layer

Самая частая ложная победа при настройке Cline выглядит так:
- файл создан;
- структура папок вроде правильная;
- агент уверенно говорит «готово»;
- но rules/skills/hooks/MCP реально не подхватились.

Поэтому проверять нужно не только запись файла, но и **видимость слоя в runtime**.

Этот документ нужен, чтобы:
- сделать явный post-install self-check;
- ловить wrong-path кейсы;
- уметь быстро восстанавливаться, если слой не сработал;
- отличать проблему пути, формата, runtime и самой логики слоя.

---

## 2. Принцип проверки

Порядок всегда такой:
1. Слой записан.
2. Файл прочитан обратно.
3. Проверен правильный path и scope.
4. Прогнан visibility check.
5. Только после этого слой считается реально рабочим.

Если visibility check не пройден — слой не считается установленным, даже если файл существует.

---

## 3. Pre-install checks

Перед установкой нового слоя проверь:
- [ ] Я понимаю ОС и runtime
- [ ] Я понимаю global vs workspace scope
- [ ] Я ставлю слой маленьким батчем
- [ ] Я знаю, как буду проверять именно этот слой
- [ ] Я не смешиваю сразу несколько потенциальных причин ошибки

---

## 4. Post-install checks: rules

### Что проверить после записи rules
- файл реально лежит в ожидаемом path;
- файл прочитан обратно;
- агент показывает ожидаемое always-on поведение;
- нет явного конфликта с другими rules.

### Как понять, что rules реально видны

Проверь на простых сценариях:
- language/style;
- docs-search behavior;
- tool usage discipline;
- базовую честность и предсказуемость ответов.

### Мини-smoke suite для rules

```text
Ответь по-русски и кратко: зачем перед правкой кода сначала изучать текущую систему?
```

```text
Если ты не уверен в API библиотеки, что ты должен сделать первым шагом?
```

```text
Перед правкой существующего файла что ты сделаешь сначала и почему?
```

### Симптомы, что rule не виден
- поведение агента не изменилось вообще;
- agent игнорирует language/style;
- agent продолжает фантазировать там, где должен проверять;
- project-specific rule не влияет внутри workspace.

### Recovery
1. Проверь path.
2. Проверь scope.
3. Перечитай файл обратно.
4. Прогони smoke test снова.
5. Не добавляй новые rules, пока не заработал хотя бы один минимальный rule-layer.

---

## 5. Post-install checks: skills

### Что проверить после записи skills
- каждая skill лежит в отдельной папке;
- внутри есть `SKILL.md`;
- agent может явно использовать skill по задаче;
- skill не дублирует уже существующий.

### Как понять, что skills реально видны

Попроси агент явно использовать skill:
- `systematic-debugging`
- `frontend-design`
- `deployment-guide`
- любой другой установленный skill

### Мини-smoke suite для skills

```text
Используй systematic-debugging и разложи баг по гипотезам.
```

```text
Примени frontend-design: нужен понятный адаптивный экран без перегруза.
```

### Симптомы, что skill не виден
- папка есть, а skill не вызывается;
- агент отвечает общо, как будто skill не существует;
- в структуре skill нет `SKILL.md`;
- перепутан global/workspace path.

### Recovery
1. Проверь папку skill.
2. Проверь наличие `SKILL.md`.
3. Проверь, читает ли runtime этот path.
4. Прогони явный skill prompt.
5. Не тащи 10 skills сразу, пока не подтвердил хотя бы один.

---

## 6. Post-install checks: MCP

### Что проверить после записи MCP settings
- MCP entry реально записан в нужный config;
- config читается текущим runtime;
- MCP реально вызывается;
- MCP даёт тот тип пользы, ради которого подключался.

### Как понять, что MCP реально подключён

Нужно не просто увидеть запись в JSON, а выполнить целевой smoke:
- Context7 → docs lookup;
- Tavily → web search;
- Playwright → browser scenario;
- GitHub → repo interaction;
- любой другой MCP → use-case-specific check.

### Мини-smoke suite для MCP

```text
Найди актуальную документацию по известной библиотеке.
```

```text
Сделай веб-поиск по технической теме.
```

```text
Открой страницу и проверь консоль.
```

### Симптомы, что MCP не подключён
- запись в config есть, а вызова нет;
- MCP указан, но реально не работает;
- agent ведёт себя так, будто MCP не существует;
- непонятно, какой runtime читает JSON.

### Recovery
1. Проверь config path.
2. Проверь runtime extension/storage path.
3. Перечитай config обратно.
4. Прогони один конкретный MCP smoke.
5. Не подключай новые MCP, пока не подтверждён один текущий.

---

## 7. Post-install checks: hooks

### Что проверить после записи hooks
- hook лежит в правильном path;
- stdout возвращает только валидный JSON;
- hook срабатывает на ожидаемом событии;
- hook не ломает happy-path workflow.

### Мини-smoke suite для hooks
- happy-path сценарий;
- блокирующий сценарий;
- no-regression сценарий.

### Примеры
- `git add .env` должен блокироваться;
- обычный маленький `read_file` не должен ломаться;
- логирование должно идти без мусора в stdout.

### Симптомы, что hook сломан
- workflow внезапно ломается;
- stdout загрязнён;
- hook не срабатывает вообще;
- появляются странные ложные блокировки.

### Recovery
1. Отключи подозрительный hook.
2. Проверь stdout/stderr separation.
3. Прогони один минимальный event test.
4. Верни hook только после подтверждённого smoke test.

---

## 8. Post-install checks: workflows

### Что проверить после записи workflow
- workflow реально нужен под повторяемую процедуру;
- он не дублирует rule или hook;
- агент может на него опереться как на reusable process.

### Симптомы, что workflow не работает как надо
- workflow существует, но никто не может объяснить, зачем он нужен;
- он дублирует always-on policy;
- он слишком общий и не даёт повторяемой пользы.

### Recovery
1. Проверь, действительно ли это workflow, а не doc/rule/hook.
2. Сузь зону ответственности.
3. Привяжи workflow к конкретной повторяемой процедуре.

---

## 9. Final smoke suite после базового setup

Если базовый перенос завершён, минимально проверь:
1. Rule по language/style.
2. Rule по docs-search.
3. Один явный skill.
4. Один MCP.
5. Один safe hook, если он подключался.
6. Один browser/read-only сценарий, если есть Playwright.

### Финальная таблица проверки
Перед фразой «готово» полезно свести всё в простую таблицу:

| Слой | Статус | Чем подтверждено |
|---|---|---|
| Rules | pass / fail | prompt + UI |
| Skills | pass / fail | explicit call + UI |
| MCP | pass / fail | tool call + Configured |
| Hooks | pass / fail | event test |
| Workflows | pass / fail | reusable process check |
| USER.md / профиль пользователя | pass / fail | файл + read-back |

Пока хотя бы один обязательный слой без подтверждения — setup не считается завершённым.

### Пример минимального финального набора
- language/style prompt
- docs lookup
- explicit skill call
- MCP call
- browser read-only check

---

## 10. Symptom → likely cause → first recovery step

| Симптом | Вероятная причина | Первый шаг |
|---|---|---|
| Файл есть, но поведение не изменилось | wrong path / wrong scope | перепроверить runtime + scope |
| Skill лежит в папке, но не вызывается | нет `SKILL.md` или wrong path | проверить структуру skill |
| MCP записан, но не работает | wrong config path / runtime storage mismatch | проверить, какой runtime читает config |
| Hook ломает workflow | polluted stdout / overcomplicated hook | отключить hook и проверить JSON output |
| Агент говорит уверенно, но слой не виден | visibility check не был сделан | остановиться и прогнать smoke test |
| Всё стало хуже после нескольких слоёв сразу | изменено слишком много за один батч | откатить до последнего подтверждённого слоя |

---

## 11. Когда делать rollback

Откатывайся, если:
- после добавления одного слоя setup стал менее предсказуемым;
- неясно, какой именно новый компонент всё сломал;
- visibility check не пройден, а изменений уже слишком много;
- новый слой добавил сложность, но не дал подтверждённой пользы.

Правило:
**откатывай последний неподтверждённый слой, а не строй поверх него ещё больше хаоса.**

---

## 12. Мини-чеклист self-check и recovery

- [ ] Я отличаю «файл записан» от «слой реально виден»
- [ ] Я проверяю каждый слой отдельно
- [ ] Я умею назвать симптомы wrong-path кейса
- [ ] Я не расширяю setup поверх неподтверждённого слоя
- [ ] Я знаю, когда нужно сделать rollback

---

## 13. Куда идти дальше

- Для путей и layout — [`25-cross-platform-installation-paths.md`](25-cross-platform-installation-paths.md)
- Для mega-prompt — [`26-mega-prompt-for-ai-installer.md`](26-mega-prompt-for-ai-installer.md)
- Для validation — [`14-validation-checklists.md`](14-validation-checklists.md)
- Для install/adapt логики — [`13-install-and-adapt.md`](13-install-and-adapt.md)

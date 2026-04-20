# 29. Понятное оглавление для новичка

Если ты открыл этот репозиторий и почувствовал:
- «слишком много файлов»;
- «не понимаю, что читать первым»;
- «всё звучит слишком технарски»;
- «где вообще нормальный маршрут для человека?» —

то этот документ как раз для тебя.

Он не про настройку по шагам и не про глубину.
Он про **навигацию**:
- что открыть первым;
- что можно пока пропустить;
- какие уроки связаны между собой;
- как не потеряться и не утонуть в количестве материалов.

---

## Самый короткий ответ: с чего начать

Если вообще не хочешь думать, просто открой эти 4 файла по порядку:

1. [`00-start-here.md`](00-start-here.md) — что такое Cline и почему нельзя копировать setup вслепую
2. [`01-cline-mental-model.md`](01-cline-mental-model.md) — как правильно думать о роли агента
3. [`21-learning-path-for-students.md`](21-learning-path-for-students.md) — учебный маршрут по шагам
4. [`13-install-and-adapt.md`](13-install-and-adapt.md) — как переносить систему под себя без хаоса

Если после этого захочешь понять, как не теряться в больших задачах, добавь:

5. [`28-three-level-planning-in-cline.md`](28-three-level-planning-in-cline.md)

---

## Если тебе нужен не список файлов, а нормальный маршрут

### Маршрут 1. Я вообще впервые слышу про Cline
Иди так:
1. [`00-start-here.md`](00-start-here.md)
2. [`01-cline-mental-model.md`](01-cline-mental-model.md)
3. [`21-learning-path-for-students.md`](21-learning-path-for-students.md)

**Что ты получишь:**
- перестанешь путать Cline с обычным AI-чатом;
- поймёшь, что такое rules, skills, hooks и MCP;
- увидишь понятный путь обучения.

---

### Маршрут 2. Я хочу быстро собрать рабочий минимум
Иди так:
1. [`00-start-here.md`](00-start-here.md)
2. [`13-install-and-adapt.md`](13-install-and-adapt.md)
3. [`07-mcp-guide-human.md`](07-mcp-guide-human.md)
4. [`14-validation-checklists.md`](14-validation-checklists.md)
5. [`../examples/prompts/smoke-tests.md`](../examples/prompts/smoke-tests.md)

**Что ты получишь:**
- минимальный setup без перегруза;
- понимание, что именно реально нужно поставить сначала;
- проверку, что setup не просто записан, а действительно работает.

---

### Маршрут 3. Я хочу учиться по программе, а не хаотично
Иди так:
1. [`21-learning-path-for-students.md`](21-learning-path-for-students.md)
2. потом бери следующий документ по его подсказкам

**Что ты получишь:**
- учебную последовательность;
- домашки и критерии понимания;
- меньше шансов расползтись по всему repo сразу.

---

### Маршрут 4. Я хочу понять, из чего вообще состоит вся система
Иди так:
1. [`23-system-map-rules-skills-hooks-mcp.md`](23-system-map-rules-skills-hooks-mcp.md)
2. [`03-rules-guide-human.md`](03-rules-guide-human.md)
3. [`04-skills-guide-human.md`](04-skills-guide-human.md)
4. [`05-hooks-guide-human.md`](05-hooks-guide-human.md)
5. [`07-mcp-guide-human.md`](07-mcp-guide-human.md)

**Что ты получишь:**
- общую карту слоёв;
- понимание, что работает всегда, а что по запросу;
- меньше путаницы между rules, skills, hooks, workflows и MCP.

---

### Маршрут 5. Я уже что-то настроил, хочу проверить себя
Иди так:
1. [`14-validation-checklists.md`](14-validation-checklists.md)
2. [`../examples/prompts/smoke-tests.md`](../examples/prompts/smoke-tests.md)
3. [`27-setup-self-check-and-recovery.md`](27-setup-self-check-and-recovery.md)
4. [`10-troubleshooting.md`](10-troubleshooting.md)

**Что ты получишь:**
- понимание, что setup реально виден и работает;
- способ проверить visibility и поведение;
- маршрут восстановления, если всё разъехалось.

---

### Маршрут 6. Я хочу научиться вести большие задачи без хаоса
Иди так:
1. [`21-learning-path-for-students.md`](21-learning-path-for-students.md)
2. [`28-three-level-planning-in-cline.md`](28-three-level-planning-in-cline.md)
3. [`17-context-memory-and-compact.md`](17-context-memory-and-compact.md)

**Что ты получишь:**
- понимание, как вести длинные задачи;
- разницу между глобальным планом, текущей фазой и чек-листом;
- связь планирования с контекстом, compaction и continuity.

---

## Как уроки связаны между собой

Ниже — человеческая карта, без «архитектурного тумана».

### Главная логика такая
**README**
→ [`00-start-here.md`](00-start-here.md)
→ [`01-cline-mental-model.md`](01-cline-mental-model.md)
→ [`21-learning-path-for-students.md`](21-learning-path-for-students.md)
→ дальше уже ветвление по цели

---

### Если тебе нужно понять основу
[`00-start-here.md`](00-start-here.md)
→ [`01-cline-mental-model.md`](01-cline-mental-model.md)
→ [`23-system-map-rules-skills-hooks-mcp.md`](23-system-map-rules-skills-hooks-mcp.md)

Смысл:
- сначала понять, что такое Cline;
- потом понять, как он мыслится как агент;
- потом увидеть всю систему целиком.

---

### Если тебе нужно поставить setup
[`00-start-here.md`](00-start-here.md)
→ [`13-install-and-adapt.md`](13-install-and-adapt.md)
→ [`07-mcp-guide-human.md`](07-mcp-guide-human.md)
→ [`14-validation-checklists.md`](14-validation-checklists.md)
→ [`../examples/prompts/smoke-tests.md`](../examples/prompts/smoke-tests.md)

Смысл:
- сначала не копировать вслепую;
- потом перенести минимальный набор;
- потом подключить внешние инструменты;
- потом проверить, что всё реально работает.

---

### Если тебе нужно понять все слои системы
[`23-system-map-rules-skills-hooks-mcp.md`](23-system-map-rules-skills-hooks-mcp.md)
→ [`03-rules-guide-human.md`](03-rules-guide-human.md)
→ [`04-skills-guide-human.md`](04-skills-guide-human.md)
→ [`05-hooks-guide-human.md`](05-hooks-guide-human.md)
→ [`06-cline-workflows-guide-human.md`](06-cline-workflows-guide-human.md)
→ [`07-mcp-guide-human.md`](07-mcp-guide-human.md)

Смысл:
- сначала общая карта;
- потом разбор каждого слоя по отдельности.

---

### Если тебе нужно не потеряться в больших задачах
[`21-learning-path-for-students.md`](21-learning-path-for-students.md)
→ [`28-three-level-planning-in-cline.md`](28-three-level-planning-in-cline.md)
→ [`17-context-memory-and-compact.md`](17-context-memory-and-compact.md)

Смысл:
- learning path даёт общий маршрут;
- урок 28 объясняет 3 уровня плана;
- урок 17 показывает, как это связано с контекстом и восстановлением после паузы.

---

### Если что-то сломалось или стало непонятно
[`14-validation-checklists.md`](14-validation-checklists.md)
→ [`10-troubleshooting.md`](10-troubleshooting.md)
→ [`27-setup-self-check-and-recovery.md`](27-setup-self-check-and-recovery.md)

Смысл:
- сначала проверь симптомы;
- потом разберись с типовыми проблемами;
- потом восстанови setup системно, а не наугад.

---

## Что новичку не надо читать первым

Не потому что это плохие документы.
А потому что без базы они только перегрузят.

Не начинай с этого:
- [`24-rules-mega-guide.md`](24-rules-mega-guide.md) — слишком большой для первого входа
- [`25-cross-platform-installation-paths.md`](25-cross-platform-installation-paths.md) — полезно, но не как первый файл
- [`26-mega-prompt-for-ai-installer.md`](26-mega-prompt-for-ai-installer.md) — мощно, но рано без базового понимания
- [`27-setup-self-check-and-recovery.md`](27-setup-self-check-and-recovery.md) — это уже слой self-check и recovery, а не самый первый вход

### Правило простое
Сначала:
- понять сущности;
- собрать минимальный setup;
- проверить его;

и только потом:
- углубляться в мега-гайды;
- автоматизировать установку;
- усложнять систему.

---

## Если у тебя только один вечер

Вот нормальный порядок на один спокойный проход:

1. [`00-start-here.md`](00-start-here.md)
2. [`01-cline-mental-model.md`](01-cline-mental-model.md)
3. [`21-learning-path-for-students.md`](21-learning-path-for-students.md)
4. [`13-install-and-adapt.md`](13-install-and-adapt.md)
5. [`07-mcp-guide-human.md`](07-mcp-guide-human.md)
6. [`14-validation-checklists.md`](14-validation-checklists.md)
7. [`../examples/prompts/smoke-tests.md`](../examples/prompts/smoke-tests.md)

Если останутся силы и интерес:
8. [`28-three-level-planning-in-cline.md`](28-three-level-planning-in-cline.md)

---

## Если ты уже работаешь с Cline, но всё равно путаешься

Тогда у тебя, скорее всего, проблема не в том, что ты «слабый пользователь», а в одном из двух:

1. у тебя нет ясной карты материалов;
2. ты пытался ставить всё сразу без понятного маршрута.

В этом случае сделай так:
- вернись в [`00-start-here.md`](00-start-here.md);
- открой [`21-learning-path-for-students.md`](21-learning-path-for-students.md);
- выбери **один** маршрут из этого оглавления;
- не переходи к следующему, пока не понял текущий.

---

## Самая простая формула навигации по repo

Если совсем коротко:

- **`00-start-here.md`** — первая точка входа;
- **`21-learning-path-for-students.md`** — маршрут обучения;
- **`13-install-and-adapt.md`** — перенос под себя;
- **`14-validation-checklists.md`** + **`smoke-tests.md`** — проверка, что всё работает;
- **`28-three-level-planning-in-cline.md`** — как вести большие задачи без хаоса.

Если ты запутался — возвращайся сюда.

---

## Куда идти дальше
- Для следующего шага — [`00-start-here.md`](00-start-here.md) — если хочешь начать с самой первой точки входа
- Для следующего шага — [`21-learning-path-for-students.md`](21-learning-path-for-students.md) — если хочешь идти как по учебной программе
- Для следующего шага — [`13-install-and-adapt.md`](13-install-and-adapt.md) — если уже готов переносить setup под себя
- Для следующего шага — [`14-validation-checklists.md`](14-validation-checklists.md) — если хочешь проверить, что setup реально работает
- Для следующего шага — [`28-three-level-planning-in-cline.md`](28-three-level-planning-in-cline.md) — если хочешь научиться не теряться в длинных задачах

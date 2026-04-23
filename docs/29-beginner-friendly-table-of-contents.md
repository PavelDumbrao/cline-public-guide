# 29. Понятное оглавление для новичка

Если ты открыл repo и почувствовал:
- «слишком много файлов»;
- «не понимаю, что читать первым»;
- «где здесь нормальный маршрут для человека?» —

то этот документ для тебя.

Его задача простая:
- быстро помочь выбрать **один** маршрут;
- не дать тебе читать всё подряд;
- показать, какой файл открывать следующим;
- вернуть тебя в точку опоры, если ты снова потерялся.

---

## Как пользоваться этим оглавлением

Не пытайся пройти весь repo линейно.

Правильный способ такой:
1. Сначала выбери **один сценарий**.
2. Пройди только его маршрут.
3. Не прыгай в соседние ветки, пока текущая не стала понятной.

Если запутался — возвращайся сюда.

---

## Быстрый выбор маршрута

| Если у тебя сейчас такой запрос | Куда идти |
|---|---|
| Я вообще не понимаю, с чего начать | [`00-start-here.md`](00-start-here.md) |
| Хочу понять Cline как систему | [`23-system-map-rules-skills-hooks-mcp.md`](23-system-map-rules-skills-hooks-mcp.md) |
| Хочу собрать минимальный setup | [`13-install-and-adapt.md`](13-install-and-adapt.md) |
| Хочу проверить, что setup реально работает | [`14-validation-checklists.md`](14-validation-checklists.md) + [`../examples/prompts/smoke-tests.md`](../examples/prompts/smoke-tests.md) |
| Хочу, чтобы мой Cline помог мне всё поставить | [`26-mega-prompt-for-ai-installer.md`](26-mega-prompt-for-ai-installer.md) |
| Хочу дать этот repo агенту как sync-pack | [`30-ai-agent-sync-pack.md`](30-ai-agent-sync-pack.md) + [`../ai/README_FOR_CLINE.md`](../ai/README_FOR_CLINE.md) |
| Уже запутался и хочу снова увидеть карту | этот файл + [`21-learning-path-for-students.md`](21-learning-path-for-students.md) |

---

## Самый короткий маршрут по умолчанию

Если не хочешь долго выбирать, открой по порядку:

1. [`00-start-here.md`](00-start-here.md)
2. [`01-cline-mental-model.md`](01-cline-mental-model.md)
3. [`21-learning-path-for-students.md`](21-learning-path-for-students.md)
4. [`13-install-and-adapt.md`](13-install-and-adapt.md)

Если потом захочешь научиться вести длинные задачи без хаоса:

5. [`28-three-level-planning-in-cline.md`](28-three-level-planning-in-cline.md)

---

## Маршрут 1. Я впервые слышу про Cline

Иди так:
1. [`00-start-here.md`](00-start-here.md)
2. [`01-cline-mental-model.md`](01-cline-mental-model.md)
3. [`21-learning-path-for-students.md`](21-learning-path-for-students.md)

**Что получишь:**
- поймёшь, что Cline — это не просто чат;
- увидишь базовые сущности;
- перестанешь читать repo хаотично.

---

## Маршрут 2. Я хочу понять карту всей системы

Иди так:
1. [`23-system-map-rules-skills-hooks-mcp.md`](23-system-map-rules-skills-hooks-mcp.md)
2. [`03-rules-guide-human.md`](03-rules-guide-human.md)
3. [`04-skills-guide-human.md`](04-skills-guide-human.md)
4. [`05-hooks-guide-human.md`](05-hooks-guide-human.md)
5. [`06-cline-workflows-guide-human.md`](06-cline-workflows-guide-human.md)
6. [`07-mcp-guide-human.md`](07-mcp-guide-human.md)

**Что получишь:**
- перестанешь путать rule, skill, hook, workflow и MCP;
- поймёшь, как слои связаны между собой;
- увидишь, в каком порядке систему лучше собирать.

---

## Маршрут 3. Я хочу быстро собрать минимальный setup

Иди так:
1. [`00-start-here.md`](00-start-here.md)
2. [`13-install-and-adapt.md`](13-install-and-adapt.md)
3. [`07-mcp-guide-human.md`](07-mcp-guide-human.md)
4. [`14-validation-checklists.md`](14-validation-checklists.md)
5. [`../examples/prompts/smoke-tests.md`](../examples/prompts/smoke-tests.md)

**Что получишь:**
- минимальный setup без перегруза;
- меньше шансов притащить лишние hooks и MCP;
- сразу доказательство, что setup реально работает.

---

## Маршрут 4. Я хочу учиться по фазам, а не по списку файлов

Иди так:
1. [`21-learning-path-for-students.md`](21-learning-path-for-students.md)
2. дальше следуй по фазам внутри него

**Что получишь:**
- нормальный учебный ритм;
- понимание, что пока рано, а что уже пора подключать;
- меньше риска утонуть в деталях слишком рано.

---

## Маршрут 5. Я хочу, чтобы мой Cline помог мне собрать setup

Это режим **AI-assisted install**, а не ещё не полный AI sync.

Иди так:
1. [`13-install-and-adapt.md`](13-install-and-adapt.md)
2. [`25-cross-platform-installation-paths.md`](25-cross-platform-installation-paths.md)
3. [`26-mega-prompt-for-ai-installer.md`](26-mega-prompt-for-ai-installer.md)
4. [`27-setup-self-check-and-recovery.md`](27-setup-self-check-and-recovery.md)

**Что получишь:**
- агент будет ставить не хаотично, а по install-протоколу;
- у него появятся stop conditions;
- после каждого слоя будет read-back и visibility proof.

---

## Маршрут 6. Я хочу дать repo агенту как sync-pack

Это уже режим **AI sync mode**.

Иди так:
1. [`30-ai-agent-sync-pack.md`](30-ai-agent-sync-pack.md)
2. [`../ai/README_FOR_CLINE.md`](../ai/README_FOR_CLINE.md)
3. потом при необходимости возвращайся к:
   - [`25-cross-platform-installation-paths.md`](25-cross-platform-installation-paths.md)
   - [`26-mega-prompt-for-ai-installer.md`](26-mega-prompt-for-ai-installer.md)
   - [`27-setup-self-check-and-recovery.md`](27-setup-self-check-and-recovery.md)

**Что получишь:**
- ясное разделение human docs и syncable `ai/` слоя;
- понятный порядок синка rules → skills → MCP → hooks;
- меньше шансов, что агент начнёт копировать repo целиком без верификации.

---

## Маршрут 7. Я уже что-то настроил и хочу проверить себя

Иди так:
1. [`14-validation-checklists.md`](14-validation-checklists.md)
2. [`27-setup-self-check-and-recovery.md`](27-setup-self-check-and-recovery.md)
3. [`10-troubleshooting.md`](10-troubleshooting.md)
4. [`../examples/prompts/smoke-tests.md`](../examples/prompts/smoke-tests.md)

**Что получишь:**
- поймёшь, что реально работает, а что только “лежит на диске”;
- найдёшь wrong-path и wrong-visibility кейсы;
- получишь recovery loop вместо хаотичных попыток.

---

## Если у тебя только один спокойный вечер

Вот хороший маршрут без перегруза:

1. [`00-start-here.md`](00-start-here.md)
2. [`01-cline-mental-model.md`](01-cline-mental-model.md)
3. [`21-learning-path-for-students.md`](21-learning-path-for-students.md)
4. [`13-install-and-adapt.md`](13-install-and-adapt.md)
5. [`07-mcp-guide-human.md`](07-mcp-guide-human.md)
6. [`14-validation-checklists.md`](14-validation-checklists.md)
7. [`../examples/prompts/smoke-tests.md`](../examples/prompts/smoke-tests.md)

Если останутся силы:
8. [`28-three-level-planning-in-cline.md`](28-three-level-planning-in-cline.md)

---

## Что не надо читать первым

Не потому что это плохие документы.
А потому что без базы они перегружают.

Не начинай с этого:
- [`24-rules-mega-guide.md`](24-rules-mega-guide.md)
- [`25-cross-platform-installation-paths.md`](25-cross-platform-installation-paths.md)
- [`26-mega-prompt-for-ai-installer.md`](26-mega-prompt-for-ai-installer.md)
- [`27-setup-self-check-and-recovery.md`](27-setup-self-check-and-recovery.md)

Сначала:
- пойми сущности;
- собери минимальный setup;
- докажи, что он работает;

и только потом усложняй систему.

---

## Самая простая формула навигации по repo

Если совсем коротко:
- **`00-start-here.md`** — первая точка входа;
- **`21-learning-path-for-students.md`** — маршрут по фазам;
- **`13-install-and-adapt.md`** — перенос под себя;
- **`14-validation-checklists.md`** + **`smoke-tests.md`** — доказательство, что setup работает;
- **`26-mega-prompt-for-ai-installer.md`** — режим, где setup помогает собирать агент;
- **`30-ai-agent-sync-pack.md`** — режим, где repo читает уже сам AI-агент как sync-pack.

---

## Если снова потеряешься

Сделай только три вещи:
1. вернись в [`00-start-here.md`](00-start-here.md);
2. выбери **один** маршрут из этого файла;
3. не прыгай в следующую ветку, пока текущая не стала понятной.

---

## Куда идти дальше прямо сейчас

- Хочешь первую точку входа → [`00-start-here.md`](00-start-here.md)
- Хочешь маршрут по фазам → [`21-learning-path-for-students.md`](21-learning-path-for-students.md)
- Хочешь переносить setup → [`13-install-and-adapt.md`](13-install-and-adapt.md)
- Хочешь подключить AI-установщика → [`26-mega-prompt-for-ai-installer.md`](26-mega-prompt-for-ai-installer.md)
- Хочешь включить AI sync mode → [`30-ai-agent-sync-pack.md`](30-ai-agent-sync-pack.md)
- Хочешь проверить setup → [`14-validation-checklists.md`](14-validation-checklists.md)

Если запутался — возвращайся сюда.

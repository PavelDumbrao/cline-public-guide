# Hooks

Здесь лежит **public hook pack** для Cline.

Это уже не просто игрушечные примеры, а публичный и безопасный mirror рабочего hook-слоя, который можно переносить почти 1-в-1 в свой setup.

---

## Что включено
- `TaskStart`
- `PreToolUse`
- `PostToolUse`
- `PreCompact`
- `SessionStart`
- `TaskComplete`
- `scripts/project_identity.py`
- `scripts/context_guard.py`

---

## Что это даёт
Этот hook pack показывает зрелую архитектуру:
- `TaskStart` = continuity load и project focus;
- `PreToolUse` = safety + giant-input guards;
- `PostToolUse` = telemetry + oversized-result handling;
- `PreCompact` = checkpoint и recovery bundle;
- `SessionStart` = restore после compaction;
- `TaskComplete` = уведомление и reminder по continuity.

Общая логика вынесена в helper scripts, а hooks остаются тонкими и понятными.

---

## Что здесь уже безопасно для публичного repo
- нет реальных токенов;
- нет chat id;
- нет приватных URL/IP;
- `TaskComplete` использует только env-переменные;
- project-specific значения остаются за пользователем.

---

## Как использовать
### Для человека
Сначала прочитай:
- `../../docs/05-hooks-guide-human.md`
- `../../docs/13-install-and-adapt.md`
- `../../docs/14-validation-checklists.md`

### Для AI-агента
Смотри:
- `../../docs/30-ai-agent-sync-pack.md`
- `../README_FOR_CLINE.md`

Если агент переносит setup из repo, он может копировать этот hook-layer как public base, а потом адаптировать только env и project-specific values.

---

## Что ещё важно
Этот пакет — **public mirror**, а не живая приватная система автора.

То есть:
- структура и логика близки к реальному setup;
- секреты и приватная инфраструктура сознательно убраны;
- перенос всё равно должен идти по шагам с visibility/smoke check.

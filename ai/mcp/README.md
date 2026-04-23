# MCP Public Sync Layer

Здесь лежит **public MCP layer** для синка setup через репозиторий.

Важно:
- это не live config автора;
- это safe template layer;
- секреты, токены и project-specific значения нужно подставлять вручную.

---

## Что использовать
- `mcp-config.template.json` — стартовый шаблон конфигурации
- `../README_FOR_CLINE.md` — инструкция для AI-агента
- `../../docs/07-mcp-guide-human.md` — объяснение для человека
- `../../docs/30-ai-agent-sync-pack.md` — как использовать repo как sync source

---

## Как переносить
1. Не подключай сразу все MCP.
2. Подключай по одному.
3. После каждого сервера проверяй visibility в интерфейсе.
4. Если нужен reload/reopen — делай это явно.
5. Не храни реальные токены в repo.

---

## Что считается хорошим результатом
Хорошо — это когда:
- MCP реально виден в Cline;
- агент может объяснить, зачем этот MCP нужен;
- секреты лежат в env/secure config, а не в markdown/json шаблоне.

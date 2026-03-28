# Smoke Test Prompts

## Smoke test rules
- «Ответь по-русски и предложи краткий план из 3 шагов.»
- «Если не уверен, сначала найди официальную документацию и скажи, что именно проверил.»

## Smoke test skills
- «Используй systematic-debugging и разложи причину 500 ошибки по шагам.»
- «Используй frontend-design и предложи структуру простого onboarding-экрана.»
- «Используй deployment-guide и дай чеклист перед деплоем.»

## Smoke test hooks
- «Объясни, должен ли `git add .env` быть заблокирован в безопасном setup.»
- «Проверь, что hook не должен печатать лишний текст в stdout.»

## Smoke test MCP
- «Найди в документации, как работает AbortController для fetch.»
- «Покажи, как бы ты использовал web search для проверки спорного API-вопроса.»

## Smoke test browser automation
- «Открой страницу и проверь, есть ли ошибки в консоли.»
- «Проверь, отвечает ли основной пользовательский сценарий без падений.»

## Smoke test public repo sanitation
- «Проведи проверку repo: нет ли токенов, IP, доменов, credentials или private-only материалов.»
- «Проверь, не перепутаны ли Cline workflows и n8n examples.»

# 07. MCP Guide

## Что такое MCP
MCP — это способ подключить к Cline внешние инструменты и источники данных.

## Чем MCP отличается от skills / hooks / workflows
- MCP даёт инструмент или данные
- skill даёт знания и шаблон мышления
- hook автоматически запускает скрипт на событии
- workflow задаёт шаги работы

## Must-have MCP для новичка
- `context7` — документация библиотек
- `tavily` — веб-поиск и research
- `playwright` — браузер и UI-проверки

## Optional MCP
- `github` — если работаешь с GitHub
- `exa` — если нужен чистый поиск
- `cocoindex-code` — если у тебя большая локальная кодовая база
- `n8n-docs` — если работаешь с n8n

## Advanced MCP
- `n8n-mcp` — для live-инстанса n8n
- второй Exa MCP, если ты понимаешь зачем он нужен

## Private-only MCP
- `hostinger-api`

## Какие MCP нужны по ролям

### Разработчик frontend/fullstack
- context7
- tavily
- playwright
- github

### Человек, работающий с n8n
- context7
- tavily
- n8n-docs
- при необходимости n8n-mcp

### Человек, автоматизирующий браузер
- playwright
- context7
- tavily

## Какие требуют API keys или логин
Чаще всего требуют:
- tavily
- exa
- github
- railway
- n8n live access
- hostinger-api

## Как безопасно добавлять MCP
1. Подключай по одному
2. Понимай, зачем он нужен
3. Проверяй, не дублирует ли он уже существующий MCP
4. Не храни секреты в repo
5. Проверяй, какие данные MCP может читать и отправлять

## Типичная ошибка
Ставить 10 MCP сразу и потом не понимать, какой из них реально нужен.

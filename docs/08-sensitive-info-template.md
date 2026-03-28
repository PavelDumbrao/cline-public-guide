# 08. Sensitive Info Template

## Что считается sensitive info
- API keys
- токены ботов
- chat IDs
- email-адреса
- IP-адреса
- домены приватных сервисов
- webhook URLs
- database URLs
- логины и пароли
- приватные пути на сервере

## Где нельзя хранить секреты
- в rules
- в skills
- в hooks
- в markdown-примерах
- в repo history

## Чем заменять
- `<API_KEY>`
- `<BOT_TOKEN>`
- `<CHAT_ID>`
- `<PRIVATE_URL>`
- `<PRIVATE_IP>`
- `<DB_URL>`
- `<SSH_HOST>`

## Проверка перед публикацией
1. Поиск по `token`
2. Поиск по `key`
3. Поиск по `password`
4. Поиск по `http://` и `https://`
5. Поиск по IP-адресам
6. Поиск по `.env`, `credentials`, `webhook`

## Главная мысль
Публичный репозиторий должен быть **шаблоном**, а не слепком работающей приватной системы.

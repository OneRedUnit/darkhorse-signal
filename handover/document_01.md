# DARKHORSE VPS – Handover Document

## 1. Общая цель текущей конфигурации
Мы отказались от старого хаотичного Docker-стека на VPS (Ubuntu) и развернули систему заново.  
На данный момент приоритет:
- Рабочее **Gitea** с доступом по HTTPS через Caddy.
- Локальный **Qdrant** (в контейнере) с HTTPS через Caddy.
- Простое реверс-проксирование по доменам с авто-TLS.
- Возможность легко добавлять новые сервисы по той же схеме.

---

## 2. Принятые технические решения

### Reverse Proxy
- **Caddy** выбран вместо Nginx.
- Причины:
  - Автоматическое получение и обновление SSL/TLS сертификатов Let’s Encrypt.
  - Минимальные конфиги для каждого домена.
  - Простота расширения конфигурации.
- Домены и привязки:
  - `vault.sarmata5.com` → **Gitea** (порт 3000, localhost).
  - `cell-memory.sarmata5.com` → **Qdrant** (порт 6333, localhost).

### Контейнеризация
- **Docker Compose** для управления сервисами.
- Сервисы слушают **только на localhost**, кроме SSH в Gitea (порт 2222).
- Данные хранятся в постоянных директориях.

### Хранилище данных
- **Gitea**: `/root/gitea/data` (права `1000:1000`).
- **Qdrant**: `/srv/qdrant/storage`.

---

## 3. Текущий стек

### Сервисы и контейнеры
```yaml
services:
  gitea:
    image: gitea/gitea:latest
    ports: ["127.0.0.1:3000:3000", "0.0.0.0:2222:22"]
    volumes:
      - /root/gitea/data:/data

  qdrant:
    image: qdrant/qdrant:latest
    ports: ["127.0.0.1:6333:6333", "127.0.0.1:6334:6334"]
    volumes:
      - /srv/qdrant/storage:/qdrant/storage

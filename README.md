# 🔐 HTTP Server Credential Logger (Go)

Цей проєкт — простий HTTP-сервер на Go, який приймає POST-запити на `/login` і логує облікові дані у файл `credentials.txt`. Крім того, сервер роздає статичні файли з директорії `public`.

⚠️ **Попередження**: цей код не безпечний і не призначений для продакшену! Його слід використовувати лише для освітніх цілей або в межах тестування.

---

## 🧠 Опис

- Обробник `/login` логує `_user`, `_pass`, IP-адресу, User-Agent і час спроби входу.
- Усі логи записуються у файл `credentials.txt`.
- Статичний контент (HTML/CSS/JS) доступний через `/`, напр., `http://localhost:8080/index.html`.

---

## 🚀 Запуск
1. Встановлення залежностей

```bash
go get github.com/gorilla/mux
go get github.com/sirupsen/logrus
```

2. Підготовка проєкту
- Створи папку public з HTML-файлом, напр., index.html.
- Збери сервер:

```bash
go run main.go
```

3. Надішли запит

```bash
curl -X POST -d "_user=test&_pass=secret" http://localhost:8080/login
```

4. Перевір лог

У credentials.txt з’явиться щось на кшталт:

```pgsql
time=2025-04-22T14:31:10Z username=test password=secret user-agent=curl/7.81.0 ip_address=127.0.0.1:52144 level=info msg="login attempt"
```

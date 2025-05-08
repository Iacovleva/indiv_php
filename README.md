Описание проекта
Этот проект реализует простую систему авторизации с использованием Node.js, Express и MongoDB. Пользователь может зарегистрироваться, войти в систему и получить доступ к защищённым маршрутам.

Функционал API
✅ Регистрация (POST /api/auth/register) – создание нового пользователя с шифрованным паролем ✅ Вход (POST /api/auth/login) – проверка email/пароля и генерация JWT-токена ✅ Защита API (middlewares/verifyToken.js) – доступ к данным только с токеном ✅ MongoDB + Express – хранение пользователей в базе данных

Описание маршрутов API
Регистрация пользователя
Запрос: POST /api/auth/register

Пример JSON:
{
  "username": "Elena",
  "email": "elena@example.com",
  "password": "123456"
}

Ответ:
{
  "_id": "65c123abcd456ef789",
  "username": "Elena",
  "email": "elena@example.com",
  "createdAt": "2025-05-08T18:30:00.000Z"
}

Вход в систему
Запрос: POST /api/auth/login

Пример JSON:
{
  "email": "elena@example.com",
  "password": "123456"
}

Ответ:
{
  "token": "eyJhbGciOiJIUzI1NiIsInR..."
}

Доступ к защищённому маршруту (/api/user/profile)
Запрос: GET /api/user/profile

Headers:

Authorization: Bearer ТВОЙ_ТОКЕН
Ответ (если токен верный):
{
  "username": "Elena",
  "email": "elena@example.com",
  "createdAt": "2025-05-08T18:30:00.000Z"
}

Если токен неверный или отсутствует:
{
  "error": "Доступ запрещён"
}
Технологии
✅ Node.js + Express – для обработки запросов ✅ MongoDB – для хранения данных о пользователях ✅ bcrypt – для безопасного хранения паролей ✅ jsonwebtoken (JWT) – для защиты маршрутов

Вывод
Этот проект успешно реализует базовую авторизацию с защитой маршрутов. 📌 Можно дорабатывать: добавлять восстановление пароля, роли пользователей и поддержку OAuth (Google Login).
# Notes API

Веб-приложение для управления личными заметками с использованием FastAPI и Telegram. Он включает CRUD операции для заметок, аутентификацию пользователей с помощью JWT и интеграцию с Telegram для авторизации.

## Структура проекта

- `app/main.py`: Основной файл для запуска FastAPI приложения.
- `app/bot.py`: Основной файл для работы с Telegram ботом.
- `app/models.py`: Определение моделей базы данных.
- `app/schemas.py`: Pydantic схемы для валидации данных.
- `app/crud.py`: CRUD операции для работы с базой данных.
- `app/auth.py`: Функции для аутентификации и работы с JWT.
- `app/database.py`: Подключение к базе данных и конфигурация сессий.
- `Dockerfile`: Docker файл для создания контейнера.
- `docker-compose.yml`: Docker Compose файл для запуска приложения и базы данных.

## Настройка и запуск проекта

### Требования

- Python 3.8+ (тестировалось на 3.12 версс)
- PostgreSQL (тестировалось на 16 версии)

### Установка зависимостей

1. **Создайте виртуальное окружение и активируйте его:**

   ```bash
   python -m venv venv
   source .venv/bin/activate  # Для Windows используйте `.venv\Scripts\activate`
   ```

2. **Установите:**

   ```bash
   pip install -r requirements.txt
   ```

### Настройка базы данных
**Обновите файл app/database.py с вашими данными для подключения к базе данных:**

   ```bash
   SQLALCHEMY_URL = "postgresql://username:password@localhost:5432/your_database"
   ```

### Запуск приложения
**Запустите приложение и базу данных с помощью Docker Compose:**

   ```bash
   docker-compose up --build
   ```

Приложение будет доступно по адресу http://localhost:3000.

## Использование Telegram бота
### Запуск бота
Для запуска Telegram бота, используйте команду:

   ```bash
   python app/bot.py
   ```

Бот использовать заданный секретный ключ для аутентификации пользователей через ваш API.
/start — Запускает бот и инициирует процесс авторизации пользователя. После успешной авторизации, бот предложит основные действия через кнопки:
Авторизация через Telegram происходит с помощью хеша, который генерируется на основе ID и имени пользователя Telegram.
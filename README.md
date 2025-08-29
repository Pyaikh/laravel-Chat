# Chat Application

Современное веб-приложение для обмена сообщениями в реальном времени, построенное на Laravel 12 с использованием Livewire 3 и WebSocket технологий.

## 🚀 Технологии

- **Backend**: Laravel 12 (PHP 8.2+)
- **Frontend**: Livewire 3, Tailwind CSS 4, Vite
- **Real-time**: Laravel Broadcasting, Pusher
- **Database**: SQLite (по умолчанию)
- **Testing**: Pest PHP

## ✨ Возможности

- 💬 Чат в реальном времени между пользователями
- 🔐 Аутентификация и авторизация пользователей
- 👥 Список пользователей с возможностью выбора собеседника
- 📱 Адаптивный дизайн с современным UI
- ⚡ Мгновенная доставка сообщений через WebSocket
- 🎯 Индикатор набора текста
- 🎨 Настройки профиля и внешнего вида

## 📋 Требования

- PHP 8.2 или выше
- Composer
- Node.js и npm
- SQLite (или MySQL/PostgreSQL)

## 🛠️ Установка

1. **Клонируйте репозиторий**
   ```bash
   git clone <repository-url>
   cd chat
   ```

2. **Установите PHP зависимости**
   ```bash
   composer install
   ```

3. **Установите Node.js зависимости**
   ```bash
   npm install
   ```

4. **Настройте окружение**
   ```bash
   cp .env.example .env
   php artisan key:generate
   ```

5. **Настройте базу данных**
   ```bash
   # Для SQLite (по умолчанию)
   touch database/database.sqlite
   
   # Или настройте MySQL/PostgreSQL в .env файле
   ```

6. **Выполните миграции**
   ```bash
   php artisan migrate
   ```

7. **Настройте broadcasting (для real-time функционала)**
   ```bash
   # Добавьте в .env файл настройки Pusher или Reverb
   BROADCAST_CONNECTION=pusher
   PUSHER_APP_ID=your_app_id
   PUSHER_APP_KEY=your_app_key
   PUSHER_APP_SECRET=your_app_secret
   PUSHER_APP_CLUSTER=your_cluster
   ```

## 🚀 Запуск

### Разработка

Запустите все сервисы одной командой:
```bash
composer run dev
```

Эта команда запустит:
- Laravel сервер
- Очередь сообщений
- Логи в реальном времени
- Vite dev сервер

### Продакшн

1. **Соберите assets**
   ```bash
   npm run build
   ```

2. **Запустите сервер**
   ```bash
   php artisan serve
   ```

3. **Запустите очередь (в отдельном терминале)**
   ```bash
   php artisan queue:work
   ```

## 🏗️ Архитектура

### Основные компоненты

- **Chat** (`app/Livewire/Chat.php`) - основной Livewire компонент чата
- **ChatMessage** (`app/Models/ChatMessage.php`) - модель сообщений
- **MessageSent** (`app/Events/MessageSent.php`) - событие отправки сообщения
- **User** (`app/Models/User.php`) - модель пользователя

### База данных

- `users` - таблица пользователей
- `chat_messages` - таблица сообщений с полями:
  - `sender_id` - ID отправителя
  - `receiver_id` - ID получателя
  - `message` - текст сообщения
  - `timestamps` - время создания/обновления

### Real-time функционал

Приложение использует Laravel Broadcasting для мгновенной доставки сообщений:
- Приватные каналы для каждого пользователя
- WebSocket соединения через Pusher
- Индикатор набора текста в реальном времени

## 🧪 Тестирование

Запустите тесты:
```bash
composer run test
```

## 📁 Структура проекта

```
chat/
├── app/
│   ├── Events/          # События для broadcasting
│   ├── Http/            # HTTP контроллеры
│   ├── Livewire/        # Livewire компоненты
│   ├── Models/          # Eloquent модели
│   └── Providers/       # Сервис-провайдеры
├── database/
│   ├── migrations/      # Миграции базы данных
│   └── seeders/         # Сидеры данных
├── resources/
│   ├── views/           # Blade шаблоны
│   ├── css/             # Стили
│   └── js/              # JavaScript файлы
├── routes/               # Маршруты приложения
└── tests/                # Тесты
```

## 🔧 Настройка

### Broadcasting

Для работы real-time функционала настройте один из драйверов:

- **Pusher** (рекомендуется для продакшна)
- **Reverb** (новый драйвер от Laravel)
- **Redis** (для локальной разработки)

### Очереди

Приложение использует очереди для обработки broadcast событий. Убедитесь, что worker очереди запущен:

```bash
php artisan queue:work
```

## 🤝 Вклад в проект

1. Форкните репозиторий
2. Создайте ветку для новой функции
3. Внесите изменения
4. Создайте Pull Request

## 📄 Лицензия

MIT License

## 🆘 Поддержка

Если у вас возникли вопросы или проблемы, создайте Issue в репозитории.

---

**Примечание**: Это приложение является стартовым набором для Laravel с Livewire и может быть расширено дополнительными функциями в зависимости от ваших потребностей.

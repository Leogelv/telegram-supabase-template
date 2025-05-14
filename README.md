# Telegram Mini App с интеграцией Supabase

Готовый шаблон для создания Telegram Mini App с использованием React, TypeScript и интеграцией с Supabase для хранения данных и аутентификации пользователей Telegram.

## Особенности

- 🚀 **React + TypeScript**: Современный стек с типизацией
- 📱 **Telegram Mini App API**: Полная интеграция с Telegram Mini Apps SDK
- 🔐 **Аутентификация через Telegram**: Безопасная авторизация на основе initData
- 💾 **Supabase интеграция**: Готовая настройка хранения данных и авторизации
- 🌐 **TON Connect**: Поддержка интеграции с блокчейном TON
- 🔄 **Vite**: Быстрая сборка и разработка

## Быстрый старт

1. Клонируйте репозиторий:
```bash
git clone https://github.com/Leogelv/telegram-supabase-template.git my-telegram-app
cd my-telegram-app
```

2. Установите зависимости:
```bash
npm install
```

3. Создайте `.env.local` файл с следующими переменными:
```
NEXT_PUBLIC_SUPABASE_URL=your-supabase-url
NEXT_PUBLIC_SUPABASE_ANON_KEY=your-supabase-anon-key
```

4. Настройте схему базы данных в Supabase, используя SQL из `scripts/supabase-schema.sql`

5. Запустите приложение:
```bash
npm run dev
```

## Документация

Подробная документация по настройке и использованию находится в директории `docs/`:

- [Настройка Supabase](docs/SUPABASE_SETUP.md)
- [Планирование и задачи](docs/TASK.md)
- [Краткосрочное планирование](docs/SHORT_PLANNING.md)

## Структура проекта

```
src/
├── components/      # Общие компоненты
├── css/            # Стили
├── helpers/        # Вспомогательные функции
├── lib/            # Библиотеки
│   └── supabase/   # Интеграция с Supabase
├── navigation/     # Маршрутизация
├── pages/          # Страницы приложения
```

## Лицензия

MIT 
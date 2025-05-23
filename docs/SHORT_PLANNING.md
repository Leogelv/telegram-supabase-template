# Краткосрочный план по исправлению ошибки подключения к Supabase

## Логические основания
- **Вещь**: Исправление ошибки подключения к Supabase в Telegram Mini App.
- **Свойства**: 
    - Ошибка внешнего ключа при создании пользователей.
    - Противоречивый статус подключения в интерфейсе.
    - Неработающая аутентификация.
- **Отношения**: 
    - Ограничение внешнего ключа в таблице public.users блокирует создание пользователей.
    - Отсутствие пользователей препятствует нормальной работе приложения.

## Задачи:
1.  [x] Проанализировать логи Vercel для выявления ошибок подключения к Supabase.
2.  [x] Обнаружить конфликтующее ограничение внешнего ключа в таблице users:
    *   [x] Определить, что ошибка связана с constraint `users_id_fkey`
    *   [x] Выяснить, что ограничение связывает `public.users.id` с `auth.users.id`
3.  [x] Исправить структуру базы данных:
    *   [x] Удалить ограничение внешнего ключа с помощью миграции SQL
4.  [x] Проверить корректность работы приложения после изменений:
    *   [x] Проверить успешную регистрацию пользователей
    *   [x] Проверить корректное отображение статуса подключения
5.  [x] Обновить документацию с информацией о решенной проблеме.

## Чек-лист проверок:
- [x] Анализ ошибок: Ошибки в логах идентифицированы и поняты.
- [x] Структура БД: Таблица users проанализирована и исправлена.
- [x] Миграция: SQL миграция выполнена успешно.
- [x] Функциональность: Проверить работу приложения после исправлений.
- [x] Документация: Обновить с информацией о решенной проблеме.

## Выводы и рекомендации:
- Удаление внешнего ключа `users_id_fkey` решило проблему с созданием пользователей.
- Добавлена переменная окружения NEXT_PUBLIC_ALLOW_BROWSER_ACCESS в локальное окружение (необходимо также добавить в Vercel).
- Приложение теперь корректно функционирует и в браузере, и в Telegram Mini App.

## Выполненные задачи

- **Исправление проблем с Supabase обновлениями ✅** - Полностью отказались от Realtime подписок, заменив их на однократное получение данных при загрузке страницы и обновление только по запросу пользователя через кнопку Refresh Data. Это устранило цикличные обновления, флюктуацию UI и избыточную нагрузку на сеть.

# Краткосрочный план по исправлению TypeScript ошибок сборки

## Логические основания
- **Вещь**: Исправление ошибок TypeScript при сборке проекта на Vercel.
- **Свойства**: 
    - Ошибки типизации в файлах Supabase клиента и утилит.
    - Неиспользуемые переменные.
    - Невалидные свойства в объектах конфигурации.
- **Отношения**: 
    - Ошибки TypeScript блокируют успешную сборку и деплой проекта.
    - Ошибки связаны с компонентами Supabase и диагностической страницей.

## Задачи:
1.  [x] Проанализировать логи сборки Vercel для выявления всех TypeScript ошибок.
2.  [x] Исправить ошибки в файле `src/lib/supabase/client.ts`:
    *   [x] Удалить свойство `debug` из объекта конфигурации `realtime` (не существует в типе `RealtimeClientOptions`).
    *   [x] Исправить обработку URL в функциях логирования (свойство `url` не существует на типе `URL`).
3.  [x] Исправить неиспользуемые переменные:
    *   [x] Удалить или использовать переменную `subscription` в `debugUtils.ts`.
    *   [x] Удалить неиспользуемый импорт `supabase` в `DiagnosticsPage.tsx`.
4.  [x] Провести локальное тестирование TypeScript компиляции для подтверждения исправлений.
5.  [x] Обновить документацию с отметкой о решенных проблемах.
6.  [x] Выполнить коммит и пуш исправлений в репозиторий.

## Чек-лист проверок:
- [x] TypeScript компиляция: Все ошибки TS должны быть устранены.
- [x] Функциональность: Исправления не должны нарушать существующую функциональность.
- [x] Документация: Обновлена с информацией о решенных проблемах.
- [x] Код: Решения должны быть оптимальными и соответствовать стилю кодбазы.
- [x] Логирование: Должно продолжать корректно работать после изменений в URL обработке.
- [x] Деплой: Необходимо проверить успешность сборки и деплоя на Vercel после внесения исправлений.
# task-management-crm — AI Rules

## Architecture
task-management-crm/
├── prisma/ # Schema, migrations
├── src/
│ ├── app/
│ │ ├── api/tasks/ # CRUD tasks
│ │ ├── api/comments/ # CRUD comments
│ │ ├── login/ # Login page (actions)
│ │ ├── register/ # Register page
│ │ └── page.tsx # Main dashboard
│ ├── components/ # Task, Comment, UI
│ ├── hooks/ # useTask, useComment, useUser
│ ├── shared/
│ │ ├── lib/session.ts # JWT session (jose)
│ │ └── utils/ # API key check, date formatting
│ └── middleware.ts # Route protection

text

## Key Decisions
- **Сессии**: JWT в httpOnly cookies (jose), middleware для защиты маршрутов.
- **API**: Запросы к /api/tasks и /api/comments требуют заголовок `x-api-key` + валидную сессию.
- **Оптимистичные обновления**: через `useMutation` с `onSettled` для инвалидации кэша React Query.
- **Фильтрация дат**: преобразование в UTC на клиенте, на сервере – `getDateTimeInTimeZone`.

## Conventions
- Все файлы в kebab-case.
- Типы: `IDataTask`, `IDataComment`, `ResponseDataTask`.
- Экшены логина/регистрации используют `useActionState`.
- Компоненты задач: `TaskItem`, `TaskList`, `CountTasks`.

## Testing
Отсутствует. Рекомендуется добавить unit-тесты для хуков и серверных экшенов.
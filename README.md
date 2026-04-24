# Task Management CRM

Система управления задачами с комментариями, фильтрацией, PWA и ролевой моделью.

**Стек:** Next.js 15 App Router, Prisma (PostgreSQL), React Query, Tailwind CSS v4, Zod.

## Возможности
- Регистрация/логин через серверные экшены (JWT сессии)
- Создание, редактирование, удаление задач
- Статусы: новая, в работе, ожидание, отменено, выполнено, в архиве
- Отчёты к задачам
- Комментарии с inline-редактированием
- Фильтр по статусу и дате (день/диапазон)
- PWA (next-pwa), установка на устройство
- API защищён через x-api-key

## Быстрый старт
```bash
cp .env.example .env   # настроить DATABASE_URL и SESSION_SECRET
docker compose up -d   # PostgreSQL
npx prisma migrate deploy
npm run dev
Приложение: http://localhost:3000

Тестовые аккаунты
Любой зарегистрированный через /register
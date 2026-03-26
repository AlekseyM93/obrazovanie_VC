# Tutor Platform MVP

MVP-платформа для репетиторов и учеников на **Next.js + TypeScript + Prisma + PostgreSQL + LiveKit + S3/MinIO**.

## Что уже заложено

- роли: tutor / student / admin
- онлайн-комнаты для уроков
- выдача LiveKit токена для видеоконференции
- заготовка под запись уроков и обработку webhook
- база знаний с загрузкой файлов в S3/MinIO
- интерактивная доска в интерфейсе урока
- Prisma-схема для дальнейшего расширения
- готовый промт для Cursor

## Почему такой стек

- **Next.js App Router** удобно использовать как fullstack-приложение с UI и backend route handlers. Официальная документация рекомендует route handlers внутри `app` для HTTP-обработчиков. citeturn730246search1turn730246search10
- **Prisma + PostgreSQL** дают типобезопасный доступ к данным и удобные миграции для Next.js-проектов. citeturn730246search2turn730246search8turn730246search20
- **LiveKit** подходит для комнат, screen share и записи. В документации есть room service, screen sharing, webhooks и egress API для записи комнат. citeturn730246search15turn730246search21turn730246search12turn730246search3

## Быстрый запуск

```bash
cp .env.example .env
docker compose up -d
npm install
npx prisma generate
npx prisma migrate dev --name auth_init
npm run db:seed
npm run dev
```

## Что открыть

- главная: `http://localhost:3000`
- дашборд: `http://localhost:3000/dashboard`
- тестовая комната: `http://localhost:3000/rooms/demo-room`
- login: `http://localhost:3000/auth/login`
- MinIO console: `http://localhost:9001`

## Демо-аккаунты

- `admin@tutor.local` / `AdminPass123`
- `tutor@tutor.local` / `TutorPass123`
- `student@tutor.local` / `StudentPass123`

## Что нужно доделать в Cursor

1. Подключить настоящую аутентификацию через Auth.js / Clerk / Supabase Auth.
2. Сделать нормальное управление пользователями и доступом.
3. Реализовать создание уроков из БД, а не через мок.
4. Подключить реальную запись через LiveKit Egress и хранение видео в S3.
5. Добавить чат, календарь, домашки, уведомления, оплату.
6. Заменить простую whiteboard-заглушку на полноценную доску (например, tldraw или Excalidraw).
7. Сделать продакшн-деплой: HTTPS, Redis, jobs, background workers, monitoring.

## Статус

Это **сильный стартовый каркас**, а не полностью законченный Zoom-клон. Он специально подготовлен так, чтобы ты мог быстро продолжить разработку в Cursor.

# 🔮 Таро — Нити Судьбы

## Деплой на Vercel — пошаговая инструкция

---

### ШАГ 1 — Получите API-ключ Anthropic

1. Зайдите на https://console.anthropic.com
2. Нажмите **API Keys** → **Create Key**
3. Скопируйте ключ (начинается с `sk-ant-...`) — он покажется только один раз!

---

### ШАГ 2 — Создайте аккаунт на Vercel

1. Зайдите на https://vercel.com
2. Нажмите **Sign Up** → войдите через GitHub (бесплатно)

---

### ШАГ 3 — Загрузите файлы на GitHub

1. Зайдите на https://github.com → **New repository**
2. Назовите репозиторий `tarot-app`, нажмите **Create**
3. Загрузите все файлы из этой папки:
   - `api/tarot.js`
   - `public/index.html`
   - `vercel.json`
   - `package.json`

Или через терминал:
```bash
git init
git add .
git commit -m "first commit"
git remote add origin https://github.com/ВАШ_ЛОГИН/tarot-app.git
git push -u origin main
```

---

### ШАГ 4 — Подключите GitHub к Vercel

1. На https://vercel.com нажмите **Add New Project**
2. Выберите ваш репозиторий `tarot-app`
3. Нажмите **Import** → настройки оставьте по умолчанию
4. **НЕ нажимайте Deploy ещё!** — сначала добавьте ключ (Шаг 5)

---

### ШАГ 5 — Добавьте API-ключ в Vercel (самое важное!)

1. В настройках проекта найдите раздел **Environment Variables**
2. Нажмите **Add**:
   - **Name:** `ANTHROPIC_API_KEY`
   - **Value:** `sk-ant-ваш-ключ-здесь`
3. Нажмите **Save**

---

### ШАГ 6 — Деплой!

1. Нажмите **Deploy**
2. Подождите ~1 минуту
3. Vercel выдаст вам ссылку вида: `https://tarot-app-xxxxxx.vercel.app`

🎉 **Готово!** Приложение работает, ключ скрыт, Claude отвечает.

---

## Структура проекта

```
tarot-vercel/
├── api/
│   └── tarot.js        ← серверная функция (здесь хранится ключ)
├── public/
│   └── index.html      ← ваше приложение
├── vercel.json         ← конфигурация маршрутов
└── package.json        ← версия Node.js
```

## Как это работает

```
Пользователь → index.html → /api/tarot → Anthropic API
                                ↑
                        Ключ хранится здесь,
                        в переменных Vercel.
                        Никто его не видит!
```

---

## Обновление приложения

Любой `git push` автоматически деплоит новую версию — Vercel следит за репозиторием сам.

```bash
# Внесли изменения в index.html → просто:
git add .
git commit -m "обновил приложение"
git push
# Через 30 секунд уже на сайте ✓
```

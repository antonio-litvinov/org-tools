# org-tools — контекст проекта

## Что это
Инструменты для управления структурой команды и визуализации показателей.
Репозиторий: https://github.com/antonio-litvinov/org-tools

## Файлы проекта
- `apps/team-cards.html` — визуализация команд: перетаскивание сотрудников, импорт/экспорт Excel
- `apps/dashboard.html` — дашборд показателей (ещё не создан как файл, дизайн есть в Pencil)
- `design/design-kit.pen` — дизайн-системы в Pencil

## Дизайн-системы в design-kit.pen
Два дизайн-системы в одном файле:

### 1. Light & Airy (frame `FSlEZ`)
Основная система: кнопки, карточки, метрики, прогресс-бары, бейджи, чарт.
- Компоненты с префиксом `DS/`
- Dashboard frame: `OwFJp` ("Показатели управления")

### 2. Команды (frame `Bkvvp`)
Для инструмента team-cards. Компоненты с префиксом `Team/`:
- `Team/Chip/*` — 7 вариантов по роли (Backend, Frontend, Аналитика, Тестирование, Дизайн, ML, Delivery)
- `Team/RoleHeader/*` — минималистичные заголовки секций ролей
- `Team/Button/*` — Primary, Success, Neutral (маленькие, градиентные)
- `Team/Status/*` — Success, Error, Info (тост-уведомления)
- `Team/Card` — карточка команды с хедером и слотом для контента

## Дизайн-язык
**"Light & Airy"** — светлый, лёгкий, современный:
- Фон: `#FAFBFC`, карточки: `#FFFFFF`
- Чипы: белая основа + слабый градиент цвета роли + прозрачная рамка
- Кнопки: `padding: 6px 13px`, `font-size: 13px`, белая основа + градиент
- Статусы: белая основа + `rgba`-градиент + `rgba`-рамка (без solid-заливки)
- Шрифты: Inter (UI) + JetBrains Mono (числа)
- Иконки: Lucide (inline SVG)

### CSS-переменные (design tokens)
```css
--ds-accent-blue: #3B82F6
--ds-bg-card: #FFFFFF
--ds-bg-primary: #FAFBFC
--ds-border-light: #E5E9EF
--ds-text-primary: #1A1D21
--ds-text-secondary: #4B5563
--ds-text-muted: #9BA3AF
--ds-success: #10B981
--ds-warning: #F59E0B
--ds-radius-lg: 16px
--ds-radius-md: 10px
--ds-radius-pill: 999px
```

### Цвета ролей
```css
--role-backend-color: #EA580C
--role-frontend-color: #059669
--role-analytics-color: #2563EB
--role-testing-color: #D97706
--role-design-color: #BE185D
--role-ml-color: #7C3AED
--role-delivery-color: #DC2626
```

## team-cards.html — техническая архитектура
- **SheetJS** (CDN) — чтение/запись `.xlsx`
- **HTML5 Drag & Drop API** — перемещение чипов между командами
- Данные: массив `teams[]` с полями `{name, members: [{name, role}]}`
- Ключевые функции: `renderTeams()`, `createTeamCard()`, `saveToExcel()`, `downloadTemplate()`
- Drag: `.person-chip` draggable → drop на `.person-chips` контейнер
- Drop-target визуализация: класс `drop-target` (dashed outline, rgba-фон)

## Следующие шаги (идеи)
- [ ] Сгенерировать `apps/dashboard.html` из дизайна в Pencil
- [ ] Итеративно развивать team-cards и dashboard

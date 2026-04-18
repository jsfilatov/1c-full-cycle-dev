# Навык `1c-full-cycle-dev`

Документация навыка в этом репозитории.

Полный цикл доработки 1С в **существующей** конфигурации: фазы **0–12**, Phase Gate (**strict** по умолчанию, **`fast_track`** только по явному opt-in в чате), PRD/ADR, ревью плана, таск-лист, реализация через **`phase9-context-index.md`** и субагентов **`1c-developer`** / **`1c-metadata-manager`** для `src/cf/**` и `src/cfe/**`, ревью кода, итоги, опционально документация. Рабочие артефакты — в `.tasks/task-[feature-name]/`.

**Нормативный текст процесса** — только в [`SKILL.md`](.cursor/skills/1c-full-cycle-dev/SKILL.md) (в т.ч. gate-таблица, дословные вопросы в «Дословные gate-вопросы», приёмочные исправления, лимиты итераций). **Копируемые шаблоны** — в [`references/`](.cursor/skills/1c-full-cycle-dev/references/) (`prd-template.md`, `tasks-template.md`, `acceptance-record-template.md`, `phase9-context-index-template.md`, `workflow-state-template.md`, `artifact-layout.md`).

| Путь | Назначение |
|------|------------|
| [`.cursor/skills/1c-full-cycle-dev/SKILL.md`](.cursor/skills/1c-full-cycle-dev/SKILL.md) | Алгоритм фаз, gate, субагенты, исключения |
| [`.cursor/skills/1c-full-cycle-dev/references/`](.cursor/skills/1c-full-cycle-dev/references/) | Шаблоны для вставки в каталог задачи |

## Когда использовать / не использовать

**Использовать:** нетривиальная доработка с фиксацией требований (PRD/ADR), ревью плана до кода, приёмка с ID, итерации по замечаниям приёмки при уже сохранённых артефактах.

**Не использовать:** тривиальный хотфикс; достаточно одного вызова `1c-developer` / `1c-error-fixer` без конвейера.

Триггеры и краткое назначение — в поле `description` frontmatter [`SKILL.md`](.cursor/skills/1c-full-cycle-dev/SKILL.md).

Пример вызова:

```bash
/1c-full-cycle-dev Добавить интеграцию с API складской системы
```

## Установка

1. Развернуть в проекте набор [comol/cursor_rules_1c](https://github.com/comol/cursor_rules_1c) (`.cursor/rules/`, `.cursor/agents/`, MCP по их документации).
2. Агент **`1c-code-explorer`**: файл в `.cursor/agents/` из **модифицированной** линии **AndreevED/1c-ai-feature-dev-workflow**, `name: 1c-code-explorer`.
3. Правило **`code-explorer-rules.mdc`** в `.cursor/rules/` (в этом репозитории: [`.cursor/rules/code-explorer-rules.mdc`](.cursor/rules/code-explorer-rules.mdc)) — нужно для ожидаемого поведения Phase 2; при переносе только навыка скопировать правило отдельно.
4. Каталог навыка **`1c-full-cycle-dev`** целиком в `.cursor/skills/` — вместе с [`SKILL.md`](.cursor/skills/1c-full-cycle-dev/SKILL.md) и [`references/`](.cursor/skills/1c-full-cycle-dev/references/).

**Требования:** среда с субагентами; исходники 1С в репозитории (или согласованный способ); MCP для 1С — по рекомендациям **comol/cursor_rules_1c**.

## Возобновление в новом чате

Источник истины по шагу — **каталог задачи** и при наличии **`workflow-state.md`** (шаблон: [`workflow-state-template.md`](.cursor/skills/1c-full-cycle-dev/references/workflow-state-template.md)); перечень файлов: [`artifact-layout.md`](.cursor/skills/1c-full-cycle-dev/references/artifact-layout.md). По одним файлам нельзя надёжно отличить «артефакт записан» от «gate закрыт в чате» — правила и `ожидается_gate`: [`SKILL.md`](.cursor/skills/1c-full-cycle-dev/SKILL.md). Для точки внутри Phase 9 смотреть ещё **`tasks.md`** и **`phase9-context-index.md`**.

## Атрибуция

Воркфлоу модернизирован относительно идей [AndreevED/1c-ai-feature-dev-workflow](https://github.com/AndreevED/1c-ai-feature-dev-workflow); агент **`1c-code-explorer`** — изменённая линия того же проекта. Остальные роли (`1c-developer`, `1c-architect`, …) — ориентация на [comol/cursor_rules_1c](https://github.com/comol/cursor_rules_1c). Вызов в Cursor по полю **`name`** в frontmatter файлов агентов (например `1c-developer`, не обязательно совпадение имени файла с `developer.md`). Полная таблица «агент ↔ фаза» — в [`SKILL.md`](.cursor/skills/1c-full-cycle-dev/SKILL.md); навык **не** дублирует промпты агентов.

Отдельные роли можно вызывать вне конвейера (исследование, черновик PRD, точечная реализация) — смысл вызова задаёт пользователь; в полном цикле оркестратор следует [`SKILL.md`](.cursor/skills/1c-full-cycle-dev/SKILL.md).

## Кастомизация и сопровождение

Логику фаз, gate и Phase 9 менять в [`SKILL.md`](.cursor/skills/1c-full-cycle-dev/SKILL.md); шаблоны полей — в [`references/`](.cursor/skills/1c-full-cycle-dev/references/), в согласовании со [`SKILL.md`](.cursor/skills/1c-full-cycle-dev/SKILL.md). При смене фаз или путей шаблонов обновляйте этот README.

Лицензии сторонних репозиториев — в репозиториях **AndreevED/1c-ai-feature-dev-workflow** и **comol/cursor_rules_1c**.

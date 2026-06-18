# LiveProgTok — ТВ-лента как TikTok

**LiveProgTok** — веб-приложение в стиле TikTok для просмотра телепрограммы. Данные загружаются из публичных репозиториев через **jsDelivr CDN** (с поддержкой CORS), а в случае недоступности — через GitHub API.

## Особенности

- 📱 Полноэкранная вертикальная лента с каналами.
- 🔄 Автообновление каждые 3 часа.
- 🛡️ Резервные источники (3 репозитория) — автоматическое переключение.
- 📺 Воспроизведение потоков (HLS/MP4) прямо в карточке.
- ❤️ Лайки и шеринг.

## Источники данных

Приложение пытается загрузить `schedule.json` последовательно из трёх репозиториев:

1. `OinkTechLtd/liveprogramma`
2. `OinkTechLLC/liveprogramma`
3. `TwixoffLtdco/liveprogramma`

Сначала используется **jsDelivr CDN** (основной способ), затем **GitHub API** (резерв).

## Добавление своего источника

Измените массивы `SOURCES` и `API_SOURCES` в `index.html`:

```javascript
const SOURCES = [
    'https://cdn.jsdelivr.net/gh/ВАШ_НИК/РЕПО@ветка/путь/к/schedule.json',
    // ...
];
const API_SOURCES = [
    'https://api.github.com/repos/ВАШ_НИК/РЕПО/contents/путь/к/schedule.json',
    // ...
];

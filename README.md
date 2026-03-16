# glanceDashboard

Personal [Glance](https://github.com/glanceapp/glance) dashboard configuration — a modular YAML setup with pages for home, gaming, and 3D printing.

## Structure

```
glanceDashboard/
├── glance.yml          # Root config — includes page files
├── home.yml            # Home page layout and widgets
├── gaming.yml          # Gaming page layout and widgets
├── 3dprinting.yml      # 3D Printing page layout and widgets
├── game-tracker.yml    # Upcoming game releases widget (RSS)
├── epic-games.yml      # Epic Games free games widget (custom API)
├── steam.yml           # Steam specials/discounts widget (custom API)
└── spoolman.yml        # Filament spool tracker widget (Spoolman API)
```

## Pages

### Home
3-column layout (small / full / small)

- **Head:** Upcoming game releases (RSS from local game tracker service)
- **Left column:** Bookmarks (N6 bus timetable), Epic Games free games, Steam specials, filament spool tracker
- **Center column:** Docker containers, server stats
- **Right column:** DuckDuckGo search (with YouTube bang), calendar

### Gaming
3-column layout (small / full / small)

- **Left column:** Twitch top games (top 20, filters out non-game categories)
- **Center column:** Reddit posts from r/pcgaming and r/games, YouTube gaming channel videos (Gameranx, Skill Up, GameLinked, Digital Foundry)
- **Right column:** r/gamingnews (vertical cards)

### 3D Printing
3-column layout (small / full / small)

- **Left column:** Print queue todo list
- **Center column:** Reddit feeds — r/3Dprinting, r/FixMyPrint, r/resinprinting, r/functionalprint, r/3Dprintedminis
- **Right column:** Calendar

## Widget Files

| File | Type | Description |
|------|------|-------------|
| `game-tracker.yml` | RSS | Upcoming game releases from a local API (`192.168.1.252:8066`) |
| `epic-games.yml` | Custom API | Free games from the Epic Games Store (IE locale, 1h cache) |
| `steam.yml` | Custom API | Steam featured specials with discount highlighting (IE, 12h cache) |
| `spoolman.yml` | Custom API | Filament spool inventory from local Spoolman instance (`192.168.1.252:7912`) |

## Local Services

Some widgets depend on self-hosted services on the local network:

- **Game tracker** — `http://192.168.1.252:8066`
- **Spoolman** — `http://192.168.1.252:7912`
- **Docker / Server stats** — local host

## Usage

Point your Glance instance at `glance.yml` as the configuration file. Page files are pulled in via `$include` directives, so all files must be in the same directory (or adjust paths accordingly).

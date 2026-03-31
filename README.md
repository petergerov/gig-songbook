# Easy Songbook

A musician-focused iOS app for managing songs, building setlists, and performing live — with chord transposition built in.

## Free vs Pro

| Feature | Free | Pro |
|---|---|---|
| Song library (unlimited songs) | ✓ | ✓ |
| Manual song entry | ✓ | ✓ |
| Setlists | up to 7 | Unlimited |
| Setlist locking | ✓ | ✓ |
| Chord transposition | ✓ | ✓ |
| Performance mode | ✓ | ✓ |
| Appearance settings | ✓ | ✓ |
| Import songs (file / folder / JSON) | — | ✓ |
| Export songs & setlists (JSON) | — | ✓ |
| Chord tab diagrams | — | ✓ |

Pro is a one-time in-app purchase (`com.gerov.GigSongbook.pro`).

## Features

- **Song library** — store lyrics, chords, key, BPM, and performance notes
- **Lyrics fetch** — auto-fetch lyrics by artist and song title from `lyrics.ovh` and `lrclib.net`; user-initiated only, song title and artist are sent to these services
- **File import** *(Pro)* — import songs from `.md`, `.txt`, and `.pdf` files (single files, multiple selection, or entire folders)
- **Export / import** *(Pro)* — share your entire song library or individual setlists as JSON files; setlist exports embed all referenced songs so they are fully self-contained
- **Chord tab diagrams** *(Pro)* — interactive chord diagrams rendered entirely on-device (open position, A-shape and E-shape barre voicings); no network request required
- **Setlists** — organize songs into ordered setlists with date and venue info (up to 7 free, unlimited with Pro)
- **Setlist locking** — lock a setlist to prevent accidental changes during a gig; locked setlists cannot be deleted until unlocked
- **Song deletion protection** — songs used in a setlist require confirmation before deletion; the app shows which setlists are affected
- **Chord transposition** — transpose chords up/down live during performance, or set a fixed transposition per song in a setlist
- **Performance mode** — full-screen dark display with auto-hiding controls
- **Appearance settings** — choose font, size, and line spacing for lyrics

## Requirements

- iOS 17.0+
- Xcode 16.0+

## Project Structure

```
GigSongbook/
├── GigSongbookApp.swift
├── ProStore.swift              # StoreKit 2 IAP — free/pro entitlement
├── SongImporter.swift          # Parses .md / .txt / .pdf into Song objects
├── SongbookExporter.swift      # Creates JSON export payloads for songs and setlists
├── ActivityViewController.swift # presentShareSheet() — presents UIActivityViewController directly via UIKit
├── ChordTransposer.swift       # Detects chord lines and transposes them
├── ChordMapper.swift           # Chord shapes and diagram data
├── Models/
│   ├── Song.swift
│   ├── Setlist.swift
│   └── AppSettings.swift
├── ViewModels/
│   └── SongbookStore.swift     # Central state, UserDefaults persistence, JSON import
└── Views/
    ├── ContentView.swift       # Tab navigation
    ├── UpgradeView.swift       # Pro upgrade / paywall sheet
    ├── Songs/
    │   ├── SongsListView.swift
    │   └── SongEditorView.swift
    ├── Setlists/
    │   ├── SetlistsListView.swift
    │   ├── SetlistDetailView.swift
    │   └── SetlistEditorView.swift
    ├── Performance/
    │   ├── PerformanceView.swift
    │   ├── ChordChartPanel.swift
    │   ├── ChordDiagramView.swift
    │   ├── ChordVariationsSheet.swift
    │   └── LocalChordChart.swift
    └── Settings/
        └── SettingsView.swift
```

## Data Model

### Song

| Field    | Type     | Description                          |
|----------|----------|--------------------------------------|
| `id`     | UUID     | Unique identifier                    |
| `title`  | String   | Song title (required)                |
| `artist` | String   | Artist or band name                  |
| `lyrics` | String   | Full lyrics text, may contain chords |
| `key`    | String   | Musical key, e.g. `Am`, `G#`        |
| `bpm`    | Int?     | Tempo in beats per minute            |
| `notes`  | String   | Performance notes, chord diagrams    |

### Setlist

| Field                | Type              | Description                              |
|----------------------|-------------------|------------------------------------------|
| `id`                 | UUID              | Unique identifier                        |
| `name`               | String            | Setlist name                             |
| `date`               | Date?             | Optional gig date                        |
| `venue`              | String            | Venue name                               |
| `songIDs`            | [UUID]            | Ordered list of song references          |
| `isLocked`           | Bool              | Prevents editing when `true`             |
| `songTranspositions` | [String: Int]     | Per-song semitone offsets (UUID → steps) |

All data is stored in `UserDefaults` as JSON (keys `songs_v1`, `setlists_v1`, `settings_v1`).

## Export / Import

### Songs

In the **Songs** tab, tap **⊕** and choose:

- **Export All Songs** — writes all songs to `easysongbook-songs.json` and opens the share sheet (AirDrop, Files, Mail, etc.)
- **Import Songs (JSON)** — opens the file picker to select a previously exported `easysongbook-songs.json`; songs already in the library (matched by UUID) are skipped

### Setlists

In the **Setlists** tab, tap **⊙** and choose:

- **Export All Setlists** — writes all setlists and every song they reference to `easysongbook-setlists.json`
- **Import Setlist** — opens the file picker; accepts both single-setlist exports and multi-setlist exports. If the imported setlist name matches an existing one, you are asked to **Overwrite** it or **Keep Both** (imported as a new setlist with a numeric suffix, e.g. `Summer Tour 2`)

On an individual setlist, tap **⊙** in the toolbar and choose **Export Setlist** to share just that setlist as `<name>.easysongbook-setlist.json`.

### Export file format

All exports are pretty-printed JSON with ISO 8601 dates. Setlist exports embed the full song data, so a recipient does not need to have any of those songs already.

```json
// easysongbook-songs.json
{ "version": 1, "exportedAt": "...", "songs": [ ... ] }

// <name>.easysongbook-setlist.json
{ "version": 1, "exportedAt": "...", "setlist": { ... }, "songs": [ ... ] }

// easysongbook-setlists.json
{ "version": 1, "exportedAt": "...", "setlists": [ ... ], "songs": [ ... ] }
```

## File Import

Songs can be imported from `.md`, `.txt`, and `.pdf` files. Tap **+** → **Import from File** in the Songs tab to open the file picker. Multiple files and folders are supported — the app recursively processes all supported files in a selected folder.

### Supported formats

#### Markdown (`.md`) — YAML frontmatter

```markdown
---
title: Amazing Grace
artist: Traditional
key: G
bpm: 72
notes: Capo 2
---

Amazing grace! How sweet the sound
That saved a wretch like me...
```

Supported frontmatter keys: `title`, `artist` / `author`, `key`, `bpm` / `tempo`, `notes`.

#### Markdown (`.md`) — heading fallback

```markdown
# Amazing Grace

Amazing grace! How sweet the sound
That saved a wretch like me...
```

The first `# Heading` becomes the title; everything below is lyrics.

#### Plain text (`.txt`) — key/value header

```
Title: Amazing Grace
Artist: Traditional
Key: G
BPM: 72

Amazing grace! How sweet the sound
That saved a wretch like me...
```

Supported header keys (case-insensitive): `Title`, `Artist` / `Author` / `Band`, `Key`, `BPM` / `Tempo`, `Notes`. A blank line separates the header from the lyrics. If no header is found, the first line becomes the title.

#### PDF (`.pdf`)

Text is extracted via PDFKit and parsed using the same key/value header logic as `.txt`.

## Chord Transposition

Chords embedded in lyrics are detected and transposed automatically. A line is treated as a **chord line** when at least 60 % of its whitespace-separated tokens are valid chord symbols.

**Recognised chord syntax:**

```
[A-G][#b]?(maj|min|m|aug|dim|sus[24]?|add)?[0-9]*(/[A-G][#b]?)?
```

Examples: `G`, `Am`, `D7`, `Fmaj7`, `Gsus4`, `Cadd9`, `D/F#`, `Bb`, `Ebm7`.

Transposing up uses sharps (`F#`, `G#`…); transposing down uses flats (`Bb`, `Eb`…). Bass notes in slash chords (e.g. `G/B`) are transposed together with the root.

### During performance

The **− ♩ +** control at the bottom of Performance mode transposes all chord lines live. The lyrics are never modified — transposition is display-only.

### Per-song in a setlist (unlocked)

Each song row in a setlist shows a small `−  0  +` stepper. Set the transposition for each song before the gig; values are saved with the setlist.

### Locked setlists

When a setlist is locked (`lock` button in the toolbar), the saved transpositions are applied automatically in Performance mode and the `+`/`−` buttons are disabled (a `lock` icon is shown instead).

## Setlist Locking

Tap the **lock** icon in the top-right of a setlist to toggle the locked state.

| State      | Effect                                                         |
|------------|----------------------------------------------------------------|
| Unlocked   | Songs can be added, removed, and reordered; transpositions are editable |
| Locked     | All editing is disabled; saved transpositions are applied automatically in Performance mode |

A small lock icon appears next to the setlist name in the list view.

## Performance Mode

Tap **Start Performance** from a setlist, or **Perform This Song** from a song, to enter full-screen performance mode.

- **Tap** anywhere to show/hide controls (auto-hide after 4 s)
- **Swipe left/right** — use the prev/next arrows to move between songs in a setlist
- **Transpose** — `−` / `+` buttons adjust transposition live; resets to the saved value when switching songs
- **Locked** — transpose is read-only when the setlist is locked

## Upgrade to Pro

Free users see a **Pro** banner in Settings and lock icons on gated actions (import, export, chord tabs). Tapping any locked feature opens the upgrade sheet. The upgrade is a one-time in-app purchase — no subscription.

Purchases can be restored at any time from the upgrade sheet or Settings.

## Settings

| Setting          | Default     | Range / Options                              |
|------------------|-------------|----------------------------------------------|
| Font             | Menlo       | Courier New, Menlo, SF Mono, Monaco, Courier, American Typewriter |
| Font size        | 18 pt       | 12 – 36 pt                                   |
| Line spacing     | 6 pt        | 0 – 20 pt                                    |
| Keep screen on   | On          | Disables auto-lock during performance        |

Changes are saved immediately and a live preview is shown in the Settings tab.

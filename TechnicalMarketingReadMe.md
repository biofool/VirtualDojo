# Technical Marketing Summary — VirtualDojo

## One-Line Positioning

A Go-based utility for updating YouTube video metadata via the YouTube Data API, designed for managing martial arts educational content on YouTube.

## Target Users / Personas

- **Martial arts instructors** managing YouTube channels with educational content (virtual dojo)
- **Content managers** needing to bulk-update YouTube video categories and metadata
- **Developers** building YouTube content management tools in Go

## Key Features (Grounded in Code)

- **YouTube video metadata update** — uses YouTube Data API v3 `Videos.Update` to modify title, description, and category (`YoutubeRenamer`)
- **Education category assignment** — sets video category ID to "27" (Education) (`YoutubeRenamer`)
- **OAuth 2.0 authentication** — uses `youtube.YoutubeForceSslScope` for secure API access (`YoutubeRenamer`)
- **Preserves existing title** — reads the current video title and re-applies it (useful for category-only updates) (`YoutubeRenamer`)

## Technical Differentiators

- **Go + YouTube API** — lightweight, compiled utility for YouTube metadata management
- **Education-focused** — defaults to the Education category, suited for instructional/educational content
- **Minimal footprint** — single-file Go snippet with no external dependencies beyond the Google API client

## Use Cases

- Recategorizing martial arts training videos as "Education" on YouTube
- Updating video descriptions and titles programmatically
- Building automated YouTube channel management workflows for educational content

## Benefits / Value Proposition

- Automates YouTube video metadata updates that would otherwise require manual editing in YouTube Studio
- Go's compiled binary is easily deployable and fast
- OAuth 2.0 ensures secure, scoped API access

## Tech Stack

- **Language**: Go (Golang)
- **API**: Google YouTube Data API v3 (`google.golang.org/api/youtube/v3`)
- **Auth**: OAuth 2.0 (`YoutubeForceSslScope`)
- **License**: CC0 1.0 Universal (Public Domain)

## Known Limitations

- **Incomplete code** — the `getClient()` function is referenced but not implemented; OAuth 2.0 client creation must be added
- **Hardcoded video ID** — `videoID` is set to `"someid"` (placeholder); no CLI argument or config file support
- **No Go module** — missing `go.mod` and `go.sum`; not a buildable Go module as-is
- **Single video only** — updates one video at a time; no batch processing
- **Title set to existing title** — the update sets title and description to the existing title, which may overwrite the description unintentionally
- **No error recovery** — uses `log.Fatalf` for all errors, terminating immediately on failure

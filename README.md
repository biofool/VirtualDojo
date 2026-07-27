# VirtualDojo

A placeholder repository containing a YouTube video renamer utility written in Go, along with a CC0 license. The project appears to be related to managing YouTube content for a virtual dojo (martial arts training) context.

## Overview

The repository contains a Go source file (`YoutubeRenamer`) that uses the Google YouTube API to update video metadata (title, description, category) for a specified video ID. The project is in an early/prototype stage — the `YoutubeRenamer` file is a standalone Go snippet, not a complete module.

## Prerequisites

- [Go](https://go.dev/dl/) (v1.11+)
- Google Cloud project with YouTube Data API v3 enabled
- OAuth 2.0 credentials (client ID and secret) for the YouTube API
- `google.golang.org/api/youtube/v3` Go package

## Setup

1. Clone the repository:
   ```bash
   git clone https://github.com/biofool/VirtualDojo.git
   cd VirtualDojo
   ```

2. Enable the YouTube Data API v3 in your Google Cloud project.

3. Create OAuth 2.0 credentials and download the client secret JSON file.

4. The `YoutubeRenamer` file references a `getClient()` function (not included) — you will need to implement OAuth 2.0 client creation using `golang.org/x/oauth2` and the YouTube API scope `youtube.YoutubeForceSslScope`.

## How to Run

The `YoutubeRenamer` file is a Go source snippet. To use it:

1. Place it in a Go module directory:
   ```bash
   go mod init virtualdojo
   go get google.golang.org/api/youtube/v3
   ```

2. Implement the `getClient()` function for OAuth 2.0 authentication.

3. Set the `videoID` variable to the target YouTube video ID.

4. Run:
   ```bash
   go run YoutubeRenamer
   ```

The script updates the video's title and description (set to the existing title) and changes the category to "27" (Education).

## Project Structure

```
VirtualDojo/
├── README.md          # This file
├── YoutubeRenamer     # Go source — YouTube video metadata updater
└── LICENSE            # CC0 1.0 Universal (Public Domain)
```

## Key Features

- YouTube video metadata update via YouTube Data API v3
- Sets video category to Education (category ID "27")
- Uses OAuth 2.0 with `YoutubeForceSslScope` for authentication

# forum-dev-server

Dev server for the forum project. Connects forum-app and forum-api via a reverse proxy and provides scripts to up/down the full stack.

## Prerequisites

1. SSH access to GitHub (for cloning repos)
2. Docker running

## Setup

1. Clone this repo:
   ```sh
   gh repo clone 420Cry/forum-server ~/projects/forum/forum-server
   cd ~/projects/forum/forum-server
   ```

2. Create config:
   ```sh
   cp config.ini.example config.ini
   # Edit config.ini: set PROJECTS_DIRECTORY, GITHUB_ORG
   ```

3. Install CLI alias:
   ```sh
   ./bin/forum install:script
   source ~/.zshrc  # or ~/.bashrc
   ```

4. Clone forum repos:
   ```sh
   forum install:clone
   ```

5. Start everything:
   ```sh
   forum up
   ```

## Commands

| Command | Description |
|---------|-------------|
| `forum up` | Start proxy + all forum projects |
| `forum down` | Stop all projects + proxy |
| `forum install:clone` | Clone forum-api, forum-app repos |
| `forum install:script` | Add `forum` alias to shell |

## URLs (with proxy)

Add to `/etc/hosts`:

```
127.0.0.1 app.forum.test
127.0.0.1 api.forum.test
```

- **App:** http://app.forum.test
- **API:** http://api.forum.test

## Ports

- 80 – Proxy (nginx)
- 3000 – forum-app (direct)
- 3001 – forum-api (direct)

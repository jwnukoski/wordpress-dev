# WordPress Docker Environment
Basic template for working in WordPress with Docker.

## Setup
1. Copy `.env.example` to `.env`. Modify as needed.
2. Run `docker compose build && docker compose up -d`
3. Run `sudo chown -R [your local user]` to gain ownership of files you want to work on.

## TODO
- Add Xdebug by default.
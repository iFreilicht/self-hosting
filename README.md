# self-hosting

Files for setting up my self-hosted infrastructure

## Prepare

1. Run `cp .env.sample .env`
2. Fill in the `.env` file. The exact values don't matter, but the passwords should be long and randomized
3. Run `crontab self-hosting.cron` to install the required cronjobs

## Start

Run `docker-compose up -d`

## Initial steps

In Nextcloud, you will need to create a user account. This is done automatically when you first visit its URL.
After that, go to `Settings` -> `Administration` -> `Basic Settings` and set `Background jobs` to `Cron`.

## Stop

Run `docker-compose down`
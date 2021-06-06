# self-hosting

Files for setting up my self-hosted infrastructure

## Prepare

1. Run `cp .env.sample .env`
2. Fill in the `.env` file. The exact values don't matter, but the passwords should be long and randomized
3. The next steps should be executed in a root terminal
4. Generate an ssh key without passphrase in /root/.ssh/. This will be used for automated actions. `ssh-keygen -o -a 100 -t ed25519`
5. Create two remote borg repositories with the key you just created, and initialize them `borg init -e repokey-blake2 <ID>@<ID>.repo.borgbase.com:repo`
6. When asked for a passphrase, use the same for both. Make sure to store it somewhere safe and edit `BORG_PASSPHRASE` in `.env`.
7. Back up the borg key for both repos and store it somewhere safe! `borg key export <ID>@<ID>.repo.borgbase.com:repo ~/borg-key`

## Start

Run `docker-compose up -d`

## Initial steps

In Nextcloud, you will need to create a user account. This is done automatically when you first visit its URL.
After that, go to `Settings` -> `Administration` -> `Basic Settings` and set `Background jobs` to `Cron`.

## Stop

Run `docker-compose down`
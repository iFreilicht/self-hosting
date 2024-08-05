# self-hosting

These were the files for setting up my self-hosted infrastructure on a Hetzner CX22 VPS.
It's based entirely on docker-compose, which makes it very simple to set up and monitor.

This repo is no longer used, as I've now migrated everything to a NixOS machine in my basement, but I
thought it might be interesting to see for others how something like this can be set up.

You can see an overview of all services in `docker-compose.yml`. It includes a self-configuring reverse proxy
with nginx, monitoring with portainer, and backups with borgmatic.

## Prepare

1. Run `cp .env.sample .env`
2. Fill in the `.env` file. The exact values don't matter, but the passwords should be long and randomized
3. The next steps should be executed in a root terminal
4. Generate an ssh key without passphrase in /root/.ssh/. This will be used for automated actions. `ssh-keygen -o -a 100 -t ed25519`
5. Create two remote borg repositories with the key you just created, and initialize them `borg init -e repokey-blake2 <ID>@<ID>.repo.borgbase.com:repo`
6. When asked for a passphrase, use the same for both. Make sure to store it somewhere safe and edit `BORG_PASSPHRASE` in `.env`.
7. Back up the borg key for both repos and store it somewhere safe! `borg key export <ID>@<ID>.repo.borgbase.com:repo ~/borg-key`
8. Symlink the files in the etc/ directory or copy them to their destination

## Start

Run `docker-compose up -d`

## Initial steps

In Nextcloud, you will need to create a user account. This is done automatically when you first visit its URL.
After that, go to `Settings` -> `Administration` -> `Basic Settings` and set `Background jobs` to `Cron`.

## Stop

Run `docker-compose down`

## Final note

server1 was active from May 2021 to August 2024. It was a good time.
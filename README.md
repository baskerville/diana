![diana](https://github.com/baskerville/diana/raw/master/logo/diana-logo.jpg)

## Usage

    dad [-h|-d DOWNLOAD_DIR|-s SECRET_TOKEN|-u USERNAME|-p PASSWORD] start|stop
    diana [-h|-u USERNAME|-p PASSWORD] ACTION [ARGUMENTS]

## Actions

- `list` — Output the list of active downloads.

- `paused` — Output the list of paused downloads.

- `stopped` — Output the list of stopped downloads.

- `info [--select-file=...] GID ...` — Output informations regarding the given GIDs.

- `files GID ...` — Output the files owned by the downloads corresponding to the given GIDs.

- `errors` — Output the list of errors.

- `stats` — Output download bandwidth statistics.

- `add [--select-file=...] ITEM ...` — Download the given items (local or remote URLs to torrents, etc.).

- `remove GID ...` — Remove the downloads corresponding to the given GIDs.

- `forcerm GID ...` — Forcibly remove the downloads corresponding to the given GIDs.

- `pause GID ...` — Pause the downloads corresponding to the given GIDs.

- `resume GID ...` — Resume the downloads corresponding to the given GIDs.

- `preview [--select-file=...] GID ...` — Preview all the files from all the downloads corresponding to the given GIDs.

- `sleep` — Pause all the active downloads.

- `wake` — Resume all the paused downloads.

- `purge` — Clear the list of stopped downloads and errors.

- `clean` — Stop seeding completed downloads.

## Environment Variables

- `DIANA_DOWNLOAD_DIR` — Used by the daemon.
- `DIANA_PREVIEW_COMMAND` — Command used to preview files.
- `DIANA_INFO_COMMAND` — Command used to get file informations.
- `DIANA_SECRET_TOKEN` — Secret RPC authorization token.

All commands receive the partial file as first argument.

## Dependencies

- aria2
- python3

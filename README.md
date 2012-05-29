![diana] (https://github.com/baskerville/diana/raw/master/preview/diana_logo.jpg)

    SYNOPSIS
        diana <action> [arguments]

    ACTIONS 
        list
            Show the list of active downloads.

        paused
            Show the list of paused downloads.

        stopped
            Show the list of stopped downloads.

        errors
            Show the list of encountered errors.

        stats
            Show download bandwidth statistics.

        sleep
            Pause all the active downloads.

        wake
            Resume all the paused downloads.

        purge
            Clear the list of stopped downloads and errors.

        clean
            Stop seeding completed downloads.

        kill
            Kill the daemon.

        add [--select-file=...] ITEM ...
            Download the given items (local or remote URLs to torrents, etc.).

        remove GID ...
            Remove the downloads corresponding to the given GIDs.

        forcerm GID ...
            Forcibly remove the downloads corresponding to the given GIDs.

        pause GID ...
            Pause the downloads corresponding to the given GIDs.

        resume GID ...
            Resume the downloads corresponding to the given GIDs.

        files GID ...
            Show the files owned by the downloads corresponding to the given GIDs.

        info [--select-file=...] GID ...
            Retrieve informations regarding the given GIDs.

        preview [--select-file=...] GID ...
            Preview all the files from all the downloads corresponding to the given GIDs.


## Prerequisites

First launch the daemon which is called `dad`.

## Get the File Indexes

This function might help:

    tl () {
            aria2c -S "$@" | grep '\./'
    }


## Dependencies

`aria2` and `python3`.

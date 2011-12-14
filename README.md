# diana -- a command line interface to the aria2 daemon

![diana] (http://blobs.ge.tt/4EcnB8B/diana_logo.jpg?sig=-TQ_lRNcPBf2hwtGiv9yTx-ewBtDcsn8fgY)

## Get Started

To get the list of available actions just call **diana** without parameters.

The daemon script is called **dad**.

**diana** is written in Python and uses the JSON RPC interface to communicate with the **aria2** daemon.

## Advanced Usage

If you want to download only certain files inside a torrent :

- Get the index of the relevant files with **tl**:

    tl () {
            aria2c -S "$@" | grep '\./'
    }

- Call **diana** with the appropriate option (see the manual for **aria2c** and search for **--select-file**):

    diana --select-file=foo add bar.torrent

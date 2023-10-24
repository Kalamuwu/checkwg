# checkwg
A simple wg-quick wrapper script and systemd service to connect to and manage wg connections.

```
$ checkwg -h
checkwg: attempts to connect to vpn, and checks connection status afterward.
Usage: checkwg [-fhiqQrs] [-c NUM]

    -c <NUM>  Number of times to attempt reconnection if final check fails.
              Defaults to 3. Negative values will attempt infinitely.

    -f        Skip final connection check

    -h        Display this message

    -i        Skip initial wg check, force new connection. This can be dangerous
              if a connection is already found.

    -q        Quiet output, but show important status messages (implies -s)

    -Q        Quiet output, do not output anything (implies -q)

    -r        Reconnect. Disconnects existing connection and then connects
              normally.

    -s        Quiet subcommands. Show status messages, but not anything from wg
              or other subcommands
```

## Usage

Download file `checkwg`, make executable, and edit the line `INTERFACE="interface"` to match the wg config in `/etc/wireguard/`.
To enable automatically connecting to this Wireguard interface at boot, download file `startwg.service`, and edit the command to point to the correct path to the `checkwg` script you just downloaded. Save and enable the service.

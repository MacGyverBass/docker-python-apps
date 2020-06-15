# Docker Images of Various Python Applications

This is a repository with various applications written in Python and installed in Docker.

## List of Python Applications with Sources

- `catt` - Cast All The Things: Allows you to send local/online videos or webpages to your Chromecast.  [GitHub](https://github.com/skorokithakis/catt)
- `icdiff` - Improved colored diff.  [GitHub](https://github.com/jeffkaufman/icdiff)
- `jc` - JSONifies the output of many CLI tools and file-types for easier parsing in scripts.  [GitHub](https://github.com/kellyjonbrazil/jc)
- `speedtest-cli` - Command line interface for testing internet bandwidth using speedtest.net servers.  [GitHub](https://github.com/sivel/speedtest-cli)
- `stig` - TUI and CLI for the BitTorrent client Transmission.  [GitHub](https://github.com/rndusr/stig)
- `tremc` - Console client for the BitTorrent client Transmission.  [GitHub](https://github.com/tremc/tremc)
- `we-get` - Command-line tool for searching torrents.  [GitHub](https://github.com/rachmadaniHaryono/we-get)

## Examples of Use

Below are various examples for the above applications.  I will try to keep this list updated as more items are added.

The following example runs `catt` with the command argument `scan` on the `host` network.  You can also use a `macvlan` for this, as long as it is on the same network as your Chromecast devices.

```sh
docker run --rm -it \
 --network=host \
 macgyverbass/catt \
 scan
```

The following example runs `icdiff` with the current path bind-mounted (as read-only in this example) and with the files `before.txt` and `after.txt` being compared.

```sh
docker run --rm -it \
 -v "${PWD}":"${PWD}":ro -w "${PWD}" \
 macgyverbass/icdiff \
 "before.txt" "after.txt"
```

The following example pipes the output of `ls -l` into `jc` with the argument `--ls` and it will return JSON text, which then can be piped into `jq` or another application needing JSON input.  Note that in this example, the `-i` arugment for `docker run` is omitted, as `-i` will prevent the Docker entrypoint from receiving the piped data.

```sh
ls -l | docker run --rm -t \
 macgyverbass/jc \
 --ls
```

The following example runs `speedtest-cli` using the `--secure` argument.  Note that `speedtest-cli` also runs without any arguments passed to it.

```sh
docker run --rm -it \
 macgyverbass/speedtest-cli \
 --secure
```

The following example runs `stig` on the host `192.168.0.80` on port `9095`.  Note that your IP/port will depend on your Transmission server setup.  Remember to review the documentation on the official website for more details using this executable.

```sh
docker run --rm -it \
 macgyverbass/stig \
 set connect.host 192.168.1.0 \; set connect.port 9091 \;
```

The following example runs `tremc` on the host `192.168.0.80` on port `9095`.  Note that your IP/port will depend on your Transmission server setup.  Remember to review the documentation on the official website for more details using this executable.

```sh
docker run --rm -it \
 macgyverbass/tremc \
 --connect 192.168.0.80:9095
```

The followinig example runs `we-get` with the search term "linux" and with the output in JSON using the `-J` switch.

```sh
docker run --rm -it \
 macgyverbass/we-get \
 --search "linux" -J
```

Your uses will differ from the above examples, but they can be used as a guide for running them on your system.

# フォーク版の変更点など

* forked from [mtkhs/radicast](https://github.com/mtkhs/radicast)
* partial keyの取得方法の変更に伴う修正版。
* DockerイメージをArm64化

# radicast

* record radiko
* serve rss for podcast

## REQUIRE

* rtmpdump
* swftools
* ffmpeg or avconv
* or docker (see docker section)

## INSTALL

```
$ go get github.com/tkhs/radicast
```

## USAGE

### SETUP CONFIG.JSON

```
$ radicast --setup > config.json
```

### EDIT CONFIG.JSON

```
$ vim config.json
$ cat config.json

{
  "FMT": [
    "0 0 17 * * *"
  ]
}
```

cron specification is [here](https://godoc.org/github.com/robfig/cron#hdr-CRON_Expression_Format)

### LAUNCH

```
$ radicast
$ curl 127.0.0.1:3355/rss # podcast rss
```

### RELOAD CONFIG.JSON

* reload config when receive HUP signal

## DOCKER

```
$ mkdir workspace
$ cd workspace
$ docker pull mtkhs/radicast
$ docker run --rm mtkhs/radicast:latest --setup > config.json
$ docker run --rm -p 3355:3355 -v `pwd`:/workspace mtkhs/radicast:latest --config /workspace/config.json --output /workspace/output
```

* [docker-hub](https://hub.docker.com/r/mtkhs/radicast/)

## SEE ALSO

* [ripdiko](https://github.com/miyagawa/ripdiko)

## LICENSE

* MIT

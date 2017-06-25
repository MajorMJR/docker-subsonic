
This repository contains configuration files for building a
Docker (http://docker.io) image for the Subsonic media streamer.

This container is modified slightly from https://github.com/mschuerig/subsonic-docker-image in order to support Docker automated builds.

## Noteworthy

* Subsonic 6.1 (http://www.subsonic.org)
* Debian/Jessie
* Runs as user subsonic (UID 10000)

## Build your own image

```shell
$ docker build -t <your-name>/debian-subsonic debian-subsonic
```

## Get a pre-built image

A current image is available as a trusted build from the Docker index:

```shell
$ docker pull  majormjr/debian-subsonic
```

## Run a container with this image

```shell
$ docker run \
  --detach \
  --publish 4040:4040 \
  --volume "/wherever/your/music/is:/var/music:ro" \
  <your-name>/debian-subsonic

```

## Pitfalls

The host music directory mounted into the container at /var/music must be
readable by user subsonic (UID 10000).

If you use a volume for the container's /var/subsonic, the host directory
mounted there must have read-write-execute permissions for user
subsonic (UID 10000).

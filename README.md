# qbt-nox-accel
[![Release Status](https://github.com/whoisnian/qbt-nox-accel/actions/workflows/release.yml/badge.svg)](https://github.com/whoisnian/qbt-nox-accel/actions/workflows/release.yml)
[![Release Version](https://img.shields.io/github/v/tag/whoisnian/qbt-nox-accel?logo=docker&filter=v*&label=version)](https://github.com/whoisnian/qbt-nox-accel/pkgs/container/qbt-nox-accel)

Download torrent content file from qBittorrent WebUI via Nginx X-Accel-Redirect.

## Usage
Use external nginx or run qbt-nox-accel using docker compose. You can run the docker compose example from this repository:
```sh
cd example
mkdir ./config ./downloads
docker compose up
# Visit the nginx listening addr http://127.0.0.1:8080 in your web browser.
# WebUI default username is admin. A temporary password is generated and printed at startup.
```

## Reference
* [qBittorrent-nox docker image](https://github.com/qbittorrent/docker-qbittorrent-nox)
* [qBittorrent source code](https://github.com/qbittorrent/qBittorrent)
* [Issue #2843: Download a file from the webui](https://github.com/qbittorrent/qBittorrent/issues/2843)
* [Wiki: NGINX Reverse Proxy for Web UI](https://github.com/qbittorrent/qBittorrent/wiki/NGINX-Reverse-Proxy-for-Web-UI)

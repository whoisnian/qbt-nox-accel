# qbt-nox-accel
[![Release Status](https://github.com/whoisnian/qbt-nox-accel/actions/workflows/release.yml/badge.svg)](https://github.com/whoisnian/qbt-nox-accel/actions/workflows/release.yml)
[![Release Version](https://img.shields.io/github/v/tag/whoisnian/qbt-nox-accel?logo=docker&filter=v*&label=version)](https://github.com/whoisnian/qbt-nox-accel/pkgs/container/qbt-nox-accel)

Download torrent content file from qBittorrent WebUI via Nginx X-Accel-Redirect.

## How it works
This repo applies two patches to the qBittorrent source code:
1. **Add a "Download" button to the WebUI:** This patch adds a new API endpoint that, when called, returns an `X-Accel-Redirect` header containing the path to the requested file.
2. **Add `--webui-addr` command-line option:** This patch allows binding the WebUI to a specific address, which is necessary for qBittorrent to only listen on local address.

When you click the "Download" button in the context menu of Content panel, the WebUI sends a request to the qBittorrent API. The API then tells Nginx to send the file directly to you.

## Usage
Use external nginx or run qbt-nox-accel using docker compose. You can run the docker compose example from this repository:
```sh
git clone https://github.com/whoisnian/qbt-nox-accel.git
cd qbt-nox-accel/example

mkdir ./config ./downloads
docker compose up
```
Visit the nginx listening addr http://127.0.0.1:8080 in your web browser.  
WebUI default username is `admin`, and a temporary password will be printed to the console at startup.

## Development
1. Clone the qBittorrent repository outside of this repository directory.  
   `git clone https://github.com/qbittorrent/qBittorrent.git && cd qBittorrent`
2. Checkout the desired qBittorrent tag as base version.  
   `git checkout release-X.Y.Z`
3. Apply the qbt-nox-accel patches.  
   `git am ../qbt-nox-accel/patches/*.patch`
4. Make your changes and commit them in qBittorrent repository.  
5. Generate new qbt-nox-accel patch files.  
   `git format-patch release-X.Y.Z -o ../qbt-nox-accel/patches`

## Reference
* [qBittorrent-nox docker image](https://github.com/qbittorrent/docker-qbittorrent-nox)
* [qBittorrent source code](https://github.com/qbittorrent/qBittorrent)
* [Issue #2843: Download a file from the webui](https://github.com/qbittorrent/qBittorrent/issues/2843)
* [Wiki: NGINX Reverse Proxy for Web UI](https://github.com/qbittorrent/qBittorrent/wiki/NGINX-Reverse-Proxy-for-Web-UI)

[![Stand With Ukraine](https://raw.githubusercontent.com/vshymanskyy/StandWithUkraine/main/badges/StandWithUkraine.svg)](https://stand-with-ukraine.pp.ua)

[![Stand With Ukraine](https://raw.githubusercontent.com/vshymanskyy/StandWithUkraine/main/banner2-direct.svg)](https://stand-with-ukraine.pp.ua)

# StorjScriptableWidgetExporter

![stars](https://img.shields.io/github/stars/dusselmann/storjScriptableWidgetExporter) ![last_commit](https://img.shields.io/github/last-commit/dusselmann/storjScriptableWidgetExporter)

<img src="https://github.com/dusselmann/storjScriptableWidget/blob/main/screenshot.jpeg?raw=true" alt="" width=340 align="right"/> 

This is a fork of [StorjWidgetExporter](https://github.com/striker43/storjWidget-Exporter) with minor modifications: it just adds trash disk space to the disk space calculation to show a more accurate space used.

StorjScriptableWidgetExporter starts a python Flask server which pulls information from storj node api for `node`, `satellite` and `payout` metrics and aggregates the data. The endpoint is returning the total `ingress` and `egress` over all nodes, the `estimated daily earnings` and the `current months earnings`, `total space used` and `total space available`, `total number of queried nodes` and `online count of queried nodes`.

The Exporter's endpoint will be available at http://localhost:3123/bandwidth

Tested with storj node version `1.84.1`

## Usage

* StorjWidget-Exporter can be installed as a docker container or run as a standalone script
* Make sure you have `-p 127.0.0.1:14002:14002` in your storagenode container docker run command to allow local connections to your node's api

### Installation

    docker volume create --name snwidget
    git clone https://github.com/dusselmann/storjScriptableWidgetExporter
    cd storjScriptableWidgetExporter/
    sudo docker build -t storjwidget .
    docker run -d --restart always --privileged -p 3123:3123 -e NODES_LIST=192.168.188.59:14002,myNodesIp.com:14002 -v storjWidgetVolume:/var/www/storjWidgetVolume --name snwidget storjwidget

## Next Steps:
When your storjWidget-Exporter is up, running and returning stats of your node(s) at http://localhost:3123/bandwidth, you can continue and set up your [storjScriptableWidget](https://github.com/dusselmann/storjScriptableWidget).

## contributing

[issues](https://github.com/dusselmann/storjScriptableWidgetExporter/issues) and [pull requests](https://github.com/dusselmann/storjScriptableWidgetExporter/pulls) are welcome. for major changes, please open an [issue](https://github.com/dusselmann/storjScriptableWidgetExporter/issues) first to discuss what you would like to change.

if you want to contact me directly, feel free to do so via discord: https://discordapp.com/users/371404709262786561

## license

[Apache-2.0](https://github.com/dusselmann/storjScriptableWidget/blob/main/LICENSE)

# Tegola & OpenMaptiles
## About

This project is aiming to enable the tegola vector tile server to support
serving tiles using the OpenMapTiles schema.

## Installation
### Requirements

* docker
* docker-compose
* tegola

### Quickstart
#### Init

Fetch git submodules:

```bash
git submodule update --init
```

#### Configure tegola server

To generate the tegola config:

```bash
$ git clone https://github.com/johngian/openmaptiles-tegola.git
$ cd vendor/openmaptiles
$ make start-db
$ make list-geofabrik      # List all areas available to download
$ make download area=planet   # Planet takes long time to load. Use a different area for dev purposes 
$ make import-osm
$ make import-borders
$ make import-wikidata
$ make build-tegola-config
$ cat build/tegola.toml
```

#### Start tegola server

To start the tegola server:

```bash
$ cd vendor/openmaptiles
$ make start-tegola
```

## Notes

* Currently the setup is relying on the following forks
  * [johngian/openmaptiles-tools@tegola-config](https://github.com/johngian/openmaptiles-tools/tree/tegola-config)
  * [johngian/openmaptiles@tegola-support](https://github.com/johngian/openmaptiles/tree/tegola-support)
  * [johngian/tegola@mvt-fixes](https://github.com/johngian/tegola/tree/mvt-fixes)
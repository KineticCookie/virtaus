# Virtaus

## How to build stuff

### finland-osm

1. Download the `finland-latest.osm.pbf` file from https://download.geofabrik.de/europe/finland.html and put it to the `data` folder. (result: `finland-osm/data/finland-latest.osm.pbf`)
2. Run `docker build -t kineticcookie/virtaus-finland-osm .`

### Backend

1. `sbt docker` builds the image.

### Navigation service

1. Run `docker build -t kineticcookie/virtaus-nav-service .`

### Frontend

1. Run `docker build -t kineticcookie/virtaus-frontend .`

### Proxy

1. Run `docker build -t kineticcookie/virtaus-proxy .`

## How to deploy stuff

1. Make sure that you have k8s cluster.
2. Recommended: create new namespace
3. `kubectl apply -f k8s/ --namespace ${NAMESPACE}`
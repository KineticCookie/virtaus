FROM osrm/osrm-backend AS extractor
ADD https://download.geofabrik.de/europe/finland-latest.osm.pbf /data/finland-latest.osm.pbf
RUN osrm-extract -p /opt/car.lua /data/finland-latest.osm.pbf

FROM osrm/osrm-backend AS partitioner
COPY --from=extractor /data /data
RUN osrm-partition /data/finland-latest.osrm

FROM osrm/osrm-backend AS customizer
COPY --from=partitioner /data /data
RUN osrm-customize /data/finland-latest.osrm

FROM osrm/osrm-backend
COPY --from=customizer /data /data
ENTRYPOINT osrm-routed --algorithm mld /data/finland-latest.osrm

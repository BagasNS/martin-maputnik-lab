# Martin Vector Tile Stack (Educational)

This project runs an educational vector-tile stack with PostGIS, Martin, and Maputnik. It is intended for local learning and experimentation only.

## What’s inside
- `docker-compose.yml` — orchestrates PostGIS, Martin (tile server), and Maputnik (style editor) with direct host ports exposed.
- `data/pgdata/` — PostGIS data volume (persisted locally).

## Prerequisites
- Docker and Docker Compose installed.
- Ports `3000`, `3001`, and `5432` available on your host (adjust in `docker-compose.yml` if needed).

## Quick start
```bash
docker-compose up -d
```

Access directly (no reverse proxy):
- Maputnik: http://localhost:3001/
- Martin tiles: http://localhost:3000/tiles.json
- PostGIS: host `localhost`, port `5432`, db `spatial_data`, user `postgis_admin`, password `postgis_admin`

Stop and clean up:
```bash
docker-compose down
```

## Notes
- Martin uses the PostGIS connection string `postgres://postgis_admin:postgis_admin@postgis/spatial_data`.
- Point Maputnik at the Martin tile JSON: `http://localhost:3000/catalog/[LAYER_NAME]`.
- For production or internet exposure, add proper security hardening (TLS, auth, restricted credentials). This setup is for educational use only.

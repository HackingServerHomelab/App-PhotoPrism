# App-PhotoPrism

## First Time Prerequisites

1. `rm ./Data/mysql/.gitkeep`
2. `chown 1000:1000 ./Data/photoprism`
2. Run [Traefik](https://github.com/mattlombana/App-Traefik)

## Running the Containers

1. Update the following volumes in [docker-compose.yml](./Docker/docker-compose.yml)
    * `"../Data/mysql:/var/lib/mysql"`
    * `"../Data/photoprism:/photoprism/storage" # settings, index, and sidecar files`
    * `"../Data/pictures:/photoprism/originals" # Photo & Video Collection`
    * `"../Data/Family:/photoprism/originals/Family"`
    * `"../Data/Friends:/photoprism/originals/Friends`"
    * `"../Data/import:/photoprism/import"`
2. Update the following environment variables in [docker-compose.yml](./Docker/docker-compose.yml)
    * `MYSQL_ROOT_PASSWORD: changeme`
    * `MYSQL_PASSWORD: changeme`
    * `PHOTOPRISM_ADMIN_PASSWORD: "changeme"`
    * `PHOTOPRISM_SITE_URL: "https://localhost"  # Canonical / public site URL`
    * `PHOTOPRISM_DATABASE_DSN: "photoprism:changeme@tcp(mariadb:3306)/photoprism?charset=utf8mb4,utf8&parseTime=true"`
3. Update the Traefik host label in [docker-compose.yml](./Docker/docker-compose.yml)
    * ``"traefik.http.routers.photoprism.rule=Host(`localhost`)"``
4. Run `docker-compose -f ./Docker/docker-compose.yml up -d`

## First Time Setup

1. Visit <https://your-ip>
2. Log in as `admin` with the `PHOTOPRISM_ADMIN_PASSWORD` password you set.

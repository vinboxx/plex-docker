# Plex Docker Setup
This project sets up a Plex Media Server using Docker Compose for macOS ARM-based machines like those with Apple Silicon (M1, M2). The configuration runs the `plexinc/pms-docker` image with customizable paths and environment settings.

## Prerequisites
- Docker Desktop installed on macOS.

## Project Structure
If you have created a folder named `plex-docker` in your home directory (`/Users/john`), the project structure should look like this:
```
/Users/john/plex-docker/
    ├── docker-compose.yml
    ├── .env
    ├── config/        # Plex configuration files (created after first run)
    ├── transcode/     # Temporary transcode files
    └── media/         # Your media library
        ├── Movies/
        ├── TV_Shows/
        └── Music/
```

## Running the Plex Container
1. Ensure Docker Desktop is running.
2. Run the following command to start the Plex container:
    ```sh
    docker compose up -d
    ```
3. Access the Plex web interface at `http://localhost:32400`.

## Stopping the Plex Container
To stop the Plex container, run:
```sh
docker compose down
```

## Updating the Plex Container
To update all images, run:
```sh
docker compose pull
docker compose up -d
```

## Troubleshooting
- If you cannot access the Plex web interface, use bridge networking instead of host networking in the `docker-compose.yml` file. Also add ports `32400:32400` to the `ports` section. After setup successfully, you can revert back to host networking so that Plex app can discover the server and play media directly.

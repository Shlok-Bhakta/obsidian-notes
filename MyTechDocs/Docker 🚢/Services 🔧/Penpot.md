[Github](https://github.com/penpot/penpot)

An alternative to Figma... deez nu

```yaml
---
version: "3.5"
networks:
  penpot:
services:
  penpot-frontend:
    image: "penpotapp/frontend:latest"
    restart: always
    ports:
      - 9001:80
    volumes:
      - /home/shlok/dockerservices/penpot/assets:/opt/data/assets
    depends_on:
      - penpot-backend
      - penpot-exporter
    networks:
      - penpot
    environment:
      ## https://help.penpot.app/technical-guide/configuration/#advanced-configuration
      - PENPOT_FLAGS=enable-registration enable-login-with-password
  penpot-backend:
    image: "penpotapp/backend:latest"
    restart: always
    volumes:
      - /home/shlok/dockerservices/penpot/assets:/opt/data/assets
    depends_on:
      - penpot-postgres
      - penpot-redis
    networks:
      - penpot

    environment:
      ## https://help.penpot.app/technical-guide/configuration/#advanced-configuration
      - PENPOT_FLAGS=enable-registration enable-login-with-password disable-email-verification enable-smtp enable-prepl-server
      - PENPOT_PUBLIC_URI=http://localhost:9001
      - PENPOT_DATABASE_URI=postgresql://penpot-postgres/penpot
      - PENPOT_DATABASE_USERNAME=penpot
      - PENPOT_DATABASE_PASSWORD=penpot
      - PENPOT_REDIS_URI=redis://penpot-redis/0
      - PENPOT_ASSETS_STORAGE_BACKEND=assets-fs
      - PENPOT_STORAGE_ASSETS_FS_DIRECTORY=/opt/data/assets
      - PENPOT_TELEMETRY_ENABLED=true
  penpot-exporter:
    image: "penpotapp/exporter:latest"
    restart: always
    networks:
      - penpot
    environment:
      - PENPOT_PUBLIC_URI=http://penpot-frontend
      - PENPOT_REDIS_URI=redis://penpot-redis/0
  penpot-postgres:
    image: "postgres:15"
    restart: always
    stop_signal: SIGINT
    volumes:
      - /home/shlok/dockerservices/penpot/db:/var/lib/postgresql/data
    networks:
      - penpot
    environment:
      - POSTGRES_INITDB_ARGS=--data-checksums
      - POSTGRES_DB=penpot
      - POSTGRES_USER=penpot
      - POSTGRES_PASSWORD=penpot
  penpot-redis:
    image: redis:7
    restart: always
    networks:
      - penpot
  penpot-mailcatch:
    image: sj26/mailcatcher:latest
    restart: always
    expose:
      - '1025'
    ports:
      - "1080:1080"
    networks:
      - penpot
```
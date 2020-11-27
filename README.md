# docker-compose-postgre

```yml
version: '3.1'

services:
  db:
    image: "postgres:10"
    container_name: mypostgres
    restart: always
    environment:
      - POSTGRES_DB=database
      - POSTGRES_USER=admin
      - POSTGRES_PASSWORD=123456
      - TZ=Asia/Taipei
    ports:
      - "5432:5432"
    volumes:
      - ./initdb.d:/docker-entrypoint-initdb.d
      - ./pgdata:/var/lib/postgresql/data
      - ./postgres.conf:/etc/postgresql/postgresql.conf
```

```console

docker-compose up

```

---
![Alt text](./assets/001.png)


```console

docker-compose up -d

```

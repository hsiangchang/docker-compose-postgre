# 利用 docker compose 建置 postgre 資料庫
> 如何利用 docker 建置環境，已經算是開發人員的基本日常，以下為利用 docker compose 機制來建置 postgreSQL 資料庫的範例

---
<br />
<br />

## 注意

* 請先準備好 docker , docker-compose 的執行環境
* **範例資料庫帳號密碼：admin/123456**

**1. 撰寫 docker-compose.yml 檔案**
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

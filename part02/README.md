# part02

## 2.1

docker-compose.yml file

```shell
version: '3'

services:
  simple-web-service:
    image: devopsdockeruh/simple-web-service
    volumes:
      - ./text.log:/usr/src/app/text.log
```

## 2.2

docker-compose.yml file

```shell
version: '3'

services:
  simple-web-service:
    image: devopsdockeruh/simple-web-service
    volumes:
      - ./text.log:/usr/src/app/text.log
    ports:
        - 8080:8080
    command: ["server"]
```

## 2.3(MANDATORY EXERCISE)

docker-compose.yml

```shell
version: "3.8"

services:
  frontend:
    image: frontend
    build: ./example-frontend
    ports:
      - 5000:5000
    container_name: frontend
  backend:
    image: backend
    build: ./example-backend
    ports:
      - 8080:8080
    container_name: backend
```

## 2.4

docker-compose.yml

```shell
version: "3.8"

services:
  redis:
    image: redis
    container_name: redis

  frontend:
    image: frontend
    build: ./example-frontend
    ports:
      - 5000:5000
    container_name: frontend
    depends_on:
      - backend
      
  backend:
    image: backend
    build: ./example-backend
    ports:
      - 8080:8080
    container_name: backend
    environment:
      - REDIS_HOST=redis
    depends_on:
      - redis
```

## 2.5

command

```shell
docker-compose up -d --scale compute=5
```

## 2.6

docker-compose.yml

```shell
version: "3.8"

services:
  redis:
    image: redis
    container_name: redis

  frontend:
    image: frontend
    build: ./example-frontend
    ports:
      - 5000:5000
    container_name: frontend
    depends_on:
      - backend
      
  backend:
    image: backend
    build: ./example-backend
    ports:
      - 8080:8080
    container_name: backend
    environment:
      - REDIS_HOST=redis
      - POSTGRES_HOST=db
      - POSTGRES_USER=postgres
      - POSTGRES_PASSWORD=postgres
      - POSTGRES_DATABASE=postgres
    depends_on:
      - redis

  db:
    image: postgres:alpine
    restart: unless-stopped
    container_name: db
    environment:
      - POSTGRES_PASSWORD=postgres
```

## 2.7

docker-compose.yml

```shell
version: "3.8"

services:
  
  redis:
    image: redis:alpine
    container_name: redis

  frontend:
    image: frontend
    build: ./example-frontend
    ports:
      - 5000:5000
    container_name: frontend
    depends_on:
      - backend
      
  backend:
    image: backend
    build: ./example-backend
    ports:
      - 8080:8080
    container_name: backend
    environment:
      - REDIS_HOST=redis
      - POSTGRES_HOST=db
      - POSTGRES_USER=postgres
      - POSTGRES_PASSWORD=postgres
      - POSTGRES_DATABASE=postgres
    depends_on:
      - redis

  db:
    image: postgres:13.2-alpine
    restart: unless-stopped
    environment:
      POSTGRES_PASSWORD: example
    container_name: db_redmine
    volumes:
      - database:/var/lib/postgresql/data

volumes:
  database:
```

## 2.8

docker-compose.yml

```shell
version: "3.8"

services:

  nginx:
    image: nginx:alpine
    container_name: nginx
    ports:
      - 80:80
    volumes:
      - ./nginx.conf:/etc/nginx/nginx.conf

  frontend:
    image: frontend
    build: ./example-frontend
    ports:
      - 5000:5000
    container_name: frontend
      
  backend:
    image: backend
    build: ./example-backend
    ports:
      - 8080:8080
    container_name: backend
    environment:
      - REDIS_HOST=redis
      - POSTGRES_HOST=db
      - POSTGRES_PASSWORD=postgres

  redis:
    image: redis:alpine
    container_name: redis

  db:
    image: postgres:13.2-alpine
    restart: unless-stopped
    environment:
      POSTGRES_PASSWORD: postgres
    container_name: db_postgres
    volumes:
      - database:/var/lib/postgresql/data

volumes:
  database:

```

## 2.9

## 2.10

## 2.11

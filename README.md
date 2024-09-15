# React18-docker-template
This is Docker settings of React18

## First step

- create Dockerfile
```js
FROM node:21-alpine3.18
WORKDIR /code
```

- create docker-compose.yml
```js
services:
  your_react_project_name:
    container_name: your_react_project_name
    build:
      context: .
      dockerfile: Dockerfile
    volumes:
      - ./app:/code
      - node_modules_volume:/app/node_modules
    # npm start
    command: sh -c "npm start"
    ports:
      - "8080:8080"
    # enable hot reload
    environment:
      - CHOKIDAR_USEPOLLING=true
volumes:
  node_modules_volume:
~
```

## Second step

- run the command below
```sh
docker-compose run --rm react-front sh -c "npx create-react-app app"
```

### Third step

- change the port
  - modify the script in package.json

```json
"start": "PORT=8080 react-scripts start"
```
>[!IMPORTANT]
> docker-compose.yml port should be same with package.json


## Fourth step

run the command below

```js
docker-compose build
docker-compose up -d
```

Happy coding!

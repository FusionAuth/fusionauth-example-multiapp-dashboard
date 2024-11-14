This repository holds code accompanying the FusionAuth application dashboard tutorial at https://fusionauth.io/docs/extend/examples/applicationDashboard.

## Project Contents
This project contains a `docker-compose.yml` fuke and a `kickstart` directory to assist in running your own local FusionAuth server. The `bankApp` and `insuranceApp` directories contain the demonstration Node.js apps that use FusionAuth for authentication.

## Project Dependencies
- Docker

## How to run

```sh
docker compose up

# new terminal:
cd bankApp
docker run --platform=linux/amd64 --rm -v ".:/app" -w "/app" node:23-alpine3.19 sh -c  "npm install"
docker run --platform=linux/amd64 --rm --network host  -v ".:/app" -w "/app" -e "PORT=3000" node:23-alpine3.19 sh -c  "npm run start"

# new terminal:
cd insuranceApp
docker run --platform=linux/amd64 --rm -v ".:/app" -w "/app" node:23-alpine3.19 sh -c  "npm install"
docker run --platform=linux/amd64 --rm --network host  -v ".:/app" -w "/app" -e "PORT=3001" node:23-alpine3.19 sh -c  "npm run start"
```

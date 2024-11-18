This repository holds code accompanying the FusionAuth application dashboard tutorial at https://fusionauth.io/docs/extend/examples/applicationDashboard.

## Project Contents
This project contains a `docker-compose.yml` fuke and a `kickstart` directory to assist in running your own local FusionAuth server. The `bankApp` and `insuranceApp` directories contain the demonstration Node.js apps that use FusionAuth for authentication.

## Project Dependencies
- Docker

## How to run

Run the commands below in a terminal opened in this repository.

```sh
docker compose up

# new terminal:
cd bankApp
docker run --platform=linux/amd64 --rm -v ".:/app" -w "/app" node:23-alpine3.19 sh -c  "npm install"
docker run --platform=linux/amd64 --rm --network faNetwork -p 3000:3000 -v ".:/app" -w "/app" -e "PORT=3000" node:23-alpine3.19 sh -c  "npm run start"

# new terminal:
cd insuranceApp
docker run --platform=linux/amd64 --rm -v ".:/app" -w "/app" node:23-alpine3.19 sh -c  "npm install"
docker run --platform=linux/amd64 --rm --network faNetwork -p 3001:3001 -v ".:/app" -w "/app" -e "PORT=3001" node:23-alpine3.19 sh -c  "npm run start"
```

- Browse to FusionAuth at http://localhost:9011/admin and log in with `admin@example.com` and `password`.
- Browse to Changebank at http://localhost:3000 and log in with the same username and password.
- Browse to Changeinsurance at http://localhost:3001 and log in with the same username and password.
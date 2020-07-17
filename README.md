# LaraNext

Welcome to the LaraNext project.
This personal project aims to provide a functional Docker configuration with Next.js in the frontend and Laravel in the backend. The selected database system is PostgreSQL.

## How to install

Clone the repo and build your containers.

```
git clone https://github.com/egdavid/LaraNext.git
docker-compose up -d --build
```

Don't forget to rename .env.example to .env before executing the following commands.

## Docker commands

Use Docker run to exec composer/artisan/npm commands

```
### Install and update Laravel dependencies
docker-compose run composer install
docker-compose run composer update

### Set the encryption key, migrate and seed the database
docker-compose run artisan key:generate
docker-compose run artisan migrate
docker-compose run artisan db:seed (optional)

### Install and update Nextjs dependencies
docker-compose run npm install
docker-compose run npm update
```

## Permissions

Set the right permissions on Laravel storage folder

```
sudo chmod -R 777 backend/storage
```

## Your containers are ready!

The frontend app is browsable at http://localhost:3001 and the backend at http://localhost:8080

You could set your own local domains using the hosts file of your Operating System.

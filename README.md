# LaraNext

Welcome to the LaraNext project.
This personal project aims to provide a functional Docker configuration with Next.js in the frontend and Laravel in the backend. The selected database system is PostgreSQL.

## What's up

LaraNext configuration is pretty simple. Its environment has been designed to offer a high-performance development tool capable of being propelled into production.

### Laravel 7.20

- Nginx
- PHP 7.4
- Memcached
- Redis
- Postgres

Please note that it's entirely possible to replace Laravel with Lumen if you wish to benefit from a lighter backend.

### Nextjs 9

The frontend is built on top of a simple `npx create-next-app` application with an `ESLint + Prettier + Airbnb Style` configuration.

## Installation

Clone the repo and build your containers.

```md
git clone https://github.com/egdavid/LaraNext.git
docker-compose up -d --build
```

Don't forget to rename .env.example to .env before executing the following commands.

## Docker commands

Use Docker run to exec composer/artisan/npm commands

```md
### Install and update Laravel dependencies

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

```md
sudo chown -R $USER:www-data backend
sudo chmod -R 777 backend/storage
```

## Urls

The frontend app is browsable at http://localhost:3000 and the backend at http://localhost:8080
You could set your own local domains using the hosts file of your Operating System.

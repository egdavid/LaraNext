# LaraNext

Welcome to the LaraNext project.

## How to install

```
git clone https://github.com/egdavid/LaraNext.git
docker-compose up -d --build
```

## Docker commands

Use Docker run to exec composer/artisan/npm commands

```
docker-compose run --rm composer update
docker-compose run --rm artisan migrate
docker-compose run --rm npm install
```

## Permissions

Set the right permissions on Laravel storage folder

```
sudo chmod -R 777 backend/storage
```

## Your container is ready!

The frontend app is browsable at http://localhost:3001 and the backend at http://localhost:8080

You could set your own domain using the hosts file of your Operating System

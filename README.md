# Docker Local CraftCMS Development

Local CraftCMS development environment with Docker, and Docker Compose.

This will create 3 containers

-   CraftCMS/Apache
-   phpMyAdmin
-   MySQL

I use Docker Desktop for Windows and this has worked well.

I have also been playing around with [portainer.io](https://www.portainer.io/) for managing docker containers, which seems pretty cool but not needed here.

## Requirements

Composer and Docker

Make sure you have [**Docker**](https://www.docker.com/) installed.

## Docker Config

Clone this repository or just copy docker-compose.yml and the .env file into your new project folder.

Edit the docker .env file to change the following variables to your prefernce.

-   IP
-   PROJECT_NAME
-   DB_ROOT_PASSWORD
-   DB_NAME

## Craft Config

Open a terminal where you cloned the respository, or just open the folder in your IDE and use it's terminal... Yay for VSCODE.

We first want to install CraftCMS via composer, I might turn this into a script down the road to automate it...

`composer create-project craftcms/craft html`

Next we need to edit the CraftCMS .env file in the html directory where it was installed `html/.env`

Add/Edit the following database settings

-   DB_DRIVER=mysql
-   DB_SERVER=db
-   DB_PORT=3306
-   DB_DATABASE=craftcms
-   DB_USER=root
-   DB_PASSWORD=password

**NOTE: If you modified the Docker .env above make sure to update DB_DATABASE and DB_PASSWORD with those values.**

Now lets spin up the docker container

`docker-compose up -d`

## Done

You should be able to access both CraftCMS, and phpMyAdmin installations with the configured IP in the browser address. 

By default it is `http://127.0.0.1`

-   Install/Access CraftCMS [http://127.0.0.1/admin](http://127.0.0.1/admin)
-   Access phpMyAdmin [http://127.0.0.1:8080](http://127.0.0.1:8080) user root, password you set in .env

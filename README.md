# docker-drupal

A template for running Drupal 8 in docker.

The following setup has been tested on Ubuntu 16.04 so if you have a different setup then adjust the commands to your needs.

## Requirements
* Docker
* Docker Compose
* Composer ([https://getcomposer.org/](https://getcomposer.org/))

## Installation

Open a terminal and navigate to the folder where you keep your projects.

Then run the following command:

```
git clone git@github.com:asimlqt/docker-drupal.git \
    && cd docker-drupal \
    && rm -rf .git \
    && composer create-project drupal-composer/drupal-project:8.x-dev drupal --stability dev --no-interaction \
    && cp -r drupal/. . \
    && rm -rf drupal \
    && mkdir -p config/sync \
    && chmod 777 config/sync \
    && mkdir -p web/sites/default \
    && chmod -R 777 web/sites/default
```

The above command will install all required dependencies. Once that has completed you can start docker:

```
docker-compose up
```

Give it a few seconds to start up and then open `http://localhost/` in your browser and you should see the Drupal installer. Follow the steps through until you reach `Set up database`, use the settings below:

```
Database name: drupal
Database username: drupal
Database password: drupal
Host: mysql
```

And then complete the installation!

## drush

There is a helper script to run drush. It needs to be run inside the docker container because it requires acces to the mysql cli:

```
./docker/bin/drush
```

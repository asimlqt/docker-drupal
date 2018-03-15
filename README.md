# docker-drupal

A template for running Drupal 8 in docker.

## Requirements
* Ubuntu 16.04
* Docker
* Docker Compose

## Installation

Open a terminal and navigate to the folder where you keep your projects.

Then run the following command to clone the repo:

```
git clone git@github.com:asimlqt/docker-drupal.git && cd docker-drupal && rm -rf .git
```

Next we will install Drupal using composer. It is not possible to create a new project using composer in a non-empty directory so will install it in a `drupal` folder and then copy the files into the root directory. We will also need a config/sync folder which Drupal writes to during the install process.

```
composer create-project drupal-composer/drupal-project:8.x-dev drupal --stability dev --no-interaction && cp -r drupal/. . && rm -rf drupal && mkdir -p config/sync && chmod 777 config/sync && mkdir -p web/sites/default && chmod -R 777 web/sites/default
```

Open `http://localhost/` in your browser and you should see the Drupal installer. Follow the steps through until you reach 'Set up database', use the settings below:

```
Database name: drupal
Database username: drupal
Database password: drupal
Host: mysql
Port number: 3306
```

And then complete the installation!

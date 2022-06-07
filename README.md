# Symfony-MAMP

Symfony-MAMP is a set of docker images that include Starter-Kit for a MAMP stack ([Symfony6](https://symfony.com/), [macOS](https://www.apple.com/macos/monterey/), [Apache](https://www.apache.org/), [MySQL](https://www.mysql.com/), [PHP8](https://www.php.net/) and [phpMyAdmin](https://www.phpmyadmin.net/)) all in one handy package.

## creator: Santosh Kalwar

## Using the image

## Installation

```shell
git clone https://github.com/kalwar/Symfony-MAMP.git
```

rename the file from Symfony-MAMP to {project-name}
cd {project-name} or drag file to you IDE

- open file docker-compose.yml

  - uncomment “linux” line if you have an M1 processor mac.

  optional:

  - change the ports:

    - line 7 for db '3308:3306' change the last 4 digits number "3306".
    - line 23 for phpmyadmin change first 4 digits number "9082".
    - line 36 for web server image fist 4 digits "8007".

  - change the database name. (not recomended if you dont know what you are doing, if you still want to change it write the same (myDb) in the next step) Switch "db" for your name (myDb):

    - go to docker-compose.yml and change db name in:
      - line 3
      - line 25
      - line 27

  - change the username, password and host:
    - inside .env you will find a self explained text:
      - DATABASE_NAME=(database-name)
      - DATABASE_USERNAME=(host)
      - DATABASE_PASSWORD=(password)
    - if you do any change you must also do it in web/.env file:
      - DATABASE_URL=mysql://(host):(password)@(myDb):3306/(database-name)?serverVersion=5.7

- open a terminal in your IDE

  ```shell
  docker-compose up --build
  ```

- Symfony 6 will run on [http://localhost:8007]
- phpMyAdmin will run on [http://localhost:9082]

```shell
cd web
composer require doctrine
composer require templates
composer require symfony/asset
```

create a few entities (db tables) follow carefully the guide.

```shell
bin/console make:entity
```

from cli docker image ( not phpmyadmin port and no sql port but the main cli image terminal )

```shell
cd web
php bin/console make:migration
php bin/console doctrine:migrations:migrate
```

come back to the IDE terminal and run:

```shell
composer require form validator security-csrf annotations
bin/console make:crud
```

will ask you for a name of a entity to be made a crud
gif the name of your table with initial capital letter or you will get a [ERROR] Entity "entity_name" doesn't exist; please enter an existing one or create a new one.

if you are making a fullstack project with react:

```shell
composer require symfony/webpack-encore-bundle
composer require symfony/orm-pack
composer require ux-turbo
npm install --force
npm run watch
```

# Use for reference

Use solely for reference material only

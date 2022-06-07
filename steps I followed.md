# Symfony-MAMP

Symfony-MAMP is a set of docker images that include Starter-Kit for a MAMP stack ([Symfony6](https://symfony.com/), [macOS](https://www.apple.com/macos/monterey/), [Apache](https://www.apache.org/), [MySQL](https://www.mysql.com/), [PHP8](https://www.php.net/) and [phpMyAdmin](https://www.phpmyadmin.net/)) all in one handy package.

## creator: Santosh Kalwar

## Using the image

## Installation

```shell
git clone https://github.com/kalwar/Symfony-MAMP.git
```

rename the file from Symfony-MAMP to <project-name>
cd <project-name> or drag file to you IDE

- open file docker-compose.yml

  - change the ports if needed.
  - uncomment “linux” line if you have an M1 processor mac.

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

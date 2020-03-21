> ℹ️ **NOTE:** The instructions below are for **setting up a local DEVELOPMENT environment**. If you are looking for basic installation instructions see the [Installation](https://github.com/DirectoryLister/DirectoryLister/wiki/Installation) page instead.
---

Setting up a Local Development Environment
------------------------------------------

### Requirements

  * [PHP](https://php.net) >= 7.3
    * [Composer](https://getcomposer.org)
  * [NPM](https://www.npmjs.com)
  * [Docker](https://www.docker.com)
    * [Docker Compose](https://docs.docker.com/compose/)

### Instructions

  1. [Fork the Directory Lister repository to your own account](https://github.com/DirectoryLister/DirectoryLister/fork)

  2. [Clone your fork to a local repository](https://help.github.com/en/github/creating-cloning-and-archiving-repositories/cloning-a-repository)

  3. Switch to the Directory Lister directory

          cd /path/to/DirectoryLister

  4. Install and build PHP and JavaScript dependencies

          composer install --no-interaction
          npm install && npm run dev

  5. Create the Docker `development` network

          docker network create development

  6. Create the Docker development proxy

          docker run -d -p 80:80 --network development --restart unless-stopped --volume /var/run/docker.sock:/tmp/docker.sock:ro --name dev-proxy jwilder/nginx-proxy

  7. Add the following entry to `/etc/hosts`:

          127.0.0.1  directory-lister.local

  8. Run the local Docker container

          docker-compose up -d

You should now be able to access your local Directory Lister installation at <http://directory-lister.local>

Code Analysis and Testing
-------------------------

### Coding Standards

Applies coding standards to all application and tests files.

    app/vendor/bin/php-cs-fixer fix

See the changes before applying.

    app/vendor/bin/php-cs-fixer fix --diff --dry-run

### Static Analysis

    app/vendor/bin/psalm --show-info=true

### Unit/Feature Tests

    app/vendor/phpunit

### Code Coverage

    app/vendor/bin/phpunit --coverage-text

or generate a more detailed HTML coverage report with

    app/vendor/bin/phpunit --coverage-html .coverage

Building Release Artifacts
--------------------------

Release artifacts will built in the `artifacts` directory.

### Build All

    make artifacts

### Build `tar.gz`

    make tar

#### Build `zip`

    make zip

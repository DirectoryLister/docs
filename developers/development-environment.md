# Development Environment

## Requirements

* [PHP](https://php.net) >= 8.2 with the `zip`, `dom` and `fileinfo` (and optionally `apcu`, `memcached`, `redis`) extensions&#x20;
  * [Composer](https://getcomposer.org) for PHP dependency management
* [NPM](https://www.npmjs.com) for front end asset serving and bundling
* [Docker](https://www.docker.com) and [Docker Compose](https://docs.docker.com/compose/) for running the local development container
* [Git](https://git-scm.com/) for version control

## Instructions

{% hint style="info" %}
These instructions are for setting up a local DEVELOPMENT environment. If you are looking for basic installation instruction see the [Installation](../getting-started/installation.md) page instead.
{% endhint %}

1. [Fork the Directory Lister repository to your own account](https://github.com/DirectoryLister/DirectoryLister/fork) (optional)
2.  [Clone Directory Lister to a local repository](https://help.github.com/en/github/creating-cloning-and-archiving-repositories/cloning-a-repository)

    ```
    git clone {{ REPOSITORY_URL }}
    ```
3.  Switch to the Directory Lister directory

    ```
    cd /path/to/DirectoryLister
    ```
4.  Install and build PHP and JavaScript dependencies

    ```
    composer install
    npm install
    npm run dev
    ```
5.  Run the local Docker container

    ```
    docker-compose up -d
    ```
6.  Add a host name entry to `/etc/hosts` (optional)

    ```
    127.0.0.1  directory-lister.local
    ```

You should now be able to access your local Directory Lister installation at `http://localhost` (or [http://directory-lister.local](http://directory-lister.local) if you added a host name entry)

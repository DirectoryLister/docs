# Upgrade Guide

Upgrading Directory Lister is quick and painless whether you're upgrading an existing installation or upgrading from Directory Lister `2.X`.

## Upgrade an existing Directory Lister installation

1. Download the latest version of Directory Lister 3 from [https://www.directorylister.com](https://www.directorylister.com)
2. Extract the zip/tar archive
3. Copy the extracted files/folders to your existing installation location overwriting any files if prompted
4.  Clear the cache by deleting all files in the `app/cache` directory

    ```
     rm -rf app/cache/*
    ```

## Upgrade from Directory Lister 2

{% hint style="info" %}
Please note, Directory Lister 3 requires PHP >= 7.4
{% endhint %}

1. Download the latest version of Directory Lister 3 from [https://www.directorylister.com](https://www.directorylister.com)
2. Extract the zip/tar archive
3.  Remove `index.php` and the `resources` folder from your existing installation

    ```
     rm -rf index.php resources
    ```
4. Copy the extracted files/folders to your existing installation location overwriting any files if prompted

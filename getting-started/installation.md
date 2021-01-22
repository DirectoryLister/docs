# Installation

Installation of Directory Lister is fast and requires no configuration.

{% hint style="info" %}
If you're upgrading from Directory Lister 2.X see the [Upgrade Guide](upgrade-guide.md) for upgrade instructions.
{% endhint %}

## Requirements

* Directory Lister requires [PHP](https://www.php.net/) 7.2+
  * The [Zip](https://www.php.net/manual/en/book.zip.php) extension is required for zip downloads
  * The [DOM](https://www.php.net/en/dom) and [Fileinfo](https://www.php.net/manual/en/book.fileinfo.php) extensions are required for README rendering

## Manual Installation

1. [Download Directory Lister](https://www.directorylister.com)
2. Extract the zip/tar archive
3. Copy extracted files/folders to your web server

## Install with Composer

```bash
composer create-project phlak/directory-lister
```


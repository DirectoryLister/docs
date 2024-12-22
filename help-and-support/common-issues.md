# Common Issues

The following are common issues and some information on why these occur and how to solve them.

## `open_basedir restriction in effect`

### Symptoms

You may see an error like the following:

```text
PHP Fatal error:  Uncaught RuntimeException: SplFileInfo::isFile(): open_basedir restriction in effect.
```

### Explanation

Directory Lister has security restrictions in place to to mitigate [directory traversal attacks](https://owasp.org/www-community/attacks/Path_Traversal). Specifically, the [`open_basedir`](https://www.php.net/manual/en/ini.core.php#ini.open-basedir) directive is set to the application root directory. Thus, any attempt to access files outside of the application root will be denied and cause an error similar to the one above. This applies to symbolic links pointing to files outside of the application root as well.

## Configuration changes don't take affect when changed

### Symptoms

Configuration changes made in the `.env` file aren't reflected in your application.

### Explanation

This was an issue with the v3.4.0 release. The issue was promptly resolved with the v3.4.1 bug fix, however, the bug could persist through upgrades if the application cache wasn't cleared. To resolve this issue, first ensure you're running v3.4.1 or later then clear your application cache as per the [Upgrade Guide](../getting-started/upgrade-guide.md).

```text
rm -rf app/cache/*
```

## Error 500 when visiting the server (apache2 only)

### Symptoms

Your server doesn't respond when visiting the page with Directory Lister installed.

### Explanation

Check if you have all dependencies related to Directory Lister installed. If you have, check your server logs.

On Apache2:

```text
cat /var/log/apache2/error.log
```

Check if you have entries that should look something like this (ignore the date and IP part):

```text
[Sun Jan 1 00:00:00.000000 2000] [php:error] [pid 0] [client 192.168.1.1:20000] PHP Fatal error:  Uncaught InvalidArgumentException: Compilation directory is not writable: /var/www/html/app/cache. in /var/www/html/app/vendor/php-di/php-di/src/Compiler/Compiler.php:345\nStack trace:\n#0 /var/www/html/app/vendor/php-di/php-di/src/Compiler/Compiler.php(160): DI\\Compiler\\Compiler->createCompilationDirectory()\n#1 /var/www/html/app/vendor/php-di/php-di/src/ContainerBuilder.php(144): DI\\Compiler\\Compiler->compile()\n#2 /var/www/html/app/src/Bootstrap/BootManager.php(22): DI\\ContainerBuilder->build()\n#3 /var/www/html/index.php(16): App\\Bootstrap\\BootManager::createContainer()\n#4 {main}\n  thrown in /var/www/html/app/vendor/php-di/php-di/src/Compiler/Compiler.php on line 345
```

It seems that the cache directory is unwritable by the www-data/apache user, so we need to give some permissions. First, check if the /var/www/html/app/cache directory exists:

```text
ls -ld /var/www/html/app/cache
```

If it does not exist, create it:

```text
sudo mkdir -p /var/www/html/app/cache
```

To set the correct ownership, first ensure the directory is owned by the Apache user and group:

#### Ubuntu / Debian

```text
sudo chown -R www-data:www-data /var/www/html/app/cache
```

#### Fedora / Redhat

```text
sudo chown -R apache:apache /var/www/html/app/cache
```

Then set the correct permissions:

```text
sudo chmod -R 775 /var/www/html/app/cache
```

With everything set up, feel free to restart your Apache server with this command to apply any changes:

#### Ubuntu / Debian

```text
sudo systemctl restart apache2
```

#### Fedora / Redhat

```text
sudo systemctl restart httpd
```

Test the application to ensure the error is resolved. If the issue persists, double-check the logs and permissions.

Note: granting write permissions should only be done with caution. Ensure that the cache directory is isolated and secure to avoid potential vulnerabilities. If you still encounter issues, check the PHP configuration (php.ini) for restrictions related to file writes or open_basedir.

## `Class 'DOMDocument' not found`

### Symptoms

You may see an error like the following:

```text
Fatal error: Uncaught Error: Class 'DOMDocument' not found
```

### Explanation

This error occurs when you're server is missing the PHP [DOM extension](https://www.php.net/en/dom). This extension is required for rendering README files on the page. You will need to install that extension.

#### Ubuntu / Debian

```text
sudo apt install php-dom
```

#### Fedora / Redhat

```text
sudo yum install php-xml
```

Alternatively you can disable READMEs by setting [`DISPLAY_READMES`](../configuration/app-config-reference.md#display_readmes) to `false` in your `.env` file.

## `Call to undefined function mime_content_type()`

### Symptoms

You may see an error like the following:

```text
Fatal error: Uncaught Error: Call to undefined function mime_content_type()
```

### Explanation

This error occurs when you're server is missing the PHP [fileinfo](https://www.php.net/manual/en/book.fileinfo.php) extension. This extension is required for rendering README files on the page. You will need to install that extension.

#### Ubuntu / Debian

```text
sudo apt install php-mime-type
```

#### Fedora / Redhat

```text
???
```

Alternatively you can disable READMEs by setting [`DISPLAY_READMES`](../configuration/app-config-reference.md#display_readmes) to `false` in your `.env` file.


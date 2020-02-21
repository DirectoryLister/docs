For general help and support join our [Spectrum Community](https://spectrum.chat/directory-lister) or reach out on [Twitter](https://twitter.com/DirectoryLister).

Please report bugs to the [GitHub Issue Tracker](https://github.com/DirectoryLister/DirectoryLister/issues).

Common Issues
=============

### `open_basedir restriction in effect`

#### Symptoms

You may see an error like the following:

```
PHP Fatal error:  Uncaught RuntimeException: SplFileInfo::isFile(): open_basedir restriction in effect.
```

#### Explanation

Directory Lister has security restrictions in place to to mitigate [directory traversal attacks](https://owasp.org/www-community/attacks/Path_Traversal). Specifically, the [`open_basedir`](https://www.php.net/manual/en/ini.core.php#ini.open-basedir) directive is set to the application root directory. Thus, any attempt to access files outside of the application root will be denied and cause an error similar to the one above. This applies to symbolic links pointing to files outside of the application root as well.

---

### `Class 'DOMDocument' not found`

#### Symptoms

You may see an error like the following:

```
Fatal error: Uncaught Error: Class 'DOMDocument' not found
```

This error occurs when you're server is missing the PHP [DOM extension](https://www.php.net/en/dom). This extension is required for rendering README files on the page. You will need to install that extension.

##### Ubuntu / Debian

    sudo apt install php-dom

##### Fedora / Redhat

    sudo yum install php-xml

Alternatively you can disable READMEs by setting [`DISPLAY_READMES`](https://github.com/DirectoryLister/DirectoryLister/wiki/Config-Reference#display_readmes) to `false` in your `.env` file.
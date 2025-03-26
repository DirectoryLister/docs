---
icon: square-list
---

# Configuration Reference

## Bootstrap Configuration

These configuration options are special configuration options only configurable through environment variables (e.g. through the `.env` file).

{% hint style="info" %}
There are no corresponding configuration options for these values in the `app/config` definitions because they are applied _before_ the application container (and configuration) is loaded.
{% endhint %}

### `FILES_PATH`&#x20;

A path (relative or absolute) to the directory in which you would like to list. This may even be a path outside of the application directory. When left unset, the root application directory (i.e. the folder where `index.php` is located) will be listed.

{% tabs %}
{% tab title="Possible Values" %}
An absolute or relative file path (string)
{% endtab %}

{% tab title="Default Value" %}
`<unset>`
{% endtab %}
{% endtabs %}

### `COMPILE_CONTAINER`&#x20;

Whether or not the application container will be compiled. When set to `false` the container will _not_ be compiled and cached. If left unset the container will be compiled and cached on first run and the cached container will be reused on subsequent requests. Disabling this comes with a (likely negligible) performance hit. Generally this should not be changed but might be necessary to modify when running Directory Lister on a read-only filesystem.

{% tabs %}
{% tab title="Possible Values" %}
`false` or `<unset>`
{% endtab %}

{% tab title="Default Value" %}
`<unset>`
{% endtab %}
{% endtabs %}

## Runtime Configuration

General runtime configuration is controlled by the app config located at `app/config/app.php`. These options control core application functionality.

{% hint style="warning" %}
It is highly recommended to set these values via their respective environment variables. This can be accomplished via a `.env` file located in the root of your application. An example file is provided as `.env.example`.
{% endhint %}

### `analytics_file`

File containing analytics scripts that will be included in the HTML output of your directory listing.

{% tabs %}
{% tab title="Possible Values" %}
A (string) file name
{% endtab %}

{% tab title="Default Value" %}
`.analytics`
{% endtab %}

{% tab title="Environment Variables" %}
`ANALYTICS_FILE`
{% endtab %}
{% endtabs %}

### `date_format`

The format used for rendering dates in the application views.

{% tabs %}
{% tab title="Possible Values" %}
See the [PHP `date` format documentation](https://www.php.net/manual/en/function.date.php#refsect1-function.date-parameters) for possible values.
{% endtab %}

{% tab title="Default Value" %}
`Y-m-d H:i:s`
{% endtab %}

{% tab title="Environment Variable" %}
`DATE_FORMAT`
{% endtab %}
{% endtabs %}

### `debug`

Enable application debugging and display error messages.

{% hint style="danger" %}
It is recommended that debug remains OFF unless troubleshooting an issue. Leaving this enabled WILL cause leakage of sensitive server information.
{% endhint %}

{% tabs %}
{% tab title="Possible Values" %}
`true` or `false`
{% endtab %}

{% tab title="Default Value" %}
`false`
{% endtab %}

{% tab title="Environment Variable" %}
`APP_DEBUG`
{% endtab %}
{% endtabs %}

### `display_readmes`

Parse and render `README` files on the page.

{% tabs %}
{% tab title="Possible Values" %}
`true` or `false`
{% endtab %}

{% tab title="Default Value" %}
`true`
{% endtab %}

{% tab title="Environment Variable" %}
`DISPLAY_READMES`
{% endtab %}
{% endtabs %}

### `google_analytics_id`

Your Google analytics tracking ID.

{% hint style="danger" %}
This configuration option has been deprecated and will stop working in a future release. See the [Analytics Script Injection](configuration-overview.md#analytics-script-injection) section for instructions on configuring analytics tracking.
{% endhint %}

{% tabs %}
{% tab title="Possible Values" %}
A string in the format of `UA-123456789-0` or `false` to disable
{% endtab %}

{% tab title="Default Value" %}
`false`
{% endtab %}

{% tab title="Environment Variable" %}
`GOOGLE_ANALYTICS_ID`
{% endtab %}
{% endtabs %}

### `hidden_files_list`

File containing hidden file definitions. Will be merged with definitions from the 'hidden\_files' configuration option.

{% hint style="info" %}
See the [Hiding Files](hiding-files.md) page for additional info on hiding files.
{% endhint %}

{% tabs %}
{% tab title="Possible Values" %}
A path (string) to a file
{% endtab %}

{% tab title="Default Value" %}
`.hidden`
{% endtab %}

{% tab title="Environment Variable" %}
`HIDDEN_FILES_LIST`
{% endtab %}
{% endtabs %}

### `hidden_files`

Array of hidden file definitions. Will be merged with definitions in the file defined in the `hidden_files_list` configuration option. Supports glob patterns (e.g. `*.txt`, `file.{yml,yaml}`, etc.).

{% hint style="info" %}
See the [Hiding Files](hiding-files.md) page for additional info on hiding files.
{% endhint %}

{% tabs %}
{% tab title="Possible Values" %}
An array of paths (strings)
{% endtab %}

{% tab title="Default Value" %}
`[]` (an empty array)
{% endtab %}

{% tab title="Example" %}
```php
'hidden_files' => [
    'somefile.txt', // Matches 'somefile.txt' exactly
    'README.*', // Matches files named 'README' with any file extension
    'foo/*', // Matches all files in the 'foo' directory
    'schema.{ya?ml}', // Matches 'schema.yml' or 'schema.yaml'
]
```
{% endtab %}
{% endtabs %}

### `hide_app_files`

Hide application specific files/directories (i.e. `index.php` and the `app` folder).

{% tabs %}
{% tab title="Possible Values" %}
`true` or `false`
{% endtab %}

{% tab title="Default Value" %}
`true`
{% endtab %}

{% tab title="Environment Variable" %}
`HIDE_APP_FILES`
{% endtab %}
{% endtabs %}

### `hide_dot_files`

Hide dot files/directories from the listing.

{% tabs %}
{% tab title="Possible Values" %}
`true` or `false`
{% endtab %}

{% tab title="Default Value" %}
`true`
{% endtab %}

{% tab title="Environment Variable" %}
`HIDE_DOT_FILES`
{% endtab %}
{% endtabs %}

### `hide_vcs_files`

Hide the files Version Control Systems (i.e. Git and Mercurial) use to store their metadata.

{% tabs %}
{% tab title="Possible Values" %}
`true` or `false`
{% endtab %}

{% tab title="Default Value" %}
`true`
{% endtab %}

{% tab title="Environment Variable" %}
`HIDE_VCS_FILES`
{% endtab %}
{% endtabs %}

### `home_text`

Text of the `home` link in the navigation breadcrumbs. If undefined or `null` will use the translated form of "home" from your selected language.

{% tabs %}
{% tab title="Possible Values" %}
Any string
{% endtab %}

{% tab title="Default Value" %}
`null`
{% endtab %}

{% tab title="Environment Variable" %}
`HOME_TEXT`
{% endtab %}
{% endtabs %}

### `language`

The application's interface language.

{% tabs %}
{% tab title="Possible Values" %}
See the [`app/translations`](https://github.com/DirectoryLister/DirectoryLister/tree/master/app/translations) folder for available translations.
{% endtab %}

{% tab title="Default Value" %}
`en` (English)
{% endtab %}

{% tab title="Environment Variable" %}
`APP_LANGUAGE`
{% endtab %}
{% endtabs %}

### `matomo_analytics_site_id`

Your Matomo analytics site ID.

{% hint style="danger" %}
This configuration option has been deprecated and will stop working in a future release. See the [Analytics Script Injection](configuration-overview.md#analytics-script-injection) section for instructions on configuring analytics tracking.
{% endhint %}

{% tabs %}
{% tab title="Possible Values" %}
A Matomo analytics site ID (string)
{% endtab %}

{% tab title="Default Value" %}
`false`
{% endtab %}

{% tab title="Environment Variable" %}
`MATOMO_ANALYTICS_SITE_ID`
{% endtab %}
{% endtabs %}

### `matomo_analytics_url`

Your Matomo analytics URL.

{% hint style="danger" %}
This configuration option has been deprecated and will stop working in a future release. See the [Analytics Script Injection](configuration-overview.md#analytics-script-injection) section for instructions on configuring analytics tracking.
{% endhint %}

{% tabs %}
{% tab title="Possible Values" %}
A Matomo analytics URL (string)
{% endtab %}

{% tab title="Default Value" %}
`false`
{% endtab %}

{% tab title="Environment Variable" %}
`MATOMO_ANALYTICS_URL`
{% endtab %}
{% endtabs %}

### `max_hash_size`

The maximum file size (in bytes) that can be hashed. This helps to prevent timeouts for excessively large files.

{% hint style="warning" %}
The larger a file is the longer it will take to calculate hashes for that file.
{% endhint %}

{% tabs %}
{% tab title="Possible Values" %}
Any positive integer `0` - `9223372036854775807` ([`PHP_INT_MAX`](https://www.php.net/manual/en/reserved.constants.php#constant.php-int-max))
{% endtab %}

{% tab title="Default Value" %}
`1000000000` (1 GB)
{% endtab %}

{% tab title="Environment Variable" %}
`MAX_HASH_SIZE`
{% endtab %}
{% endtabs %}

### `meta_description`

Meta tag description (i.e. `<meta name="description">`) text.

{% tabs %}
{% tab title="Possible Values" %}
Any string
{% endtab %}

{% tab title="Default Value" %}
`Yet another directory listing, powered by Directory Lister.`
{% endtab %}

{% tab title="Environment Variable" %}
`META_DESCRIPTION`
{% endtab %}
{% endtabs %}

### `readmes_first`

Show READMEs before the file listing.

{% tabs %}
{% tab title="Possible Values" %}
`true` or `false`
{% endtab %}

{% tab title="Default Value" %}
`false`
{% endtab %}

{% tab title="Environment Variable" %}
`READMES_FIRST`
{% endtab %}
{% endtabs %}

### `reverse_sort`

When enabled, reverses the order of files (after sorting is applied).

{% tabs %}
{% tab title="Possible Values" %}
`true` or `false`
{% endtab %}

{% tab title="Default Value" %}
`false`
{% endtab %}

{% tab title="Environment Variable" %}
`REVERSE_SORT`
{% endtab %}
{% endtabs %}

### `site_title`

The title of your directory listing. This will be displayed in the browser tab/title bar along with the current path.

{% tabs %}
{% tab title="Possible Values" %}
Any string
{% endtab %}

{% tab title="Default Value" %}
`Directory Lister`
{% endtab %}

{% tab title="Environment Variable" %}
`SITE_TITLE`
{% endtab %}
{% endtabs %}

### `sort_order`

Sorting order of files and folders. Can be one of several predefined values or a custom [anonymous function](https://www.php.net/manual/en/functions.anonymous.php).

When using an anonymous function it must be wrapped in a `\DI\value()` function. The anonymous function receives two `\SplFileInfo` objects as arguments and expects an integer to be returned.

### Example

```php
'sort_order' => \DI\value(
    function (SplFileInfo $file1, SplFileInfo $file2) {
        return strcmp($file1->getRealPath(), $file2->getRealPath());
    })
);
```

{% tabs %}
{% tab title="Possible Values" %}
`type`, `natural`, `name`, `accessed`, `changed`, `modified`, `<anonymous function>`
{% endtab %}

{% tab title="Default Value" %}
`type`
{% endtab %}

{% tab title="Environment Variable" %}
`SORT_ORDER`
{% endtab %}
{% endtabs %}

### `timezone`

Time zone used for date formatting.

{% tabs %}
{% tab title="Possible Values" %}
For a list of supported time zones see: [https://www.php.net/manual/en/timezones.php](https://www.php.net/manual/en/timezones.php).
{% endtab %}

{% tab title="Default Value" %}
The server's timezone
{% endtab %}

{% tab title="Environment Variable" %}
`TIMEZONE`
{% endtab %}
{% endtabs %}

### `zip_downloads`

Enable downloading of directories as a zip archive.

{% tabs %}
{% tab title="Possible Values" %}
`true` or `false`
{% endtab %}

{% tab title="Default Value" %}
`true`
{% endtab %}

{% tab title="Environment Variable" %}
`ZIP_DOWNLOADS`
{% endtab %}
{% endtabs %}

### &#x20;`zip_compress`

Compress Zip using Deflate. Enabling this option prevents file size estimation and it may prevent zip download resuming when paused.

{% tabs %}
{% tab title="Possible Values" %}
`true` or `false`
{% endtab %}

{% tab title="Default Value" %}
`false`
{% endtab %}

{% tab title="Environment Variable" %}
`ZIP_COMPRESS`
{% endtab %}
{% endtabs %}

## Cache Configuration

The cache config is located at `app/config/cache.php`. These options control the application cache.

{% hint style="warning" %}
It is highly recommended to set these values via their respective environment variables. This can be accomplished via a `.env` file located in the root of your application. An example file is provided as `.env.example`.
{% endhint %}

### `cache_driver`

The application cache driver. Setting this value to `array` will disable the cache across requests. Additional driver-specific options may be required with certain values.

{% tabs %}
{% tab title="Possible Values" %}
`apcu`, `array`, `file`, `memcached`, `redis`, `php-file`
{% endtab %}

{% tab title="Default Value" %}
`file`
{% endtab %}

{% tab title="Environment Variable" %}
`CACHE_DRIVER`
{% endtab %}
{% endtabs %}

### `cache_lifetime`

The app cache lifetime (in seconds). Setting this value to `0` will cache indefinitely.

{% tabs %}
{% tab title="Possible values" %}
Any positive integer
{% endtab %}

{% tab title="Default Value" %}
`60` (one hour)
{% endtab %}

{% tab title="Environment Variable" %}
`CACHE_LIFETIME`
{% endtab %}
{% endtabs %}

### `cache_lottery`

Some cache drivers require manually pruning the cache periodically to remove expired items. This is the percentage chance (out of 100) of a request "winning" the lottery causing the cache to be pruned.

{% tabs %}
{% tab title="Possible Values" %}
Any integer betweeen `1` and `100`
{% endtab %}

{% tab title="Default Value" %}
`2`
{% endtab %}

{% tab title="Environment Variable" %}
`CACHE_LOTTERY`
{% endtab %}
{% endtabs %}

### `memcached_host`

The Memcached server hostname or IP address.

{% tabs %}
{% tab title="Possible Values" %}
Any string
{% endtab %}

{% tab title="Default Value" %}
`localhost`
{% endtab %}

{% tab title="Environment Variable" %}
`MEMCACHED_HOST`
{% endtab %}
{% endtabs %}

### `memcached_port`

The Memcached server port.

{% tabs %}
{% tab title="Possible Values" %}
Any valid port as an integer (`0` to `65353`)
{% endtab %}

{% tab title="Default Value" %}
`11211`
{% endtab %}

{% tab title="Environment Variable" %}
`MEMCACHED_PORT`
{% endtab %}
{% endtabs %}

### `memcached_config`

The Memcached configuration [anonymous function](https://www.php.net/manual/en/functions.anonymous.php) (closure). This option is used when the `cache_driver` configuration option is set to `memcached`. The closure receives a `Memcached` object as it's only parameter. You can use this object to configure the Memcached connection. At a minimum you must connect to one or more Memcached servers via the `addServer()` or `addServers()` methods.

{% hint style="info" %}
Reference the [PHP Memcached documentation](https://secure.php.net/manual/en/book.memcached.php) for Memcached configuration options.
{% endhint %}

{% tabs %}
{% tab title="Possible Values" %}
An anonymous function that receives a `Memcached` object

```php
function (Memcached $memcached): void {
    // Configure the $memcached object
}
```
{% endtab %}

{% tab title="Default Value" %}
```php
DI\value(function (Memcached $memcached, Config $config): void {
    $memcached->addServer(
        $config->get('memcached_host'),
        $config->get('memcached_port')
    );
})
```

This closure adds a single connection to a server at the host defined by [`memcached_host`](broken-reference) on the port defined by [`memcached_port`](broken-reference).
{% endtab %}

{% tab title="Environment Variables" %}
Uses the `MEMCACHED_HOST` and `MEMCACHED_PORT` variables by default
{% endtab %}
{% endtabs %}

### `redis_host`

The Redis server hostname or IP address.

{% tabs %}
{% tab title="Possible Values" %}
Any string
{% endtab %}

{% tab title="Default Value" %}
`localhost`
{% endtab %}

{% tab title="Environment Variable" %}
`REDIS_HOST`
{% endtab %}
{% endtabs %}

### `redis_port`

The Redis server port.

{% tabs %}
{% tab title="Possible Values" %}
Any valid port as an integer (`0` to `65353`)
{% endtab %}

{% tab title="Defualt Value" %}
`6379`
{% endtab %}

{% tab title="Environment Variable" %}
`REDIS_PORT`
{% endtab %}
{% endtabs %}

### `redis_config`

The Redis configuration [anonymous function](https://www.php.net/manual/en/functions.anonymous.php) (closure). This option is used when the `cache_driver` configuration option is set to `redis`. The closure receives a `Redis` object as it's only parameter. You can use this object to configure the Redis connection. At a minimum you must connect to one or more Redis servers via the `connect()` or `pconnect()` methods.

{% hint style="info" %}
Reference the [phpredis documentation](https://github.com/phpredis/phpredis#readme) for Redis configuration options.
{% endhint %}

{% tabs %}
{% tab title="Possible Values" %}
An anonymous function that receives a `Redis` object

```php
function (Redis $redis): void {
    // Configure the $redis object
}
```
{% endtab %}

{% tab title="Default Value" %}
```php
DI\value(function (Redis $redis, Config $config): void {
    $redis->pconnect(
        $config->get('redis_host'),
        $config->get('redis_port')
    );
})
```

This closure adds a single connection to a server at the host defined by [`redis_host`](broken-reference) on the port defined by [`redis_port`](broken-reference).
{% endtab %}

{% tab title="Environment Variables" %}
Uses the `REDIS_HOST` and `REDIS_PORT` variables by default
{% endtab %}
{% endtabs %}

### `http_cache`

HTTP cache values for controlling browser page cache durations. An array of mimetypes mapped to their cache duration in seconds..

{% tabs %}
{% tab title="Possible Values" %}
An array of [mime types](https://developer.mozilla.org/en-US/docs/Web/HTTP/Basics_of_HTTP/MIME_types/Common_types) mapped to their cache duration as a seconds (integers).
{% endtab %}

{% tab title="Defualt Value" %}
```php
[
    'application/json' => 300,
    'application/zip' => 300,
]
```
{% endtab %}
{% endtabs %}

### `view_cache`

Path to the view cache directory. Set to `false` to disable view caching entirely.

{% tabs %}
{% tab title="Possible Values" %}
A directory path as a string or `false` to disable the view cache entirely
{% endtab %}

{% tab title="Default Value" %}
`app/cache/views`
{% endtab %}

{% tab title="Environment Variable" %}
`VIEW_CACHE`
{% endtab %}
{% endtabs %}

## Icon Configuration

The icon config is located at `app/config/icons.php`. Here is were file types are mapped to their respective icons. The mapping is a PHP array where the array key is the file extension (without a preceding dot) and the array value is the desired [Font Awesome](https://fontawesome.com/icons) class names.

{% code title="icons.php" %}
```php
return [
    'icons' => [
        '7z' => 'fas fa-file-archive',
        'aac' => 'fas fa-music',
        'accdb' => 'fas fa-database',
        'ai' => 'fas fa-image',
        'aif' => 'fas fa-music',
        'apk' => 'fab fa-android',
        'app' => 'fas fa-window',
        'avi' => 'fas fa-video',
        'bak' => 'fas fa-save',
        'bat' => 'fas fa-terminal',
        // etc...
    ],
];
```
{% endcode %}

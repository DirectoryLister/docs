# Cache Config Reference

The cache config is located at `app/config/cache.php`. These options control the application cache.

## `cache_driver`

> The application cache driver. Setting this value to `array` will disable the cache across requests. Additional driver-specific options may be required.

**Possible values** `apcu`, `array`, `file`, `memcached`, `redis`, `php-file`

**Default value**`file`

**Environment Variable**`CACHE_DRIVER`

## `cache_lifetime`

> The app cache lifetime \(in seconds\). If set to 0, cache indefinitely.

**Possible values**Any positive integer

**Default value**`0` \(indefinitely\)

**Environment Variable**`CACHE_LIFETIME`

## `memcached_host`

> The Memcached server hostname or IP address.

**Default value**`localhost`

**Environment Variables** `MEMCACHED_HOST`

## `memcached_port`

> The Memcached server port.

**Default value**`11211`

**Environment Variables** `MEMCACHED_PORT`

## `memcached_config`

> The Memcached configuration closure. This option is used when the `cache_driver` configuration option is set to `memcached`. The closure receives a Memcached object as it's only parameter. You can use this object to configure the Memcached connection. At a minimum you must connect to one or more Memcached servers via the `addServer()` or `addServers()` methods.
>
> Reference the [PHP Memcached documentation](https://secure.php.net/manual/en/book.memcached.php) for Memcached configuration options.

**Default value**Connects to a server at `localhost:11211`

## `redis_host`

> The Redis server hostname or IP address.

**Default value**`localhost`

**Environment Variables** `REDIS_HOST`

## `redis_port`

> The Redis server port.

**Default value**`6379`

**Environment Variables** `REDIS_PORT`

## `redis_config`

> The Redis configuration closure. This option is used when the `cache_driver` configuration option is set to `redis`. The closure receives a Redis object as it's only parameter. You can use this object to configure the Redis connection. At a minimum you must connect to one or more Redis servers via the `connect()` or `pconnect()` methods.
>
> Reference the [phpredis documentation](https://github.com/phpredis/phpredis#readme) for Redis configuration options.

**Default value**Connects to a server at `localhost:6379`

## `http_expires`

> HTTP expires values. An array of mimetypes mapped to their cache duration values.

**Possible values** An array of [mime types](https://developer.mozilla.org/en-US/docs/Web/HTTP/Basics_of_HTTP/MIME_types/Common_types) mapped to their cache duration as a [relative datetime string](https://www.php.net/manual/en/datetime.formats.relative.php).

**Default value**

```text
[
    'application/zip' => '+1 hour',
    'text/json' => '+1 hour',
]
```

## `view_cache`

> Path to the view cache directory. Set to 'false' to disable view caching entirely.

**Possible values**A directory path as a string or `false` to disable the view cache entirely

**Default value**`app/cache/views`

**Environment Variable**`VIEW_CACHE`


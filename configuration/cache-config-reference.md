# Cache Config Reference

The cache config is located at `app/config/cache.php`. These options control the application cache.

## `cache_driver`

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

## `cache_lifetime`

The app cache lifetime \(in seconds\). Setting this value to `0` will cache indefinitely.

{% tabs %}
{% tab title="Possible values" %}
Any positive integer
{% endtab %}

{% tab title="Default Value" %}
`60` \(one hour\)
{% endtab %}

{% tab title="Environment Variable" %}
`CACHE_LIFETIME`
{% endtab %}
{% endtabs %}

## `cache_lottery`

Some cache drivers require manually pruning the cache periodically to remove expired items. This is the percentage chance \(out of 100\) of a request "winning" the lottery causing the cache to be pruned.

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

## `memcached_host`

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

## `memcached_port`

The Memcached server port.

{% tabs %}
{% tab title="Possible Values" %}
Any valid port as an integer \(`0` to `65353`\)
{% endtab %}

{% tab title="Default Value" %}
`11211`
{% endtab %}

{% tab title="Environment Variable" %}
`MEMCACHED_PORT`
{% endtab %}
{% endtabs %}

## `memcached_config`

The Memcached configuration [anonymous function](https://www.php.net/manual/en/functions.anonymous.php) \(closure\). This option is used when the `cache_driver` configuration option is set to `memcached`. The closure receives a `Memcached` object as it's only parameter. You can use this object to configure the Memcached connection. At a minimum you must connect to one or more Memcached servers via the `addServer()` or `addServers()` methods.

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

This closure adds a single connection to a server at the host defined by [`memcached_host`](cache-config-reference.md#memcached_host) on the port defined by [`memcached_port`](cache-config-reference.md#memcached_port).
{% endtab %}

{% tab title="Environment Variables" %}
Uses the `MEMCACHED_HOST` and `MEMCACHED_PORT` variables by default
{% endtab %}
{% endtabs %}

## `redis_host`

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

## `redis_port`

The Redis server port.

{% tabs %}
{% tab title="Possible Values" %}
Any valid port as an integer \(`0` to `65353`\)
{% endtab %}

{% tab title="Defualt Value" %}
`6379`
{% endtab %}

{% tab title="Environment Variable" %}
`REDIS_PORT`
{% endtab %}
{% endtabs %}

## `redis_config`

The Redis configuration [anonymous function](https://www.php.net/manual/en/functions.anonymous.php) \(closure\). This option is used when the `cache_driver` configuration option is set to `redis`. The closure receives a `Redis` object as it's only parameter. You can use this object to configure the Redis connection. At a minimum you must connect to one or more Redis servers via the `connect()` or `pconnect()` methods.

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

This closure adds a single connection to a server at the host defined by [`redis_host`](cache-config-reference.md#redis_host) on the port defined by [`redis_port`](cache-config-reference.md#redis_port).
{% endtab %}

{% tab title="Environment Variables" %}
Uses the `REDIS_HOST` and `REDIS_PORT` variables by default
{% endtab %}
{% endtabs %}

## `http_cache`

HTTP cache values for controlling browser page cache durations. An array of mimetypes mapped to their cache duration in seconds..

{% tabs %}
{% tab title="Possible Values" %}
An array of [mime types](https://developer.mozilla.org/en-US/docs/Web/HTTP/Basics_of_HTTP/MIME_types/Common_types) mapped to their cache duration as a seconds \(integers\).
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

## `view_cache`

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


The cache config is located at `app/config/cache.php`. These options control the application cache.

---

### `cache_driver`

> The application cache driver. Setting this value to `array` will disable the cache across requests. Additional driver-specific options may be required.

<dl>
    <dt><strong>Possible values</strong></dt>
    <dd>
        <code>apcu</code>, <code>array</code>, <code>file</code>, <code>memcached</code>, <code>redis</code>, <code>php-file</code>
    </dd>
</dl>

<dl>
    <dt><strong>Default value</strong></dt>
    <dd><code>file</code></dd>
</dl>

<dl>
    <dt><strong>Environment Variable</strong></dt>
    <dd><code>CACHE_DRIVER</code></dd>
</dl>

---

### `cache_lifetime`

> The app cache lifetime (in seconds). If set to 0, cache indefinitely.

<dl>
    <dt><strong>Possible values</strong></dt>
    <dd>Any positive integer</dd>
</dl>

<dl>
    <dt><strong>Default value</strong></dt>
    <dd><code>0</code> (indefinitely)</dd>
</dl>

<dl>
    <dt><strong>Environment Variable</strong></dt>
    <dd><code>CACHE_LIFETIME</code></dd>
</dl>

---

### `memcached_config`

> The Memcached configuration closure. This option is used when the `cache_driver` configuration option is set to `memcached`. The closure receives a Memcached object as it's only parameter. You can use this object to configure the Memcached connection. At a minimum you must connect to one or more Memcached servers via the `addServer()` or `addServers()` methods.
>
> Reference the [PHP Memcached documentation](https://secure.php.net/manual/en/book.memcached.php) for Memcached configuration options.

<dl>
    <dt><strong>Default value</strong></dt>
    <dd>A pre-configured memcached instance pointing to <code>localhost:11211</code></dd>
</dl>

<dl>
    <dt><strong>Environment Variables</strong></dt>
    <dd>
        <code>MEMCACHED_HOST</code> (defualts to <code>localhost</code>)
        <br>
        <code>MEMCACHED_PORT</code> (defaults to <code>11211</code>)
    </dd>
</dl>

---

### `redis_config`

> The Redis configuration closure. This option is used when the `cache_driver` configuration option is set to `redis`. The closure receives a Redis object as it's only parameter. You can use this object to configure the Redis connection. At a minimum you must connect to one or more Redis servers via the `connect()` or `pconnect()` methods.
>
> Reference the [phpredis documentation](https://github.com/phpredis/phpredis#readme) for Redis configuration options.

<dl>
    <dt><strong>Default value</strong></dt>
    <dd>A pre-configured redis instance pointing to <code>localhost:6379</code></dd>
</dl>

<dl>
    <dt><strong>Environment Variables</strong></dt>
    <dd>
        <code>REDIS_HOST</code> (defualts to <code>localhost</code>)
        <br>
        <code>REDIS_PORT</code> (defaults to <code>6379</code>)
    </dd>
</dl>

---

### `http_expires`

> HTTP expires values.
> An array of mimetypes mapped to their cache duration values.

<dl>
    <dt><strong>Possible values</strong></dt>
    <dd>
        An array of <a href="https://developer.mozilla.org/en-US/docs/Web/HTTP/Basics_of_HTTP/MIME_types/Common_types">mime types</a>
        mapped to their cache duration as a <a href="https://www.php.net/manual/en/datetime.formats.relative.php">relative datetime string</a>.
    </dd>
</dl>

<dl>
    <dt><strong>Default value</strong></dt>
    <dd>
<pre style="white-space: pre;"><code>[
    'application/zip' => '+1 hour',
    'text/json' => '+1 hour',
]</code></pre>
    </dd>
</dl>

---

### `view_cache`

> Path to the view cache directory. Set to 'false' to disable view caching entirely.

<dl>
    <dt><strong>Possible values</strong></dt>
    <dd>A directory path as a string or <code>false</code> to disable the view cache entirely</dd>
</dl>

<dl>
    <dt><strong>Default value</strong></dt>
    <dd><code>app/cache/views</code></dd>
</dl>

<dl>
    <dt><strong>Environment Variable</strong></dt>
    <dd><code>VIEW_CACHE</code></dd>
</dl>

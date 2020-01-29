The view config is located at `app/config/view.php` and controls view-related settings.

### `dark_mode`

> Enable dark mode.

<dl>
    <dt><strong>Possible values</strong></dt>
    <dd><code>true</code> or <code>false</code></dd>
</dl>

<dl>
    <dt><strong>Default value</strong></dt>
    <dd><code>false</code></dd>
</dl>

<dl>
    <dt><strong>Environment Variable</strong></dt>
    <dd><code>DARK_MODE</code></dd>
</dl>

---

### `date_format`

> The format used for rendering dates in the application views.

<dl>
    <dt><strong>Possible values</strong></dt>
    <dd>See the <a href="https://www.php.net/manual/en/function.date.php#refsect1-function.date-parameters">PHP <code>date</code> format documentation</a> for possible values.</dd>
</dl>

<dl>
    <dt><strong>Default value</strong></dt>
    <dd><code>Y-m-d H:i:s</code></dd>
</dl>

<dl>
    <dt><strong>Environment Variable</strong></dt>
    <dd><code>DATE_FORMAT</code></dd>
</dl>

---

### `cache`

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
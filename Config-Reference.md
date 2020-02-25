The app config is located at `app/config/app.php`. These options control core application functionality.

---

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

### `debug`

> Enable application debugging and display error messages.

#### !!! WARNING !!!

It is recommended that debug remains OFF unless troubleshooting an issue.
Leaving this enabled WILL cause leakage of sensitive server information.

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
    <dd><code>APP_DEBUG</code></dd>
</dl>

---

### `display_readmes`

> Parse and render README files on the page.

<dl>
    <dt><strong>Possible values</strong></dt>
    <dd><code>true</code> or <code>false</code></dd>
</dl>

<dl>
    <dt><strong>Default value</strong></dt>
    <dd><code>true</code></dd>
</dl>

<dl>
    <dt><strong>Environment Variable</strong></dt>
    <dd><code>DISPLAY_READMES</code></dd>
</dl>

---

### `google_analytics_id`

> Your Google analytics tracking ID.

<dl>
    <dt><strong>Possible values</strong></dt>
    <dd>A string in the format of <code>UA-123456789-0</code> or <code>false</code> to disable</dd>
</dl>

<dl>
    <dt><strong>Default value</strong></dt>
    <dd><code>false</code></dd>
</dl>

<dl>
    <dt><strong>Environment Variable</strong></dt>
    <dd><code>GOOGLE_ANALYTICS_ID</code></dd>
</dl>

---

### `hidden_files`

> Array of files that will be hidden from the listing. Supports glob patterns.

<dl>
    <dt><strong>Possible values</strong></dt>
    <dd>An array of path strings</dd>
</dl>

<dl>
    <dt><strong>Default value</strong></dt>
    <dd><code>[]</code> (empty array)</dd>
</dl>

#### Example

```php
'hidden_files' => [
    'somefile.txt', // Matches 'somefile.txt' exactly
    'README.*', // Matches files named 'README' with any file extension
    'foo/*', // Matches all files in the 'foo' directory
    'schema.{ya?ml}', // Matches 'schema.yml' or 'schema.yaml'
]
```

---

### `hide_app_files`

> Hide application specific files/directories (i.e. `index.php` and the `app` folder).

<dl>
    <dt><strong>Possible values</strong></dt>
    <dd><code>true</code> or <code>false</code></dd>
</dl>

<dl>
    <dt><strong>Default value</strong></dt>
    <dd><code>true</code></dd>
</dl>

<dl>
    <dt><strong>Environment Variable</strong></dt>
    <dd><code>HIDE_APP_FILES</code></dd>
</dl>

---

### `hide_vcs_files`

> Hide the files Version Control System (i.e. Git and Mercurial) use to store their metadata.

<dl>
    <dt><strong>Possible values</strong></dt>
    <dd><code>true</code> or <code>false</code></dd>
</dl>

<dl>
    <dt><strong>Default value</strong></dt>
    <dd><code>true</code></dd>
</dl>

<dl>
    <dt><strong>Environment Variable</strong></dt>
    <dd><code>HIDE_VCS_FILES</code></dd>
</dl>

---

### `language`

> The application interface language.

<dl>
    <dt><strong>Possible values</strong></dt>
    <dd>See the <a href="https://github.com/DirectoryLister/DirectoryLister/tree/master/app/translations">
        <code>app/translations</code>
    </a> folder for available translations.</dd>
</dl>

<dl>
    <dt><strong>Default value</strong></dt>
    <dd><code>en</code> (English)</dd>
</dl>

<dl>
    <dt><strong>Environment Variable</strong></dt>
    <dd><code>APP_LANGUAGE</code></dd>
</dl>

---

### `max_hash_size`

> The maximum file size (in bytes) that can be hashed. This helps to prevent timeouts for excessively large files.

<dl>
    <dt><strong>Possible values</strong></dt>
    <dd>Any positive integer <code>0</code> - <code>9223372036854775807</code></dd>
</dl>

<dl>
    <dt><strong>Default value</strong></dt>
    <dd><code>1000000000</code> (<code>1GB</code>)</dd>
</dl>

<dl>
    <dt><strong>Environment Variable</strong></dt>
    <dd><code>MAX_HASH_SIZE</code></dd>
</dl>

---

### `reverse_sort`

> When enabled, reverses the order of files (after sorting is applied).

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
    <dd><code>REVERSE_SORT</code></dd>
</dl>

---

### `sort_order`

> Sorting order of files and folders. Can be one of several predefined values or a custom [anonymous function](https://www.php.net/manual/en/functions.anonymous.php).

<dl>
    <dt><strong>Possible values</strong></dt>
    <dd>
        <code>type</code>, <code>natural</code>, <code>name</code>, <code>accessed</code>, <code>changed</code>, <code>modified</code>, <code>&lt;anonymous function&gt;</code>
    </dd>
</dl>

<dl>
    <dt><strong>Default value</strong></dt>
    <dd><code>type</code></dd>
</dl>

<dl>
    <dt><strong>Environment Variable</strong></dt>
    <dd><code>SORT_ORDER</code></dd>
</dl>

#### Anonymous Function Example

The anonymous function receives two `\SplFileInfo` objects as arguments and expects an integer to be returned.

```php
'sort_order' => function (SplFileInfo $file1, SplFileInfo $file2) {
    return strcmp($file1->getRealPath(), $file2->getRealPath());
});
```

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

---

### `zip_downloads`

> Enable downloading of directories as a zip archive.

<dl>
    <dt><strong>Possible values</strong></dt>
    <dd><code>true</code> or <code>false</code></dd>
</dl>

<dl>
    <dt><strong>Default value</strong></dt>
    <dd><code>true</code></dd>
</dl>

<dl>
    <dt><strong>Environment Variable</strong></dt>
    <dd><code>ZIP_DOWNLOADS</code></dd>
</dl>

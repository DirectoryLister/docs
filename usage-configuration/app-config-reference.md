# App Config Reference

The app config is located at `app/config/app.php`. These options control core application functionality.

## `dark_mode` • ℹ️ Removed in v3.7.0

> Enable dark mode.

**Possible values**`true` or `false`

**Default value**`false`

**Environment Variable**`DARK_MODE`

## `date_format`

> The format used for rendering dates in the application views.

**Possible values**See the [PHP `date` format documentation](https://www.php.net/manual/en/function.date.php#refsect1-function.date-parameters) for possible values.

**Default value**`Y-m-d H:i:s`

**Environment Variable**`DATE_FORMAT`

## `debug`

> Enable application debugging and display error messages.

### !!! WARNING !!!

It is recommended that debug remains OFF unless troubleshooting an issue. Leaving this enabled WILL cause leakage of sensitive server information.

**Possible values**`true` or `false`

**Default value**`false`

**Environment Variable**`APP_DEBUG`

## `display_readmes`

> Parse and render README files on the page.

**Possible values**`true` or `false`

**Default value**`true`

**Environment Variable**`DISPLAY_READMES`

## `google_analytics_id`

> Your Google analytics tracking ID.

**Possible values**A string in the format of `UA-123456789-0` or `false` to disable

**Default value**`false`

**Environment Variable**`GOOGLE_ANALYTICS_ID`

## `hidden_files_list`

> File containing hidden file definitions. Will be merged with definitions from the 'hidden\_files' configuration option.

**Possible values**A path string to a file

**Default value**`.hidden`

**Environment Variable**`HIDDEN_FILES_LIST`

## `hidden_files`

> Array of hidden file definitions. Will be merged with definitions in the file defined in the 'hidden\_files\_list' configuration option. Supports glob patterns \(e.g. \*.txt, file.{yml,yaml}, etc.\).

**Possible values**An array of path strings

**Default value**`[]` \(An empty array\)

### Example

```php
'hidden_files' => [
    'somefile.txt', // Matches 'somefile.txt' exactly
    'README.*', // Matches files named 'README' with any file extension
    'foo/*', // Matches all files in the 'foo' directory
    'schema.{ya?ml}', // Matches 'schema.yml' or 'schema.yaml'
]
```

## `hide_app_files`

> Hide application specific files/directories \(i.e. `index.php` and the `app` folder\).

**Possible values**`true` or `false`

**Default value**`true`

**Environment Variable**`HIDE_APP_FILES`

## `hide_vcs_files`

> Hide the files Version Control System \(i.e. Git and Mercurial\) use to store their metadata.

**Possible values**`true` or `false`

**Default value**`true`

**Environment Variable**`HIDE_VCS_FILES`

## `home_text`

> Text of the `home` link in the navigation breadcrumbs. If undefined or null will use the translated form of "home" from your selected language.

**Possible values**Any string

**Default value**`null`

**Environment Variable**`HOME_TEXT`

## `language`

> The application interface language.

**Possible values**See the [`app/translations`](https://github.com/DirectoryLister/DirectoryLister/tree/master/app/translations) folder for available translations.

**Default value**`en` \(English\)

**Environment Variable**`APP_LANGUAGE`

## `matomo_analytics_site_id`

> Your Matomo analytics site ID.

**Default value**`false`

**Environment Variable**`MATOMO_ANALYTICS_SITE_ID`

## `matomo_analytics_url`

> Your Matomo analytics URL.

**Default value**`false`

**Environment Variable**`MATOMO_ANALYTICS_URL`

## `max_hash_size`

> The maximum file size \(in bytes\) that can be hashed. This helps to prevent timeouts for excessively large files.

**Possible values**Any positive integer `0` - `9223372036854775807`

**Default value**`1000000000` \(`1GB`\)

**Environment Variable**`MAX_HASH_SIZE`

## `meta_description`

> Meta tag description text.

**Possible values**Any string

**Default value**`Yet another directory listing, powered by Directory Lister.`

**Environment Variable**`META_DESCRIPTION`

## `readmes_first`

> Show READMEs before the file listing.

**Possible values**`true` or `false`

**Default value**`false`

**Environment Variable**`READMES_FIRST`

## `reverse_sort`

> When enabled, reverses the order of files \(after sorting is applied\).

**Possible values**`true` or `false`

**Default value**`false`

**Environment Variable**`REVERSE_SORT`

## `site_title`

> The title of your directory listing. This will be displayed in the browser tab/title bar along with the current path.

**Possible values**Any string

**Default value**`Directory Lister`

**Environment Variable**`SITE_TITLE`

## `sort_order`

> Sorting order of files and folders. Can be one of several predefined values or a custom [anonymous function](https://www.php.net/manual/en/functions.anonymous.php).

**Possible values** `type`, `natural`, `name`, `accessed`, `changed`, `modified`, `<anonymous function>`

**Default value**`type`

**Environment Variable**`SORT_ORDER`

### Anonymous Function Example

When using an anonymous function it must be wrapped in a `\DI\value()` function. The anonymous function receives two `\SplFileInfo` objects as arguments and expects an integer to be returned.

```php
'sort_order' => \DI\value(
    function (SplFileInfo $file1, SplFileInfo $file2) {
        return strcmp($file1->getRealPath(), $file2->getRealPath());
    })
);
```

## `timezone`

> Timezone used for date formatting.

**Possible values**For a list of supported timezones see: [https://www.php.net/manual/en/timezones.php](https://www.php.net/manual/en/timezones.php).

**Default value**The server's timezone

**Environment Variable**`TIMEZONE`

## `view_cache`

> Path to the view cache directory. Set to 'false' to disable view caching entirely.

**Possible values**A directory path as a string or `false` to disable the view cache entirely

**Default value**`app/cache/views`

**Environment Variable**`VIEW_CACHE`

## `zip_downloads`

> Enable downloading of directories as a zip archive.

**Possible values**`true` or `false`

**Default value**`true`

**Environment Variable**`ZIP_DOWNLOADS`

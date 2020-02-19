Directory Lister is customizable through configuration. You can configure Directory Lister in a few different ways.

The `.env` File
===============

Simple configuration changes are possible via a custom `.env` file. This file defines environment variables and their value. To get started:

  1. Copy `.env.example` to `.env`
  2. Edit the configuration values in `.env`

Your default `.env` file should look something like this:

    DARK_MODE=false

    DISPLAY_READMES=true

    ZIP_DOWNLOADS=true

    GOOGLE_ANALYTICS_ID=false

    SORT_ORDER=type
    REVERSE_SORT=false

    HIDE_APP_FILES=true
    HIDE_VCS_FILES=true

    DATE_FORMAT="Y-m-d H:i:s"

    MAX_HASH_SIZE=1000000000

Application Config
==================

More control can be achieved via the application config files located in `app/config`. Here you have full control over each option and can even write full PHP code if desired. The application configs are broken up into separate files based on their use. Reference the individual config documentation for more information about individual application configuration options.

See the [Config Reference](https://github.com/DirectoryLister/DirectoryLister/wiki/Config-Reference) for more information about individual options.

Icon Configuration
==================

You can control your application icon mapping through the icon config file.

Reference the [Icon Configuration](https://github.com/DirectoryLister/DirectoryLister/wiki/Icon-Configuration) for more information on configuring icons.

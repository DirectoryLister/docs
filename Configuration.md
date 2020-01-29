Directory Lister is customizable through configuration. You can configure Directory Lister in a few different ways.

# The `.env` File

Simple configuration changes are possible via a custom `.env` file. To get started

  1. Copy `.env.example` to `.env`
  2. Edit the configuration values in `.env`

Your default `.env` file should look something like this:

    DARK_MODE=false

    SORT_ORDER=type
    REVERSE_SORT=false

    HIDE_APP_FILES=true
    HIDE_VCS_FILES=true

    DISPLAY_READMES=true

    DATE_FORMAT="Y-m-d H:i:s"

    MAX_HASH_SIZE=1000000000

See the [.env Config Reference](https://github.com/DirectoryLister/DirectoryLister/wiki/.env-Config-Reference) for more information about individual options.

# Application Config

More control can be achieved via the application config files located in `app/config`. Here you have full control over each option and can even write full PHP code if desired. The application configs and are broken up into separate files based on their use. Reference the individual config documentation for more information about individual application configuration options.

  - [App (app.php) Config Reference]()
  - [Icon (icons.php) Config Reference]()
  - [View (view.php) Config Reference]()
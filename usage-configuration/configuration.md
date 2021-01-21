# Configuration

Directory Lister is customizable through configuration. You can configure Directory Lister in a few different ways.

## The `.env` File

Simple configuration changes are possible via a custom `.env` file. This file defines environment variables and their value. To get started:

1. Copy `.env.example` to `.env`
2. Edit the configuration values in `.env`

Your default `.env` file should look something like this:

```text
APP_DEBUG=false
APP_LANGUAGE=en

DISPLAY_READMES=true
READMES_FIRST=false
ZIP_DOWNLOADS=true

GOOGLE_ANALYTICS_ID=false

MATOMO_ANALYTICS_URL=false
MATOMO_ANALYTICS_ID=false

SORT_ORDER=type
REVERSE_SORT=false
```

## Application Config

More control can be achieved via the application config files located in `app/config`. Here you have full control over each option and can even write full PHP code if desired. The application configs are broken up into separate files based on their use. Reference the individual config documentation for more information about individual application configuration options.

See the [App Config](https://github.com/DirectoryLister/DirectoryLister/wiki/App-Config-Reference) or the [Cache Config](https://github.com/DirectoryLister/DirectoryLister/wiki/Cache-Config-Reference) references for more information about individual options.

## Icon Configuration

You can control your application icon mapping through the icon config file.

Reference the [Icon Configuration](https://github.com/DirectoryLister/DirectoryLister/wiki/Icon-Configuration) for more information on configuring icons.

Next: [Troubleshooting](https://github.com/DirectoryLister/DirectoryLister/wiki/Troubleshooting)


# Icon Configuration

The icon config is located at `app/config/icon.php`. Here is were file types are mapped to their respective icons. The mapping is a PHP array where the array key is the file extension \(without a preceding dot\) and the array value is the desired [Font Awesome](https://fontawesome.com/icons) class names.

### Example

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


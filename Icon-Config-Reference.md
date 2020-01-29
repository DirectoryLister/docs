The icon config is located at `app/config/icon.php`. Here is were file types are mapped to their respective icons. The mapping is a PHP array where the array key is the file extension (without a preceding dot) and the array value is the desired [Font Awesome](https://fontawesome.com/icons) class names.

Example:

```php
return [
    // Images
    'jpg' => 'fas fa-image',
    'png' => 'fas fa-image',

    // Data
    'json' => 'fas fa-file-alt',
    'yaml' => 'fas fa-file-alt',

    // Code
    'css' => 'fab fab fa-css3',
    'html' => 'fab fa-html5',
    'php' => 'fab fa-php',

    // etc...
```
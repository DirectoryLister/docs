# Code Analysis & Testing

## Coding Standards

Apply coding standards to all application and tests files

```text
app/vendor/bin/php-cs-fixer fix
npx eslint --fix app/resources/js/**/*.js
```

or to see the changes before applying

```text
app/vendor/bin/php-cs-fixer fix --diff --dry-run
npx eslint app/resources/js/**/*.js
```

## Static Analysis

```text
app/vendor/bin/psalm
```

## Unit/Feature Tests

```text
app/vendor/bin/phpunit
```

## Code Coverage

```text
app/vendor/bin/phpunit --coverage-text
```

or generate a more detailed HTML coverage report with

```text
app/vendor/bin/phpunit --coverage-html .coverage
```


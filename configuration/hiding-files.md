---
icon: square-dashed
---

# Hiding Files

By default Directory Lister will look for a `.hidden` file in the app root directory (the same place as `index.php`). If found, each line of this file will be used as an [ignore pattern](hiding-files.md#ignore-patterns). Each line should contain a single file or path pattern with no end-of-line delimiter.

{% hint style="info" %}
The `.hidden` file does not exist by default and must be created to be used.
{% endhint %}

{% hint style="info" %}
You can configure the `.hidden` file name via the [`hidden_file_list`](configuration-reference.md#hidden_files_list)configuration option.
{% endhint %}

## Ignore Patterns

An ignore pattern is a path to a file or folder that may contain one or more of the following special expressions.

{% hint style="warning" %}
Hidden file definitions are _case sensitive_. This means that `foo.txt` and `Foo.txt` are _not_ the same.
{% endhint %}

### Matching Expressions

* `?` matches any single character
* `*` matches zero or more characters excluding `/`
* `**` matches zero or more characters including `/`
* `[abc]` matches a single character from the set (i.e. `a`, `b` or `c`)
* `[a-c]` matches a single character in the range (i.e. `a`, `b` or `c`)
* `[^abc]` matches any character not in the set (i.e. not `a`, `b` or `c`)
* `[^a-c]` matches any character not in the range (i.e. not `a`, `b` or `c`)
* `{foo,bar,baz}` matches any pattern in the set (i.e. `foo`, `bar` or `baz`)

### Assertions

The following assertions can be used to assert that a path is followed by or not followed by another pattern.

* `(=foo)` matches any file name that also contains `foo`
* `(!foo)` matches any file name that does not also contain `foo`

### Folders

A pattern matching a folder path will cause all files and folders within that folder to be hidden as well as the folder itself.

## Examples

**`foo`** Match the literal file or folder `foo` in the root folder

**`foo/bar`** Matches the literal file or folder `bar` in the `foo` folder

**`*.txt`** Matches any file or folder ending with `.txt` in the root folder

**`**/*.txt`** Matches any file or folder ending with `.txt` one or more folders deep (e.g. `foo/bar.txt` or `foo/bar/baz.txt`)

**`**.txt`** Matches any file or folder ending with `.txt` (e.g. `foo.txt`, `foo/bar.txt`, `foo/bar/baz.txt`, etc.)

**`foo/bar/*.txt`** Matches all `.txt` files or folders in the `foo/bar` folder

**`foo/bar/**.txt`** Matches all `.txt` files or folders in the `foo/bar` folder and sub-folders

**`file.{yml,yaml}`** Matches a file or folder named `file.yml` or `file.yaml` in the root folder

**`file.tar(!.{gz,xz})`** Matches a file named `file.tar` or `file.tar.bz` but not `file.tar.gz` or `file.tar.xz`

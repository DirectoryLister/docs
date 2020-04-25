By default Directory Lister will look for a `.hidden` file in the app root directory (the same place as `index.php`). If found, each line of this file will be used as an ignore pattern. Each line should contain a single file or path pattern with no end-of-line delimiter.

> ℹ️ The `.hidden` file does not exist by default and must be created to be used.

> ℹ️ You can configure the `.hidden` file name via the [`hiden_file_list`](https://github.com/DirectoryLister/DirectoryLister/wiki/Config-Reference#hidden_files_list) configuration option.

Ignore Patterns
---------------

An ignore pattern is a path to a file or folder that may contain one or more of the following special expressions. A pattern matching a folder path will cause all files and folders within that folder to be hidden as well as the folder itself.

#### Matching Expressions

  - `?` matches any single character
  - `*` matches zero or more characters excluding `/`
  - `**` matches zero or more characters including `/`
  - `[abc]` matches a single character from the set (i.e. `a`, `b` or `c`)
  - `[a-c]` matches a single character in the range (i.e. `a`, `b` or `c`)
  - `[^abc]` matches any character not in the set (i.e. not `a`, `b` or `c`)
  - `[^a-c]` matches any character not in the range (i.e. not `a`, `b` or `c`)
  - `{foo,bar,baz}` matches any pattern in the set (i.e. `foo`, `bar` or `baz`)

Examples
--------

<dl>
    <dt><code>foo</code></dt>
    <dd>Matches the literal file or folder <code>foo</code> in the root folder</dd>
</dl>

<dl>
    <dt><code>foo/bar</code></dt>
    <dd>Matches the literal file or folder <code>bar</code> in the <code>foo</code> folder</dd>
</dl>

<dl>
    <dt><code>*.txt</code></dt>
    <dd>Matches any file or folder ending with <code>.txt</code> in the root folder</dd>
</dl>

<dl>
    <dt><code>**/*.txt</code></dt>
    <dd>Matches any file or folder ending with <code>.txt</code> one or more folders deep (e.g. <code>foo/bar.txt</code> or <code>foo/bar/baz.txt</code>)</dd>
</dl>

<dl>
    <dt><code>**.txt</code></dt>
    <dd>Matches any file or folder ending with <code>.txt</code> (e.g. <code>foo.txt</code>, <code>foo/bar.txt</code>, <code>foo/bar/baz.txt</code>, etc.)</dd>
</dl>

<dl>
    <dt><code>foo/bar/*.txt</code></dt>
    <dd>Matches all <code>.txt</code> files or folders in the <code>foo/bar</code> folder</dd>
</dl>

<dl>
    <dt><code>foo/bar/**.txt</code></dt>
    <dd>Matches all <code>.txt</code> files or folders in the <code>foo/bar</code> folder and subfolders</dd>
</dl>

<dl>
    <dt><code>file.{yml,yaml}</code></dt>
    <dd>Matches a file or folder named <code>file.yml</code> or <code>file.yaml</code> in the root folder</dd>
</dl>


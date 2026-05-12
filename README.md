<!-- Start documentation -->
# TeachBooks Fetch

A Sphinx extension that allows fetching of other HTML elements after DOM load.

This extension introduces two new directives:

- `fetch`: Fetches content from a specified reference and inserts it into the rendered document.
- `click-to-fetch`: Creates a clickable element that, when clicked, fetches content from a specified reference and inserts it into the rendered document.

## Installation

```bash
pip install teachbooks-fetch
```

## Activation

### Jupyter Book

Add the extension to your `_config.yml`:

```yaml
sphinx:
  extra_extensions:
    - teachbooks_fetch
```

### Sphinx

Add the extension to your `conf.py`:

```python
extensions = [
    # ...
    'teachbooks_fetch',
]
```

## Configuration

Currently no configuration options are available for this extension.

## Usage

### Fetch Directive

The `fetch` directive allows you to fetch content from a specified reference and insert it into the rendered document.

Minimal usage (MyST syntax):

```
:::{fetch} <ref>
:::
```

Replace `<ref>` with code that generates a reference to the content you want to fetch. This can be one of the following:
- A markdown style link, e.g. `[link text](url#id)`.
- An internal reference using the roles `ref`, `numref`, `prf:ref` (see [Sphinx Proof](https://sphinx-proof.readthedocs.io/en/latest/syntax.html)) or `bdg-link-<name>` (see [Sphinx Design](https://sphinx-design.readthedocs.io/en/latest/badges_buttons.html#badges)).
- A HTML link, e.g. `<a href="url#id">link text</a>`.

This will, initially, render a placeholder admonition with the following base MyST code:

```
:::{admonition} Fetching <ref>
:class: fetch
Content loading...
:::
```

After the DOM has loaded, the extension will attempt to fetch the content from the specified reference and replace the placeholder with the fetched content. If the fetch fails, the content of the placeholder will be updated to indicate that the fetch failed.

If preferred, you can also specify the content of the placeholder by including content in the directive:

```
:::{fetch} <ref>
This content will be shown while the fetch is in progress.
:::
```

If preferred, you can also specify the title of the placeholder by including the `title` option:

```
:::{fetch} <ref>
:title: Searching for [!a!]
:::
```

Here `[!a!]` will be replaced with reference given in the directive argument.

If preferred, you can also specify additional CSS classes for the placeholder by including the `class` option:

```
:::{fetch} <ref>
:class: my-custom-class
:::
```

### Click-to-Fetch Directive

The `click-to-fetch` directive allows you to create a clickable element that, when clicked, fetches content from a specified reference and inserts it into the rendered document.

Minimal usage (MyST syntax):

```
:::{click-to-fetch} <ref>
:::
```

This will, initially, render a placeholder admonition with the following base MyST code:

```
:::{admonition} Click to fetch <ref>
:class: fetch click-to-fetch
Waiting for a click...
:::
```

All options, content and behavior for the `fetch` directive are also available for the `click-to-fetch` directive. The only difference is that the `click-to-fetch` directive will not attempt to fetch the content until the user clicks on the placeholder.

If the click-to-fetch behavior is preferred without changing the default placeholder, you can also use the `fetch` directive with the `click-to-fetch` class.

<!-- Start examples -->
## Examples

Examples can be found here: [TeachBooks Manual](https://teachbooks.io/manual/_git/github.com_TeachBooks_TeachBooks-Fetch/main/MANUAL.html#Examples)

<!-- Start contribute -->
## Contribute

This tool's repository is stored on [GitHub](https://github.com/TeachBooks/TeachBooks-Questions). If you'd like to contribute, you can create a fork and open a pull request on the [GitHub repository](https://github.com/TeachBooks/TeachBooks-Questions).
````{margin}

```{note}

{bdg-primary}`Sphinx Extension`

```

```{seealso}

[{octicon}`mark-github` Repository](https://github.com/TeachBooks/TeachBooks-Fetch)

```
````

:::{include} README.md
:start-after: "<!-- Start documentation -->"
:end-before: "<!-- Start examples -->"
:::

## Examples

### Fetch Directive

An example of the `fetch` directive with a reference to a figure with the name `sticky_basic`:

```
:::{fetch} {numref}`sticky_basic`
:::
```

Before fetching the placeholder of the `fetch` directive will be:

:::{admonition} Fetching {numref}`sticky_basic`
:class: fetch
Content loading...
:::

After successfully fetching the content from the specified reference, the placeholder will be replaced with the fetched content, in this case resulting in:

:::{fetch} {numref}`sticky_basic`
:::

If the fetch fails, the content of the placeholder will be updated to indicate that the fetch failed:

:::{admonition} Failed to fetch {numref}`sticky_basic`
:class: fetch failed-to-fatch
Fetching failed.
:::

### Click-to-Fetch Directive

An example of the `click-to-fetch` directive with a reference to a figure with the name `sticky_basic`:

```
:::{click-to-fetch} {numref}`sticky_basic`
:::
```

Before fetching the placeholder of the `click-to-fetch` directive will be:

:::{click-to-fetch} {numref}`sticky_basic`
:::

Click on the above placeholder to fetch the content from the specified reference.


:::{include} README.md
:start-after: "<!-- Start contribute -->"
:::

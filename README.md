# endoflife-date/supported-versions

**⚠️: This action is currently WIP and does not work. Feedback is welcome [on this discussion](https://github.com/endoflife-date/endoflife.date/discussions/2700)**

This action returns a list of supported versions for a product (such as php/ruby/python/etc)
using the [endoflife.date](https://endoflife.date) [API](https://endoflife.date/docs/api).

Note: This currently uses the v1 API, which is currently still under development.

## Inputs

## `product`

**Required** The name of the product, as per the page URL. You can also use an alternate URL, for ease of use.

Examples: `php`, `ruby`, `kubernetes`, `k8s`.

## `is-actively-supported`

**Optional** Whether to only return actively supported release cycles. Default `false`.

The meaning of active support varies from product to product. Please see the API response for the product against the `support`
field to see what it means for that product.

## `is-not-eol`

**Optional** Whether to only return non-EOL release cycles. Default `false`.

The meaning of EOL varies from product to product. Please see the API response for the product against the `eol`
field to see what it means for that product.

## `is-lts`

**Optional** Whether to only return LTS release cycles. Default `false`.

The meaning of LTS varies from product to product. Please see the API response for the product against the `lts`
field to see what it means for that product.

## `is-extended-support`

**Optional** Whether to only return extended support release cycles. Default `false`.

The meaning of extended support varies from product to product. 
Please see the API response for the product against the `extendedSupport` field to see what it means for that product.

## Outputs

## `release-cycles-list`

List of release cycles that matched the applied filters. A list of strings.

Example: `["8.2", "8.1", "8.0"]`

## `latest-versions`

List of latest versions that matched the applied filters.

Example: `["8.0.28", "8.1.17", "8.2.4"]`

## `metadata`

Returns complete unfiltered metadata from the API.

Example: See content at <https://deploy-preview-2080--endoflife-date.netlify.app/api/v1/products/python/>

## `matched-cycles`

Returns a list of releases that matched the applied filters, with complete metadata

<details markdown=1><summary>Example</summary>

```json
[
  {
    "name": "3.11",
    "codename": null,
    "label": "3.11",
    "date": "2022-10-24",
    "support": null,
    "lts": false,
    "eol": "2027-10-24",
    "discontinued": null,
    "extendedSupport": null,
    "latest": {
      "name": "3.11.2",
      "date": "2023-02-07",
      "link": "https://www.python.org/downloads/release/python-3112/"
    }
  },
  {
    "name": "3.10",
    "codename": null,
    "label": "3.10",
    "date": "2021-10-04",
    "support": null,
    "lts": false,
    "eol": "2026-10-04",
    "discontinued": null,
    "extendedSupport": null,
    "latest": {
      "name": "3.10.10",
      "date": "2023-02-07",
      "link": "https://www.python.org/downloads/release/python-31010/"
    }
  },
  {
    "name": "3.9",
    "codename": null,
    "label": "3.9",
    "date": "2020-10-05",
    "support": null,
    "lts": false,
    "eol": "2025-10-05",
    "discontinued": null,
    "extendedSupport": null,
    "latest": {
      "name": "3.9.16",
      "date": "2022-12-06",
      "link": "https://www.python.org/downloads/release/python-3916/"
    }
  },
  {
    "name": "3.8",
    "codename": null,
    "label": "3.8",
    "date": "2019-10-14",
    "support": null,
    "lts": false,
    "eol": "2024-10-14",
    "discontinued": null,
    "extendedSupport": null,
    "latest": {
      "name": "3.8.16",
      "date": "2022-12-06",
      "link": "https://www.python.org/downloads/release/python-3816/"
    }
  },
  {
    "name": "3.7",
    "codename": null,
    "label": "3.7",
    "date": "2018-06-26",
    "support": null,
    "lts": false,
    "eol": "2023-06-27",
    "discontinued": null,
    "extendedSupport": null,
    "latest": {
      "name": "3.7.16",
      "date": "2022-12-06",
      "link": "https://www.python.org/downloads/release/python-3716/"
    }
  }
]
```

</details>

## Example usage

Note: All examples based against a date of 17th March 2023.

## Get list of supported Python versions

```yaml
uses: endoflife-date/supported-versions@v1
with:
  product: python
  is-not-eol: true
```

<details markdown=1><summary>Sample Outputs</summary>

```json5
"release-cycles-list": ["3.11", "3.10", "3.9", "3.8"]
"latest-versions": ["3.11.2", "3.10.10", "3.9.16", "3.8.16", "3.7.16"]
# Same as the content of the URL, not the URL itself
"metadata": "https://deploy-preview-2080--endoflife-date.netlify.app/api/v1/products/python/"
"cycles": [
  {
    "name": "3.11",
    "codename": null,
    "label": "3.11",
    "date": "2022-10-24",
    "support": null,
    "lts": false,
    "eol": "2027-10-24",
    "discontinued": null,
    "extendedSupport": null,
    "latest": {
      "name": "3.11.2",
      "date": "2023-02-07",
      "link": "https://www.python.org/downloads/release/python-3112/"
    }
  },
  {
    "name": "3.10",
    "codename": null,
    "label": "3.10",
    "date": "2021-10-04",
    "support": null,
    "lts": false,
    "eol": "2026-10-04",
    "discontinued": null,
    "extendedSupport": null,
    "latest": {
      "name": "3.10.10",
      "date": "2023-02-07",
      "link": "https://www.python.org/downloads/release/python-31010/"
    }
  },
  {
    "name": "3.9",
    "codename": null,
    "label": "3.9",
    "date": "2020-10-05",
    "support": null,
    "lts": false,
    "eol": "2025-10-05",
    "discontinued": null,
    "extendedSupport": null,
    "latest": {
      "name": "3.9.16",
      "date": "2022-12-06",
      "link": "https://www.python.org/downloads/release/python-3916/"
    }
  },
  {
    "name": "3.8",
    "codename": null,
    "label": "3.8",
    "date": "2019-10-14",
    "support": null,
    "lts": false,
    "eol": "2024-10-14",
    "discontinued": null,
    "extendedSupport": null,
    "latest": {
      "name": "3.8.16",
      "date": "2022-12-06",
      "link": "https://www.python.org/downloads/release/python-3816/"
    }
  },
  {
    "name": "3.7",
    "codename": null,
    "label": "3.7",
    "date": "2018-06-26",
    "support": null,
    "lts": false,
    "eol": "2023-06-27",
    "discontinued": null,
    "extendedSupport": null,
    "latest": {
      "name": "3.7.16",
      "date": "2022-12-06",
      "link": "https://www.python.org/downloads/release/python-3716/"
    }
  }
]
```

</details>

## Get list of Supported Node.JS LTS versions

```yaml
uses: endoflife-date/supported-versions@v1
with:
  product: nodejs
  is-not-eol: true
  is-lts: true
```

### Sample Output:

```json5
"release-cycles-list": ["18", "16", "14"]
"latest-versions": ["18.15.0", "16.19.1", "14.21.3"]
# Same as the content of the URL, not the URL itself
"metadata": "https://deploy-preview-2080--endoflife-date.netlify.app/api/v1/products/nodejs/"
```

## Get list of actively supported PHP versions

```yaml
uses: endoflife-date/supported-versions@v1
with:
  product: php
  is-actively-supported: true
```

### Sample Output:

```json5
"release-cycles-list": ["8.2", "8.1"]
"latest-versions": ["8.2.4", "8.1.17"]
# Same as the content of the URL, not the URL itself
"metadata": "https://deploy-preview-2080--endoflife-date.netlify.app/api/v1/products/php/"
```

## Get supported Kubernetes versions:

```yaml
uses: endoflife-date/supported-versions@v1
with:
  # Note that this is an alternate URL, for shorthand. https://endoflife.date/k8s -> https://endoflife.date/kubernetes
  product: k8s
  is-not-eol: true
```

### Sample Output:

```json5
"release-cycles-list": ["1.26", "1.25", "1.24"]
"latest-versions": ["1.26.2", "1.25.7", "1.24.11"]
# Same as the content of the URL, not the URL itself
"metadata": "https://deploy-preview-2080--endoflife-date.netlify.app/api/v1/products/python/"
```

## Get RHEL releases with ELS support

```yaml
uses: endoflife-date/supported-versions@v1
with:
  # Note that this is an alternate URL, for shorthand. https://endoflife.date/k8s -> https://endoflife.date/kubernetes
  product: rhel
  is-extended-support: true
```

### Sample Output:

```json5
"release-cycles-list": ["9", "8", "7", "6"]
"latest-versions": ["9.1", "8.7", "7.9", "6.10"]
# Same as the content of the URL, not the URL itself
"metadata": "https://deploy-preview-2080--endoflife-date.netlify.app/api/v1/products/rhel/"
```
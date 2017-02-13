---
title: Hiptest API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell

toc_footers:
  - <a href='https://hiptest.net'>Sign Up for Hiptest!</a>

includes:
  - authentication
  - scenarios
  - folders
  - tags
  - datasets
  - test_runs
  - tests

search: true

code_clipboard: true

meta:
  - name: description
    content: Documentation for the Kittn API
---

# Introduction

Welcome to the <a href="https://hiptest.net">Hiptest</a> API! You can use our
API to access Hiptest API endpoints, which can get information on your projects
in our database.

Since we don't provide integration with any programming languages (yet!), the
example are written in shell, using the curl command.

Our API documentation was created with [Slate](https://github.com/tripit/slate).

## Important

Hiptest API follows the [{json:api}](http://jsonapi.org) specification. The
header `accept` is always required and should be `application/vnd.api+json`. It
must also request for the desired API version - currently only version 1 is
available.

So all requests to the API must have the following header:
`Accept: application/vnd.api+json; version=1`.

## API rate limits

Your application can make up to **500** API requests per **5** minutes. Once you exceed the limit, calls will return HTTP status **429** and a message telling you that you've been limited.

Once the API endpoint is limited, you can check the headers for informations about the reset time.

```bash
HTTP/1.1 429 Too Many Requests
# snip #
X-Ratelimit-Limit: 500
X-Ratelimit-Remaining: 0
X-Ratelimit-Reset: 2017-01-01 12:00:00 +0100
# snip #
```
### Note

The throttling is based on the IP address

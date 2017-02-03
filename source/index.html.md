---
title: Hiptest API Reference

language_tabs:
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


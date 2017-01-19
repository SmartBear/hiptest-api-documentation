---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell

toc_footers:
  - <a href='https://hiptest.net'>Sign Up for Hiptest!</a>

<!-- includes:
  - errors -->

search: true

code_clipboard: true

meta:
  - name: description
    content: Documentation for the Kittn API
---

# Introduction

Welcome to the <a href="https://hiptest.net">Hiptest</a> API! You can use our API to access Hiptest API endpoints, which can get information on your projects in our database.

Since we don't provide integration with any programming languages (yet!), the example are written in shell, using the curl command.

Our API documentation was created with [Slate](https://github.com/slatedocs/slate).

# Authentication

Before sending requests to our endpoints, you will need to get an authentication token.
This token is made up of three data:

* The access-token
* Your client id
* Your uid

> To get your credentials:

```shell
  curl -XPOST "https://hiptest.net/api/auth/sign_in"
    -d '{"email": "my_hiptest_account", "password": "my_hiptest_account"}'
    -H "Content-Type: application/json"
```

You can get this authentication token using one of our API endpoint (only working if you registered to Hiptest using your email) or directly
in your Hiptest profile page (TODO).

<aside class="notice"> If you are getting your credentials through the API, your token will be set in the response headers</aside>

 Hiptest expects for the authentication token to be included in all API requests to the server, in the HTTP headers of your requests

> An API call example

```shell
  curl < Hiptest API endpoint >
            -H 'accept: application/json; version=1'
            -H 'access-token: <your access token>'
            -H 'expiry: <the expiry date of your token>'
            -H 'token-type: Bearer'
            -H 'uid: <your uid>'
            -H 'client: <your client id>'
```

# Scenarios

## Get scenarios of a given project

```shell
curl "https://hiptest-net/api/projects/<project_id>/scenarios"
  -H 'accept: application/json; version=1'
  -H 'token-type: Bearer'
  -H <all your authentication headers>
```

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "type": "scenarios",
      "id": "1",
      "attributes": {
        "name": "Find horcruxes"
      },
      "links": {
        "self": "/scenarios/1"
      }
    },
    {
      "type": "scenarios",
      "id": "2",
      "attributes": {
        "name": "Defeat Voldemort"
      },
      "links": {
        "self": "/scenarios/2"
      }
    }
  ]
}
```

This endpoint retrieves all scenarios of a given project.

### URL Parameters

Parameter | Description
--------- | -----------
project_id | The ID of the project you want to retrieve the scenarios from



# Tags
## Get tags of a given scenario

```shell
curl "https://hiptest-net/api/projects/<project_id>/scenarios/<scenario_id>/tags"
  -H 'accept: application/json; version=1'
  -H 'token-type: Bearer'
  -H <all your authentication headers>
```

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "type": "tags",
      "id": "1",
      "attributes": {
        "key": "Status",
        "value": "InProgress"
      },
      "links": {
        "self": "/tags/1"
      }
    },
    {
      "type": "tags",
      "id": "2",
      "attributes": {
        "key": "Priority",
        "value": "Over9000"
      },
      "links": {
        "self": "/tags/2"
      }
    }
  ]
}
```
This endpoint retrieves all tags of a given scenario.

### URL Parameters

Parameter | Description
--------- | -----------
project_id | The ID of the project that contains the wanted scenario
scenario_id | The ID of the scenario you want to retrieve the tags from

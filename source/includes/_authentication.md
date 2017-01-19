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

# Hiptest API documentation (https://hiptest.github.io/slate/)


The API documentation is written using Slate [https://github.com/lord/slate]

To edit it, clone this repository.

```
$ cd slate
$ bundle install
$ bundle exec middleman server
== The Middleman is loading
== View your site at "http://localhost:4567", "http://127.0.0.1:4567"
== Inspect your site configuration at "http://localhost:4567/__middleman", "http://127.0.0.1:4567/__middleman"
```

Edit the pages in the source directory using the markdown syntax. To deploy,
simply use the `deploy.sh` script:

```
$ ./deploy.sh
   identical  build/stylesheets/print.css
   identical  build/stylesheets/screen.css
   identical  build/images/navbar.png
   identical  build/images/hiptest-logo.png
   identical  build/images/getting-started/doc-api-cred-02.png
   identical  build/images/getting-started/doc-api-cred-01.png
   identical  build/images/getting-started/doc-api-project-id.png
   identical  build/images/logo.png
   identical  build/fonts/slate.woff
   identical  build/fonts/slate.woff2
   identical  build/fonts/slate.eot
   identical  build/fonts/slate.ttf
   identical  build/fonts/slate.svg
   identical  build/javascripts/all_nosearch.js
   identical  build/index.html
   identical  build/javascripts/all.js
Project built successfully.
cd8e7906a9b6e51931a13fc13b8158b8fcae45d3	refs/heads/gh-pages
Depuis github.com:hiptest/slate
   0f6ce0e..cd8e790  gh-pages   -> gh-pages
[gh-pages f539285] publish: :memo: Add some doc about features endpoints
 1 file changed, 143 insertions(+)
```

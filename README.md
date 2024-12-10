# jekyll-ci-image

[![CI/CD Pipeline (self-hosted)](https://github.com/codemonkey-science/jekyll-ci-image/actions/workflows/build-and-push.yaml/badge.svg)](https://github.com/codemonkey-science/jekyll-ci-image/actions/workflows/build-and-push.yaml)

Container image used for Jekyll-based GitHub Pages that are built with GitHub Actions. Without this image, every time you run the CI/CD pipeline, it takes a bit to install and update software, every time. Instead, this has all of the necessary prerequities installed, including:

```
libyaml-dev build-essential zlib1g-dev libssl-dev
libreadline-dev libgdbm-dev libncurses5-dev libffi-dev libsqlite3-dev
libgmp-dev libxml2-dev libxslt1-dev libcurl4-openssl-dev libicu-dev
libjemalloc-dev
```

So, if you start from this image, you can get right to the business of building your site.

## Getting Started

To use this base image, in your `.github/workflows/` workflow, specify this image something like this:

```yaml
jobs:
  run-playbook:
    runs-on: self-hosted
    container:
      image: ghcr.io/codemonkey-science/jekyll-ci-image:latest
```

Since this is a public container image, you won't need to log in.

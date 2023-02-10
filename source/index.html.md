---
title: API Reference

language_tabs:
  - shell
  - ruby
  - python
  - javascript

toc_footers:
  - <a href='https://yeahtrain.com'>Sign Up for a API Key</a>

includes:
  - station
  - dep
  - depWithDetails
  - service

code_clipboard: true

meta:
  - name: description
    content: Documentation for the yeahtrain API
---

# Introduction

👋 Welcome to the yeahtrain API! You can use our API to access UK railway depature information. At the moment this 
is a very simple barebones API but we're looking to add more features soon.

Currently, we support listing departures, looking up an individual service, and retrieving station information.

# Authentication

We use API keys to allow access to the API. You can register a new API key within the [developer portal](https://yeahtrain.com/app).

We expect each reqeust to include your API key in a custom header called `x-api-key` that looks like the following:

`x-api-key: {API_KEY}`

<aside class="notice">
You must replace <code>{API_KEY}</code> with your personal API key. Your API will start with `key_`
</aside>
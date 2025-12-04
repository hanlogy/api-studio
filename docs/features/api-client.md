---
sidebar_position: 1
title: API Client
---

# API Client

The API Client is where you run HTTP requests defined in your workspace configs
and inspect the results.

Instead of building requests through a UI, you describe them in JSON files
(`collections/*.json`) and let Api Studio execute them. This keeps your API
usage close to your code and easy to version-control.

## What it does

- Sends HTTP requests based on your request config:
  - Method, URL, query, headers, body.
  - Resolved with variables from workspace, environment, collection, and
    request.
- Applies `requestMiddleware` (if present) before the request is sent:
  - Last chance to modify the request.
  - Optionally handle auth, logging, or custom workflows.
- Executes the request and shows:
  - Status code and status text.
  - Response headers.
  - Response body.
  - Timing information.

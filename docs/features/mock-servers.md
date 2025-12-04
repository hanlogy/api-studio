---
sidebar_position: 2
title: Mock Servers
---

# Mock servers

Mock servers let you describe local **HTTP/HTTPS** endpoints in JSON and get
dynamic, rule-based responses without a real backend.

## Case-based routing

Each route can define multiple **cases**.  
The incoming request is matched against these cases (method, path, query, body,
etc.), and the first match decides the response. This makes it easy to model
different scenarios for the same endpoint.

## Jest-style matchers

Request matching supports a Jest-like syntax, such as:

- `any(Constructor)`
- `stringMatching(...)`
- `stringContaining(...)`

This lets you write expressive conditions (for example “any string containing
`foo`”) directly in your JSON config, without extra code.

### Example

```json
{
  "cases": [
    {
      "request": {
        "query": {
          "name": "{{stringContaining('foo')}}"
        }
      },
      "response": {
        "body": {
          "result": "ok"
        }
      }
    },
    {
      "request": {
        "body": {
          "level": "{{any(Number)}}"
        }
      },
      "response": "@file:../data/welcome.json"
    }
  ]
}
```

## Flexible responses and proxying

For a matched case you can:

- Return an inline JSON response.
- Load the response from a file (for example `@file:../data/welcome.json`).
- Or **forward** the request to another server, acting as a lightweight proxy
  server.

This combination lets you mix mocked behaviour with real upstream services in a
single, versioned workspace.

### Proxy Config Example

```json
{
  "name": "AWS Sam Local",
  "method": "GET",
  "path": "aws",
  "cases": [
    {
      "forward": "https://localhost:3000"
    }
  ]
}
```

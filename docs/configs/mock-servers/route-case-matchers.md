---
sidebar_position: 2
title: Case Matchers
---

# Case matchers

Case matchers are used for the mock server to match the request context.

We use the same naming as the
[Jest Asymmetric Matchers](https://jestjs.io/docs/expect#asymmetric-matchers)
and almost have the same behavior.

## `anything()`

`anything()` matches anything but `null`.

```json title="case"
{
  "body": {
    "name": "{{anything()}}"
  }
}
```

## `any(type)`

`any(type)` matches anything that is the given `type`.

`type` includes: `Number`, `String`, `Array`, `Object`

```json title="case"
{
  "body": {
    "id": "{{any(Number)}}",
    "name": "{{any(String)}}",
    "accesses": "{{any(Array)}}"
  }
}
```

## `arrayContaining(array)`

`arrayContaining(array)` matches a received array which contains all of the
elements in the expected array.

```json title="case"
{
  "body": {
    "categories": "{{arrayContaining([1, 2])}}"
  }
}
```

---

To Continue...

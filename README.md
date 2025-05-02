# `slipwayhq.modify`

A [Slipway](https://slipway.co/) Component which takes an arbitrary input JSON structure and performs a series of
modifications to it.

This is useful if you want to tweak the output of one Component before passing it into another Component.

## Suggested Permissions

None

## Example Usage

Test the component by running the following command and pasting in the input when prompted:
```
slipway run-component "slipwayhq.modify.0.5.0"
```

Input:
```json
{
  "data": {
    "foo": 1,
    "bar": [
      {
        "x": 1,
        "bad": 0
      },
      {
        "x": 2
      }
    ]
  },
  "instructions": [
    {
      "type": "set",
      "path": "foo",
      "value": 100
    },
    {
      "type": "set",
      "path": "bar[1].x",
      "value": 200
    },
    {
      "type": "set",
      "path": "bar[*].new",
      "value": "hello there"
    },
    {
      "type": "delete",
      "path": "bar[*].bad"
    }
  ]
}
```

Output:
```json
{
  "data": {
    "foo": 100,
    "bar": [
      {
        "new": "hello there",
        "x": 1
      },
      {
        "new": "hello there",
        "x": 200
      }
    ]
  }
}
```
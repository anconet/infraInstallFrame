# commentsInJson.spec.md

- This spec gives rules for how to put comments in JSON files.
- This spec should be used during creation of tools that consume JSON files.
- This spec should be used when putting comments in JSON files.

## Examples
```json
{
    "__comment":"An arbitrary string",
    "key1":"value1",
    "key2":"value2"
}
```

```json
{
    "__comment":"Just ascii text\n--------------------------\nWith lovely formatting.\n- Nice bullets...\n- etc...",
    "key1":"value1",
    "key2":"value2"
}
```

```json
{
    "__comment":{
        "__comment":"A comment object",
        "name":"My file",
        "description":"An awesome file"
    }
}
```

## Normative rules
- This specification applies only to JSON files designated by project policy.
- In designated files, `__comment` is a reserved key at all object nesting levels.
- In non-designated files, this specification imposes no requirements.
- The comment key MUST be exactly `__comment`.
- The value for `__comment` MAY be any valid JSON value type: string, object, array, number, boolean, or null.
- Tools that consume these files MUST ignore `__comment` values for business logic and configuration behavior.
- A JSON object MUST NOT contain duplicate `__comment` keys; multiple `__comment` entries in the same object are not allowed.
- Keys other than `__comment` MUST be interpreted exactly as they would be without this spec.
- When a tool modifies an existing object, it MUST preserve that object's existing `__comment` key and value if present.
- When a tool creates a new object, it SHOULD provide guidance or an explicit option for adding a `__comment` key.
- When a tool creates a new object, it MUST NOT add a `__comment` key by default unless the user or project configuration explicitly opts in.
- When a tool deletes an object, preserving that object's `__comment` is NOT required.

# Form Root Schema 

```json
{
    "$schema": "https://json-schema.org/draft/2020-12/schema",
    "definitions": {
        "block": {
            "description": "Form property format",
            "type": "object",
            "properties": {
                "field": {
                    "type": "string",
                    "description": "unique property name"
                },
                "label": {"type": "string"},
                "unit": {"type": "string"},
                "root": {"type": "string"},
                "index": {"type": "string"},
                "description": {"type": "string"},
                "required": {"type": "boolean"},
                "disabled": {"type": "boolean"},
                "readonly": {"type": "boolean"},
                "hint": {"type": "string"},
                "type": {
                    "description": "property type such as text, bool, time, index...",
                    "type": "string",
                    "enum": [
                            "text", "select", "boolean", "timestamp", "coordinates", "index", 
                            "formArray", "formAssoc", "mask", "asset", "barcode",
                            "object", "style", "assetArray"
                    ]
                },
                "defaultValue": {
                    "description": "Form new instance initial value.",
                    "type": ["string", "number", "integer", "boolean", "null", "object", "array"]
                },
                "params": {
                    "description": "Type specific parameters of this property",
                    "type": "object"
                }
            },
            "required": ["field", "type"]
        }
    },
    "description": "Form root/model format",
    "type": "object",
    "properties": {
        "id": {
            "description": "Form root unique id",
            "type": "string"
        },
        "type": {
            "description": "Form root parent or category id",
            "type": "string",
        },
        "ctime": {
            "description": "Creation time in UNIX epoch format (ms since 1970)",
            "type": "integer"
        },
        "mtime": {
            "description": "Last modification time in UNIX epoch format",
            "type": "integer"
        },
        "title": {
            "description": "Form main title",
            "type": "string"
        },
        "content": {
            "description": "Form properties content",
            "type": "object",
            "additionalProperties": {
                "$ref": "#/definitions/block"
            }
        }
    },
    "required": ["id", "ctime", "title", "content"]
}
````

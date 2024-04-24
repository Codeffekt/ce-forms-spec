# Form Query Schema

```json
{
    "$schema": "https://json-schema.org/draft/2020-12/schema",
    "definitions": {
        "queryFieldExpr": {
            "description": "How to filter forms with some specific field value",
            "type": "object",
            "properties": {
                "field": { "type": "string" },
                "op": {
                    "type": "string",
                    "enum": [ "=", "!=" , "<" , ">" , ">=" , "<=" , "~~" , "~~*" , "!~~" , "!~~*" , "@>" , "<@" , "[]" , "]]" , "][" , "[[" ]
                },
                "value": {
                    "type": ["string", "number", "integer", "boolean", "null", "object"]
                },
                "onMeta": {
                    "type": "boolean"
                },
                "type": {
                    "type": "string",
                    "enum": [ "array" , "date" , "integer" , "double" , "timestamp" , "object" , "text" , "form" , "formAssoc" ]
                }
            },
            "required": ["field"]
        },
        "querySortField": {
            "description": "How to sort returned fors regarding fields values",
            "type": "object",
            "properties": {
                "field": { "type": "string" },
                "onMeta": {
                    "type": "boolean"
                },
                "order": {
                    "type": "string",
                    "enum": [ "asc", "desc" ]
                },
                "type": {
                    "type": "string",
                    "enum": [ "array" , "date" , "integer" , "double" , "timestamp" , "object" , "text" , "form" , "formAssoc" ]
                }
            },
            "required": ["field"]
        }
    },
    "description": "Form query format",
    "type": "object",
    "properties": {
        "limit": {
            "description": "How many forms will be returned",
            "type": "integer",
            "minimum": 0
        },
        "offset": {
            "description": "Skip that many forms. Combine with limit for pagination.",
            "type": "integer",
            "minimum": 0
        },
        "queryFields": {
            "type": [{
                "type": "object"
            }, {
                "type": "array",
                "items": {
                    "$ref": "#/definitions/queryFieldExpr"
                }
            }]
        },
        "sortFields": {
            "type": "array",
            "items": {
                 "$ref": "#/definitions/querySortField"
            }
        }
    }
}

```

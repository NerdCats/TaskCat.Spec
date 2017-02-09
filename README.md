# TaskCat.Spec
JSON driven document specification for TaskCat

## Notational Conventions
The following JSON primitive types are considered for the specification. 

* null - A JSON "null" production
* boolean - A "true" or "false" value, from the JSON "true" or "false" productions
* object - An unordered set of properties mapping a string to an instance, from the JSON "object" production
* array - An ordered list of instances, from the JSON "array" production
* number - An arbitrary-precision, base-10 decimal number value, from the JSON "number" production
* string - A string of Unicode code points, from the JSON "string" production

Along with the primitive ones these are the data formats used in addtion.
* datetime - ISO 8601 standard date time format 
* duration - ISO 8601 duration format

The key words "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT", "SHOULD", "SHOULD NOT", "RECOMMENDED", "MAY", and "OPTIONAL" in this document are to be interpreted as described in RFC 2119 .

The verbs “GET”, “PUT”, “POST” and “DELETE” are to be interpreted as HTTP request methods when applied to URLs with “http” or “https”URL schemes, or equivalent protocol operations when applied to other URL schemes.

This is losely based on http://json-schema.org/latest/json-schema-core.html

## Range of JSON values
An instance may be any valid JSON value as defined by JSON [RFC7159]. JSON Schema imposes no restrictions on type: JSON Schema can describe any JSON value, including, for example, null.

## Definitions

## Document and Schema
Document would be defined as structured data sets suscpetible to changes from user interaction. The actual content of the data might create hierachies based on the schema provided. It can be nested and one document should only refer to a single schema. The aforementioned schema can have nested schema reference in it. So a single document might have nested document in it. This specification only points to a proper JSON document.

## Equality
Two JSON instances are said to be equal if and only if they are of the same type and have the same value according to the data model. Specifically, this means:

both are null; or
both are true; or
both are false; or
both are strings, and are the same codepoint-for-codepoint; or
both are numbers, and have the same mathematical value; or
both are arrays, and have an equal value item-for-item; or
both are objects, and each property in one has exactly one property with an equal key the other, and that other property has an equal value.
Implied in this definition is that arrays must be the same length, objects must have the same number of members, properties in objects are unordered, there is no way to define multiple properties with the same key, and mere formatting differences (indentation, placement of commas, trailing zeros) are insignificant.

## Numbers and integers
Since JSON denotes any number as simply `number`, it would be worth mentioning that the representation for floating point numbers should be different than integers. In no circumstance an integer should ever be represented in a floating manner.

## The `defintion` keyword:
The definition keyword defines the properties current schema exposes. A basic schema with a single string property definition would look like:

```JSON
{
    "definitions" :{
        "title" : {
            "type" : "string"
        }
    }
}
```

Here the property `title` gets its type definition through `type` keyword which would essentially point to a basic data type we discussed about. User defined types would be defined through `namespace` keyword with inline/external definitions.

## The `namespace` keyword
The namespace keyword is used to define a URI for a specific schema. It would serve as the base uri for the schema and it is resolved to populate a full schema it points to if it is encountered declared under another schema. 

If present, the value for this keyword MUST be a string, and MUST represent a valid URI-reference [RFC3986]. This value SHOULD be normalized, and SHOULD NOT be an empty fragment <#> or an empty string <>.

To name subschema in a schema document subschemas are supposed to use a `namespace` property/instance to give them an identifier. 

For example a sample schema would be:

```JSON
{
    "namespace": "example.com/schema",
    "definitions": {
        "PropertyA": {
            "namespace": "#propASchema"
        },
        "PropertyB": {
            "namespace": "#propBSchema",
            "definitions" : {
                "propX": {
                    "namespace" : "#bar",
                },
                "propY" : {
                    "namespace" : "subschema/subsubschema"
                }
            }
        }
    }
}
```

## Schema inheritance and overloading


## TODO:
* Compilable event definitions
* Execution time properties
 

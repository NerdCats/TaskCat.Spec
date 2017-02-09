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

The verbs “GET”, “PUT”, “POST” and “DELETE” are to be interpreted as HTTP request methods when applied to URLs with “http” or “https” URL schemes, or equivalent protocol operations when applied to other URL schemes.

This is losely based on http://json-schema.org/latest/json-schema-core.html

## Range of JSON values
An instance may be any valid JSON value as defined by JSON [RFC7159]. JSON Schema imposes no restrictions on type: JSON Schema can describe any JSON value, including, for example, null.

## Payload and Schema
Payload would be defined as structured data sets suscpetible to changes from user interaction. The actual content of the data might create hierachies based on the schema provided. It can be nested and one payload should only refer to a single schema. The aforementioned schema can have nested schema reference in it. So a single payload might have nested payload in it. 

## JobTask
A job task under TaskCat is a sub-unit of a single job. A JobTask denotes a stage of work in a job. A job is supposed to have tasks for any stage in a work process. JobTasks true purpose is to preserve history in the process of a Job. JobTask is volatile in nature and is susceptible to changes from users. This changes are eventful and Jobs are essentially susceptible to those. 

## Abstract JobTask Schema
```JSON
{
    "namespace": "nerdcats.co/taskcat/jobtask",
    "definitions" : {
        "Name" : {
            "type": "string"
        },
        "Variant" : {
            "type": "string" // TODO: Should come from a valid variants list,
        },
        "Predecessor" : {
            "type": "TODO: <Relational predecessor if any>, not defined yet, computable at compile time, need syntax for that too"
        },
        "Type": {
            "type": "string"
        },
        "JobTaskState": {
            "namespace": "nerdcats.co/taskcat/jobtask-state/**/*" 
            // TODO: Not defined yet, supposed to be any sub-type of this so we can have different job tasks for different job types
        },
        "AssetRef": {
            "namespace": "nerdcats.co/taskcat/assetref"
        },
        "ETA": {
            "type": "datetime"
        },
        "CreateTime": {
            "type": "datetime"
        },
        "InitiationTime" : {
            "type": "datetime"
        },
        "ModifiedTime" : {
            "type": "datetime"
        },
        "CompletionTime" : {
            "type": "datetime"
        },
        "Duration": {
            "type": "duration"
        },
        "Description": {
            "type": "string"
        },
        "Notes" : {
            "type": "string"
        },
        "IsReadytoMoveToNextTask" : {
            "type" : "boolean"
        },
        "IsDependencySatisfied" : {
            "type" : "TODO: Execution time property, need to have a definition type here"
        },
        "IsStartingTask" : {
            "type" : "TODO: Execution time property, need to have a definition type here"
        },
        "IsTerminatingTask" : {
            "type" : "TODO: Execution time property, need to have a definition type here"
        },
        "ETAFailed" : {
            "type" : "TODO: Execution time property, need to have a definition type here"
        }
    }
}
```

## TODO:
* Compilable event definitions
* Execution time properties
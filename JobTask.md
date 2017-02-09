## JobTask
A job task under TaskCat is a sub-unit of a single job. A JobTask denotes a stage of work in a job. A job is supposed to have tasks for any stage in a work process. JobTasks true purpose is to preserve history in the process of a Job. JobTask is volatile in nature and is susceptible to changes from users. This changes are eventful and Jobs are essentially susceptible to those.

## Abstract JobTask Schema
```JSON
{
    "$schema": "http://json-schema.org/draft-04/schema#",
    "id": "http://nerdcats.com/taskcat/jobtask",
    "title": "JobTask",
    "description": "Generic JobTask Schema",
    "type": "object",
    "properties": {
        "id": {
            "description": "Unique 24 character GUID",
            "type": "string"
        },
        "Name": {
            "type" : "string"
        },
        "Predecessor": {
            "type": "TODO: <Relational predecessor if any>, not defined yet, computable at compile time, need syntax for that too"
        },
        "Result" : {
            "type": "TODO: <Relational predecessor if any>, not defined yet, computable at compile time, need syntax for that too"
        },
        "Type" : {
            "type": "string",
            "minLength" : 1
        },
        "JobTaskState": {
            "description": "Current state of a jobtask",
            "$ref": "http://nerdcats.com/taskcat/jobtask/state"
            // TODO: Not defined yet, supposed to be any sub-type of this so we can have different job tasks for different job types
        },
        "AssetRef": {
            "type": "string"
        },
        "ETA" : {
            "format": "date-time",
            "type": "string",
            "description": "JobTask ETA"
        },
        "CreateTime": {
            "format": "date-time",
            "type": "string",
            "description": "JobTask creation time"
        },
        "InitiationTime": {
            "format": "date-time",
            "type": "string",
            "description": "JobTask initiation time"
        },
        "ModifiedTime": {
            "format": "date-time",
            "type": "string",
            "description": "JobTask modification time"
        },
        "CompletionTime": {
            "format": "date-time",
            "type": "string",
            "description": "JobTask completion time"
        },
        "Duration" : {
            "format": "duration",
            "type": "string",
            "description": "JobTask duration"
            // TODO: This is another place we can use some smartness, may be some property expressions
        },
        "Description": {
            "description": "Description of the jobtask",
            "type": "string"
        },
        "Notes": {
            "description": "Special set of notes for the Asset for this task",
            "type": "string"
        },
        "IsReadytoMoveToNextTask" : {
            "type": "boolean"
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
    },
    "required": ["id", "Type"]
}
```
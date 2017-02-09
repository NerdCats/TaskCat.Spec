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
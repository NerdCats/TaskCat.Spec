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
            "$ref": "http://nerdcats.com/taskcat/jobtask/state",
            "TODO": "Not defined yet, supposed to be any sub-type of this so we can have different job tasks for different job types"
        },
        "AssetRef": {
            "type": "string"
        },
        "ETA" : {
            "format": "date-time",
{
  "$schema": "http://json-schema.org/draft-04/schema#",
  "id": "http://nerdcats.com/taskcat/pickuptask",
  "type": "object",
  "definitions": {
    "point": {
      "title": "Point",
      "properties": {
        "type": {
          "enum": [
            "Point"
          ]
        },
        "coordinates": {
          "$ref": "#/definitions/position"
        }
      }
    },
    "position": {
      "description": "A single position",
      "type": "array",
      "minItems": 2,
      "items": [
        {
          "type": "number"
        },
        {
          "type": "number"
        }
      ],
      "additionalItems": false
    }
  },
  "properties": {
    "Name": {
      "title": "Name",
      "type": "string",
      "description": "The name of the Pickup Task"
    },
    "_id": {
      "title": "_id",
      "type": "string",
      "description": "The GUID for the pick up task"
    },
    "Variant": {
      "title": "Variant",
      "type": "string",
      "description": "The variant for the pick up task",
      "enum": [
        "default",
        "retry"
      ]
    },
    "Type": {
      "title": "Type",
      "type": "string",
      "description": "The type for the pick up task",
      "enum": [
        "PackagePickUp"
      ]
    },
    "State": {
      "title": "State",
      "type": "string",
      "description": "The current state of the pick up task",
      "enum": [
        "PENDING",
        "COMPLETED",
        "FAILED",
        "CANCELLED"
      ]
    },
    "AssetRef": {
      "title": "AssetRef",
      "type": "string",
      "description": "Asset id reference from the assets dictionary"
    },
    "CreateTime": {
      "title": "CreateTime",
      "description": "The time where this job task was created"
    },
    "InitiationTime": {
      "title": "CreateTime",
      "description": "The time where this job task was initiated"
    },
    "ModifiedTime": {
      "title": "ModifiedTime",
      "description": "The time where this job task was last modified"
    },
    "CompletionTime": {
      "title": "CompletionTime",
      "description": "The time where this job task was completed"
    },
    "IsStartingTask": {
      "title": "IsStartingTask",
      "description": "Denotes whether this task will be considered as a starting node in a state machine"
    },
    "IsTerminatingTask": {
      "title": "IsTerminatingTask",
      "description": "Denotes whether this task will be considered as an termination node in a state machine"
    },
    "PickupLocation": {
      "title": "PickupLocation",
      "description": "Location where the package is supposed to be picked up from",
      "properties": {
        "Point": {
          "$ref": "#/definitions/point"
        },
        "Address": {
          "type": "string"
        },
        "Provider": {
          "type": "string",
          "enum": [
            "Default"
          ]
        },
        "AddressLine1": {
          "type": "string"
        },
        "City": {
          "type": "string"
        },
        "Locality": {
          "type": "string"
        }
      }
    }
  },
  "required": ["_id", "Type"]
}
```

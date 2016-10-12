# Site Configuration Updates

Messages sent with the site-specific configuration values including hours, specifying the blankout video file, and volume settings.



## Key/Value Glossary
- **blankoutVideo** - Filename including file extension.
- **closeAt** - Time that players should stop playing
- **duration**
- **guid**
- **level**
- **openAt**
- **siteId**
- **startTime**
- **updatedOn**

## Ideal Path
### What GSTV Sends to Invenco
```javascript
{
  "guid": String,
  "updatedOn": String,
  "configuration": [
    {
      "siteId": String,
      "hours": {
        "sun": [
          {
            "openAt": String,
            "closeAt": String,
            "duration": Number
          }
        ],
        "mon": [
          {
            "openAt": String,
            "closeAt": String,
            "duration": Number
          }
        ],
        "tue": [
          {
            "openAt": String,
            "closeAt": String,
            "duration": Number
          }
        ],
        "wed": [
          {
            "openAt": String,
            "closeAt": String,
            "duration": Number
          }
        ],
        "thu": [
          {
            "openAt": String,
            "closeAt": String,
            "duration": Number
          }
        ],
        "fri":[
          {
            "openAt": String,
            "closeAt": String,
            "duration": Number
          }
        ],
        "sat":[
          {
            "openAt": String,
            "closeAt": String,
            "duration": Number
          }
        ]
      },
      "blankoutVideo": String,
      "volume":[
        {
          "startTime": String,
          "level": String
        },
        {
          "startTime": String,
          "level": String
        }
      ]
    }
  ]
}
```

### What Invenco Sends to GSTV on a Successful Download
```javascript
{
  "guid": String,
  "id": String,
  "notificationTimestamp": String
  "notificationType": "CONFIGURATION_SITE_DOWNLOADED",
  "siteId": String,
  "status": "success",
}
```

### What Invenco Sends to GSTV once Site Configuration Updates have been Applied at a Site
```javascript
{
  "guid": String,
  "id": String,
  "notificationTimestamp": String
  "notificationType": "CONFIGURATION_SITE_APPLIED",
  "siteId": String,
  "status": "success",
}
```

## Error Path
### What Invenco Sends if the Site Configuration Update Notification is Malformed or is Unable to be Parsed
Follows [Default Configuration Error Handling](#default-configuration-error-handling)

```javascript
{
  "guid": String,
  "id": String,
  "notificationTimestamp": String
  "notificationType": "CONFIGURATION_SITE_MALFORMED_DATA",
  "siteId": String,
  "status": "failure",
  "additionalInformation": ""
}
```

#### What Invenco Sends if the Volume Level in the Site Configuration Update Notification is not Formatted Correctly
Follows [Default Configuration Error Handling](#default-configuration-error-handling)

```javascript
{
  "guid": String,
  "id": String,
  "notificationTimestamp": String
  "notificationType": "CONFIGURATION_SITE_MALFORMED_DATA",
  "siteId": String,
  "status": "failure",
  "additionalInformation": "Volume Level Incorrectly Formatted"
}
```

#### What Invenco Sends if the Start Time for a Volume Level in the Site Configuration Update Notification is not Formatted Correctly
Follows [Default Configuration Error Handling](#default-configuration-error-handling)

```javascript
{
  "guid": String,
  "id": String,
  "notificationTimestamp": String
  "notificationType": "CONFIGURATION_SITE_MALFORMED_DATA",
  "siteId": String,
  "status": "failure",
  "additionalInformation": "Volume Start Time Incorrectly Formatted"
}
```

### What Invenco Sends if the Site Configuration Update Notification Contains Unexpected Values
Follows [Default Configuration Error Handling](#default-configuration-error-handling)

```javascript
{
  "guid": String,
  "id": String,
  "notificationTimestamp": String
  "notificationType": "CONFIGURATION_SITE_UNEXPECTED_VALUE",
  "siteId": String,
  "status": "failure",
  "additionalInformation": ""
}
```

#### What Invenco Sends if the Site Identifier in the Site Configuration Update Notification Does Not Exist
Follows [Default Error Handling](#default-error-handling)

```javascript
{
  "guid": String,
  "id": String,
  "notificationTimestamp": String
  "notificationType": "CONFIGURATION_SITE_UNEXPECTED_VALUE",
  "siteId": String,
  "status": "failure",
  "additionalInformation": "Site identifier does not exist"
}
```

#### What Invenco Sends if the Open At in the Site Configuration Update Notification Are Later than the Close At
Follows [Default Configuration Error Handling](#default-configuration-error-handling)

```javascript
{
  "guid": String,
  "id": String,
  "notificationType": "CONFIGURATION_SITE_UNEXPECTED_VALUE",
  "notificationTimestamp": String
  "siteId": String,
  "status": "failure",
  "additionalInformation": "" // TBD
}
```

#### What Invenco Sends if the Duration Calculations in the Site Configuration Update Notification Are Incorrect
Follows [Default Configuration Error Handling](#default-configuration-error-handling)

```javascript
{
  "guid": String,
  "id": String,
  "notificationType": "CONFIGURATION_SITE_UNEXPECTED_VALUE",
  "notificationTimestamp": String
  "siteId": String,
  "status": "failure",
  "additionalInformation": "" // TBD
}
```

### What Invenco Sends if the Site Configuration Update Notification is Missing Values
Follows [Default Configuration Error Handling](#default-configuration-error-handling)

```javascript
{
  "guid": String,
  "id": String,
  "notificationTimestamp": String
  "notificationType": "CONFIGURATION_SITE_MISSING_VALUE",
  "siteId": String,
  "status": "failure",
  "additionalInformation": ""
}
```

### What Invenco Sends if the Blankout Video in the Site Configuration Update Notification is not in the Invenco Library
Follows [Default Configuration Error Handling](#default-configuration-error-handling)

```javascript
{
  "guid": String,
  "id": String,
  "notificationTimestamp": String
  "notificationType": String,
  "siteId": String,
  "status": "failure",
  "additionalInformation": "Blankout Video File Missing"
}
```

## Standard Operating Procedure
### Applying Configuration Updates

### Error Handling
#### Default Error Handling
1. Send a notification message to GSTV alerting that an error has occured.
1. GSTV sends another notification update message.

#### Default Configuration Error Handling
1. Send a notification message to GSTV alerting that an error has occured.
1. If a previous configuration exists
  1. Continue to operate using previous configuration until next update
1. If no previous configuration exists
  1. @scott_horton Use generic configuration until next update
1. GSTV sends another notification update message.

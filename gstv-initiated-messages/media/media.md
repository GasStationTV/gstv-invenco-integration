# GSTV Initiated Message - Media Updates

A message is sent when a file has been added to a playlist or a current file in a playlist has been updated.

## Key/Value Glossary
### Fields from GSTV Messages
- **filename** - _required_ - Filename - including file extension - of video to control.
- **checksum** - _required_ - MD5 checksum for the video asset. This value should be used to ensure the correct and full video asset is being downloaded by Invenco.
- **updatedOn** - _required_ - A UTC date and time that indicates when this update was created. This can be used to ensure updates are applied in the appropriate order. The format will be `YYYY-MM-DD HH:MM:SS.MS` using 24 hour time.

### Additional Fields in Invenco Responses
- **notificationType** - A string indicating the step in the update process to which this notification refers.
  - Values
    - MEDIA_VALIDATION
    - MEDIA_DOWNLOAD
    - MEDIA_CHECKSUM_VALIDATION
    - MEDIA_TRANSCODED
    - MEDIA_PULLED_BY_TERMINAL
    - MEDIA_ACCEPTED_BY_TERMINAL
- **notificationTimestamp** - A date and time (in UTC) that indicates when this notification was created. This can be used to ensure notifications are read in the appropriate order. The format will be `year-month-day hours:mins:secs.milliseconds`. 24 hour time will be used.
- **status** - A String that will indicate if the step in the update process for which this notification was generated succeeded or failed.
  - Values
    - success
    - failure
- **id** - A unique identifier for this notification, generated by Invenco, that will be used to refer to the notification in human communication.
- **additionalInformation** - A free-form String that can be a message or other details about the notification. This should be human-readable.
- **terminalId** - The id of the terminal at the site.

## Ideal Path
### What GSTV Sends to Invenco
```javascript
{
  "guid": String,
  "updatedOn": String
  "filename": String,
  "checksum": String
}
```

### What Invenco Sends to GSTV once Media Updates have been Validated
```javascript
{
  "guid": String,
  "id": String,
  "notificationTimestamp": String
  "notificationType": "MEDIA_VALIDATION",
  "status": "success"
}
```

### What Invenco Sends to GSTV when the File has been Successfully Downloaded from S3
```javascript
{
  "guid": String,
  "id": String,
  "filename": String,
  "notificationTimestamp": String
  "notificationType": "MEDIA_DOWNLOAD",
  "status": "success"
}
```

### What Invenco Sends to GSTV when the Provided MD5 Checksum and the Calculated MD5 Checksum Match
```javascript
{
  "guid": String,
  "id": String,
  "filename": String,
  "notificationTimestamp": String
  "notificationType": "MEDIA_CHECKSUM_VALIDATION",
  "status": "success"
}
```

### What Invenco Sends to GSTV when the File has Successfully been Transcoded
```javascript
{
  "guid": String,
  "id": String,
  "filename": String,
  "notificationTimestamp": String
  "notificationType": "MEDIA_TRANSCODED",
  "status": "success"
}
```

### What Invenco Sends to GSTV once a File has been Pulled by a Terminal
```javascript
{
  "guid": String,
  "id": String,
  "filename": String,
  "notificationTimestamp": String
  "notificationType": "MEDIA_PULLED_BY_TERMINAL",
  "siteId": String,
  "status": "success",
  "terminalId": String
}
```

### What Invenco Sends to GSTV once a File has been Accepted by the Terminal
```javascript
{
  "guid": String,
  "id": String,
  "filename": String,
  "notificationTimestamp": String
  "notificationType": "MEDIA_ACCEPTED_BY_SITE",
  "siteId": String,
  "status": "success",
  "terminalId": String
}
```

## Error Path
If any part of a message causes an error the entire update will be rejected.

### What Invenco Sends if the Media Update Notification has Validation Errors
Follows [Default Configuration Error Handling](#default-configuration-error-handling).

```javascript
{
  "guid": String,
  "id": String,
  "filename": String,
  "notificationTimestamp": String
  "notificationType": "MEDIA_VALIDATION",
  "status": "failure",
  "additionalInformation": ""
}
```

#### Specific Examples
##### What Invenco Sends if the GUID, checksum or updatedOn in the Media Update Notification Does Not Exist
Follow [Default Error Handling](#default-error-handling).

Return above structure with this specific value for additionalInformation.

```javascript
  "additionalInformation": "GUID is Missing"
```

```javascript
  "additionalInformation": "Checksum is Missing"
```

```javascript
  "additionalInformation": "Updated On is Missing"
```

### What Invenco Sends if the Video File in the Media Update can not be Downloaded
1. Invenco should retry downloading the file three times.
1. If the download is still unsuccessful follow [Default Configuration Error Handling](#default-configuration-error-handling).

```javascript
{
  "guid": String,
  "id": String,
  "filename": String,
  "notificationTimestamp": String
  "notificationType": "MEDIA_DOWNLOAD",
  "status": "failure",
  "additionalInformation": ""
}
```

### What Invenco Sends if the Provided MD5 Checksum does not Match the Calculated MD5 Checksum for the Media File
Follows [Default Configuration Error Handling](#default-configuration-error-handling).

```javascript
{
  "guid": String,
  "id": String,
  "filename": String,
  "notificationTimestamp": String
  "notificationType": "MEDIA_CHECKSUM_VALIDATION",
  "status": "failure",
  "additionalInformation": ""
}
```

### What Invenco Sends if the Media File is Unable to be Transcoded
Follows [Default Configuration Error Handling](#default-configuration-error-handling).

```javascript
{
  "guid": String,
  "id": String,
  "filename": String,
  "notificationTimestamp": String
  "notificationType": "MEDIA_TRANSCODED",
  "status": "failure",
  "additionalInformation": ""
}
```

### What Invenco Sends if they are Unable to Pull Media Updates to a Terminal
Follow [Default Configuration Error Handling](#default-configuration-error-handling).

```javascript
{
  "guid": String,
  "id": String,
  "filename": String,
  "notificationTimestamp": String
  "notificationType": "MEDIA_PULLED_BY_TERMINAL",
  "siteId": String,
  "status": "failure",
	"terminalId": String,
  "additionalInformation": ""
}
```

### What Invenco Sends if a Media Updates are Rejected by the Terminal
Follow [Default Configuration Error Handling](#default-configuration-error-handling).

```javascript
{
  "guid": String,
  "id": String,
  "filename": String,
  "notificationTimestamp": String
  "notificationType": "MEDIA_ACCEPTED_BY_TERMINAL",
  "siteId": String,
  "status": "failure",
	"terminalId": String,
  "additionalInformation": ""
}
```

## Standard Operating Procedure
### Applying Media Updates
1. Poll for media update notification.
1. Validate media update notification.
  - **If success**
    - Follow [What Invenco Sends to GSTV once Media Updates have been Validated](#what-invenco-sends-to-gstv-once-media-updates-have-been-validated).
  - **If failure**
      - Follow [What Invenco Sends if the Media Update Notification has Validation Errors](#what-invenco-sends-if-the-media-update-notification-has-validation-errors).
1. Download video asset from S3.
  - **If success**
    - Follow [What Invenco Sends to GSTV when the File has been Successfully Downloaded from S3](#what-invenco-sends-to-gstv-when-the-file-has-been-successfully-downloaded-from-s3).
  - **If failure**
      - Retry download from S3 three times.
        - **If success**
          - Follow [What Invenco Sends to GSTV when the File has been Successfully Downloaded from S3](#what-invenco-sends-to-gstv-when-the-file-has-been-successfully-downloaded-from-s3).
        - **If failure**
          - Follow [What Invenco Sends if the Media Update Notification has Validation Errors](#what-invenco-sends-if-the-media-update-notification-has-validation-errors).
1. Calculate MD5 checksum of downloaded media and compare with MD5 provided in media update.
  - **If success**
    - Follow [What Invenco Sends to GSTV when the Provided MD5 Checksum and the Calculated MD5 Checksum Match](#what-invenco-sends-to-gstv-when-the-provided-md5-checksum-and-the-calculated-md5-checksum-match).
  - **If failure**
    - Download again
    - Retry MD5 check
      - **If success**
        - Follow [What Invenco Sends to GSTV when the Provided MD5 Checksum and the Calculated MD5 Checksum Match](#what-invenco-sends-to-gstv-when-the-provided-md5-checksum-and-the-calculated-md5-checksum-match).
      - **If failure**
        - Follow [What Invenco Sends if the Provided MD5 Checksum does not Match the Calculated MD5 Checksum for the Media File](#what-invenco-sends-if-the-provided-md5-checksum-does-not-match-the-calculated-md5-checksum-for-the-media-file).
1. Complete transcoding of media.
  - **If success**
    - Follow [What Invenco Sends to GSTV when the File has Successfully been Transcoded](#what-invenco-sends-to-gstv-when-the-file-has-successfully-been-transcoded).
  - **If failure**
    - Retry transcoding
      - **If success**
        - Follow [What Invenco Sends to GSTV when the File has Successfully been Transcoded](#what-invenco-sends-to-gstv-when-the-file-has-successfully-been-transcoded).
      - **If failure**
        - Follow [What Invenco Sends if the Media File is Unable to be Transcoded](#what-invenco-sends-if-the-media-file-is-unable-to-be-transcoded).
1. Pull media to required terminal.
  - **If success**
    - Follow [What Invenco Sends to GSTV once a File has been Pulled by Terminal](#what-invenco-sends-to-gstv-once-a-file-has-been-pushed-to-the-site).
  - **If failure**
    - Follow [What Invenco Sends if they are Unable to Pull Media Updates to a terminal](#what-invenco-sends-if-they-are-unable-to-push-media-updates-to-a-site).

### Error Handling
#### Media Error Handling
1. Send a notification message to GSTV alerting that an error has occurred.
1. Playback does not stop.
1. The affected file is skipped during playback.
1. GSTV sends another notification update message.

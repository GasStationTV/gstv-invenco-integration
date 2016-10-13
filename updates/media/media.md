# Media Updates

A message is sent when a file has been added to a playlist or a current file in a playlist has been updated.

<!-- TOC depthFrom:1 depthTo:6 withLinks:1 updateOnSave:1 orderedList:0 -->

- [Media Updates](#media-updates)
	- [Ideal Path](#ideal-path)
		- [What GSTV Sends to Invenco](#what-gstv-sends-to-invenco)
		- [What Invenco Sends to GSTV on Success](#what-invenco-sends-to-gstv-on-success)
	- [Error Path](#error-path)
		- [What Invenco Sends if the File is Not Found in S3](#what-invenco-sends-if-the-file-is-not-found-in-s3)
		- [What Invenco Sends if the MD5 Does Not Match After Download](#what-invenco-sends-if-the-md5-does-not-match-after-download)
		- [What Invenco Sends if the File Download Does Not Complete](#what-invenco-sends-if-the-file-download-does-not-complete)

<!-- /TOC -->

## Key/Value Glossary
### Fields from GSTV Messages
- **filename** - Filename - including file extension - of video to control.
- **checksum** - MD5 checksum for the video asset. This value should be used to ensure the correct and full video asset is being downloaded by Invenco.
- **fileUpdatedOn** - UTC datetime when the video asset was updated.


### Additional Fields in Invenco Responses
- **notificationType** - TBD
- **notificationTimestamp** - TBD
- **status** - TBD
- **id** - TBD
- **additionalInformation** - TBD

## Ideal Path
### What GSTV Sends to Invenco
```javascript
{
  "filename": String,
  "checksum": String,
  "fileUpdatedOn": "18:41"
}
```

### What Invenco Sends to GSTV on Success
```javascript
{
  "id": String,
  "filename": String,
  "notificationTimestamp": String
  "notificationType": String,
  "status": "success",
  "additionalInformation": String
}
```

## Error Path
### What Invenco Sends if the File is Not Found in S3
Follow [Media Error Handling](#media-error-handling).

```javascript
{
  "id": String,
  "filename": String,
  "notificationTimestamp": String
  "notificationType": String,
  "status": "failure",
  "additionalInformation": String
}
```

### What Invenco Sends if the MD5 Does Not Match After Download
Follow [Media Error Handling](#media-error-handling).

```javascript
{
  "id": String,
  "filename": String,
  "notificationTimestamp": String
  "notificationType": String,
  "status": "failure",
  "additionalInformation": String
}
```

### What Invenco Sends if the File Download Does Not Complete
1. Invenco should retry downloading the file three times.
1. If the download is still unsuccessful follow [Media Error Handling](#media-error-handling).

```javascript
{
  "id": String,
  "filename": String,
  "notificationTimestamp": String
  "notificationType": String,
  "status": "failure",
  "additionalInformation": String
}
```

## Standard Operating Procedure
### Applying Configuration Updates

### Error Handling
#### Media Error Handling
1. Send a notification message to GSTV alerting that an error has occured.
1. Playback does not stop.
1. The affected file is skipped during playback.
1. GSTV sends another notification update message.

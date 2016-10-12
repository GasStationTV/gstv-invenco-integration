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
### filename
Filename including file extension

### checksum

### fileUpdatedOn

### id
Invenco generated string unique per notification

### notificationType
@TODO List defined notification types for media notification

### status
Possible Values
- success
- failure

### additionalInformation
@TODO List additionalInformation values?


## Ideal Path
### What GSTV Sends to Invenco
```javascript
{
  "filename": "W_WSL14893_WASHINGTONLOTTERY2016.avi",
  "checksum": "0C86798478BF382F1CF61860D301C1B4",
  "fileUpdatedOn": "18:41"
}
```

### What Invenco Sends to GSTV on Success
```javascript
{
  "id": String, // invenco generated per notification
  "filename": "W_WSL14893_WASHINGTONLOTTERY2016.avi",
  "notificationType": String, // one of the defined notifications
  "status": "success",
  "additionalInformation": String
}
```

## Error Path
### What Invenco Sends if the File is Not Found in S3
1. A notification packet is sent to GSTV signifying an error has occurred.
1. Playback at the site is unaffected.
1. The file that was supposed to play is skipped.
1. GSTV will send another media update notification.

```javascript
{
  "id": String,  // invenco generated per notification
  "filename": String,
  "notificationType": String, // one of the defined notifications
  "status": "failure",
  "additionalInformation": String
}
```

### What Invenco Sends if the MD5 Does Not Match After Download
1. A notification packet is sent to GSTV signifying an error has occurred.
1. Playback at the site is unaffected.
1. The file that was supposed to play is skipped.
1. GSTV will send another media update notification.

```javascript
{
  "id": String,  // invenco generated per notification
  "filename": String,
  "notificationType": String, // one of the defined notifications
  "status": "failure",
  "additionalInformation": String
}
```

### What Invenco Sends if the File Download Does Not Complete
1. Invenco should retry downloading the file three times.
1. If the download is still unsucessful, a notification packet is sent to GSTV signifying an error has occurred.
1. Playback at the site is unaffected.
1. The file that was supposed to play is skipped during playback.
1. GSTV will send another media change notification.
```javascript
{
  "id": String, // invenco generated per notification
  "filename": String,
  "notificationType": String, // one of the defined notifications
  "status": "failure",
  "additionalInformation": String
}
```

# Media Updates

A message is sent when a file has been added to a playlist or a current file in a playlist has been updated.

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
A notification packet is sent to GSTV signifying an error has occurred. Playback at the site is unaffected. The file that was supposed to play is skipped. GSTV will send another media update notification.
```javascript
{
  "id": String,  // invenco generated per notification
  "filename":  "W_WSL14893_WASHINGTONLOTTERY2016.avi",
  "notificationType": String, // one of the defined notifications
  "status": "failure",
  "additionalInformation": String
}
```

### What Invenco Sends if the MD5 Does Not Match After Download
A notification packet is sent to GSTV signifying an error has occurred. Playback at the site is unaffected. The file that was supposed to play is skipped. GSTV will send another media update notification.
```javascript
{
  "id": String,  // invenco generated per notification
  "filename":  "W_WSL14893_WASHINGTONLOTTERY2016.avi",
  "notificationType": String, // one of the defined notifications
  "status": "failure",
  "additionalInformation": String
}
```

### What Invenco Sends if the File Download Does Not Complete
Invenco should retry downloading the file three times. If the download is still unsucessful, a notification packet is sent to GSTV signifying an error has occurred. Playback at the site is unaffected. The file that was supposed to play is skipped during playback. GSTV will send another media change notification.
```javascript
{
  "id": String, // invenco generated per notification
  "filename": "W_WSL14893_WASHINGTONLOTTERY2016.avi",
  "notificationType": String, // one of the defined notifications
  "status": "failure",
  "additionalInformation": String
}
```


### What Invenco Sends if the Media Update Notification Can Not Be Parsed
A notification packet is sent to GSTV signifying an error has occurred. Playback at the site is unaffected. The file that was supposed to play is skipped. GSTV will send another media update notification.
```javascript
TBD
```

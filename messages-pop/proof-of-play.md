# POP Messages - Proof of Play


## Key/Value Glossary
### Field from Invenco Messages
- **filename** -	Name of the video asset that has been displayed on a screen at a site.
- **assetId** -	Number assigned to the media asset by GSTV.  This number should be carried over from the playlist update notification.
- **ioNumber** -	The insertion order number that the asset was purchased as part of.  This value is carried over from the playlist update notification.
- **startTimestamp** -	The time in which the video asset started to play in yyyy-mm-dd HH:MM:SS format.
- **endTimestamp** - The time in which the video asset stopped playing in yyyy-mm-dd HH:MM:SS format.
- **screenState** -	For the 12", what state was the screen in during playback.  
  - **Values** : "Full", "Partial"
- **siteId** - The Invenco name of the site.
- **screenId** - The id of the screen at the site.

## Ideal Path
### What Invenco Sends to GSTV
```javascript

{
  "filename": String,
  "assetId": String,  
  "ioNumber": String   
  "startTimestamp": String (yyyy-mm-dd HH:MM:SS),
  "endTimestamp": String (yyyy-mm-dd HH:MM:SS),
  "screenState": String, 
  "siteId": String,
  "screenId": String 
}
```
## Error Path
### What Invenco Sends if Post to GSTV Fails
1. Invenco should retry sending the update three times.
1. If the update still can't be posted, Invenco should retain the POP update to re-process later
1. Send a notification message to GSTV alerting that an error has occurred.

```javascript

{
  "id": String,  
  "notificationType": String, // TBD
  "status": "failure", 
  "additionalInformation": "Failed to post POP"
}
## Global Processing
### File Missing at Terminal 
  - Terminal will check Invenco cloud for required media
    - **If success**
      - Download required media to terminal
    - **If failure**
      - Invenco sends notification to GSTV to resend media update notification
      - GSTV sends media update notification to Invenco

#### What Invenco Sends if a Media File Can Not Be Downloaded to a Terminal and is not in the Invenco Cloud
```javascript
{
  "guid": String,
  "id": String,
  "filename": String,
  "notificationTimestamp": String,
  "notificationType": "MEDIA_CHECK",
  "siteId": String,
  "status": "failure",
  "terminalId": String,
  "additionalInformation": "Video File is Missing - {filename}"
}
```


### Update Notification Processing Order
- Media update notifications should be processed before playlist update notifications
  - If a playlist update is being processed when more media updates arrive, processing of the playlist should be completed prior to media updates
- Configuration changes are processed as they arrive, but site playback should not be interrupted

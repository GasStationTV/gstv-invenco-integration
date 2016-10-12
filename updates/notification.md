# Notifications

## Anatomy of a Media Notification GSTV Sends
```javascript
{
  "filename": String,
  "checksum": String,
  "fileUpdatedOn": String
}
```

## Anatomy of a Media Notification Invenco Sends
```javascript
{
  "id": String, // invenco generated per notification
  "filename": String,
  "notificationType": String, // one of the defined notifications
  "status": String,
  "additionalInformation": String
}
```

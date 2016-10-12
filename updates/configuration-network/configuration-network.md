# Network Configuration Updates

Message sent with the network wide configuration values including shutdown hours and evergreen video settings

## Key/Value Glossary

## Ideal Path
### What GSTV Sends to Invenco
```javascript
{
   "shutdownHours":120,
   "evergreen":[
      {
         "filename":"CNN04028_HLNSAT.mp4",
         "expiryHours":25,
         "swapFilename":"CNN04031_HLNSWAP.mp4"
      },
      {
         "filename":"CNN04029_HLNSUN.mp4",
         "expiryHours":25,
         "swapFilename":"CNN04031_HLNSWAP.mp4"
      },
      {
         "filename":"CNN04104_HLNWEEKDAY.mp4",
         "expiryHours":25,
         "swapFilename":"CNN04031_HLNSWAP.mp4"
      },
      {
         "filename":"GSTV.BO__.gstvbos.mp4",
         "expiryHours":25,
         "swapFilename":""
      }
   ]
}
```

### What Invenco Sends to GSTV on Success
```javascript
{
  "id": String,  // invenco generated per notification
  "siteId": String,
  "notificationType": String, // one of the defined notifications
  "status": "success"
}
```

## Error Path
### What Invenco Sends if the Network Configuration Update Can Not Be Parsed
1. If previous network configuration exists, continue to operate with those settings.  
1. If no network configuration exists, operate without network configuration values????????????
1. Send a notification packet to GSTV signifying an error has occurred. GSTV will send another network configuration update.

```javascript
{
  "id": String, // invenco generated per notification
  "notificationType": String, // one of the defined notifications
  "status": "failure"
  "additionalInformation": "Config can't be parsed"
}
```

### What Invenco Sends if the Shutdown Hours are Missing from the Network Configuration Update
1. If previous network configuration exists, continue to operate with those settings.  
1. If no network configuration exists, ignore shutdown hours. Player will continue to play without a shutdown timeout.
1. Send a notification packet to GSTV signifying an error has occurred. GSTV will send another network configuration update."

```javascript
{
  "id": String,  // invenco generated per notification
  "notificationType": String, // one of the defined notifications
  "status": "failure"
  "additionalInformation": "shutdown hours missing"
}
```

### What Invenco Sends if the Filename in a Node is Missing from the Network Configuration Update
1. If previous network configuration exists, continue to operate with those settings.  
1. If no network configuration exists, ignore node with missing filename.  
1. Send a notification packet to GSTV signifying an error has occurred.
1. GSTV will send another network configuration update

```javascript
{
  "id": String,  // invenco generated per notification
  "notificationType": String, // one of the defined notifications
  "status": "failure"
  "additionalInformation": "filename missing in config"
}
```

### What Invenco Sends if the expiryHours Key is Missing from the Network Configuration Update
1. If previous network configuration exists, continue to operate with those settings.  
1. If no network configuration exists, ignore node with missing expiryHours  
1. Send a notification packet to GSTV signifying an error has occurred.
1. GSTV will send another network configuration update

``` javascript
{
  "id": String,  // invenco generated per notification
  "notificationType": String, // one of the defined notifications
  "status": "failure"
  "additionalInformation": "expiryhours missing in config"
}
```

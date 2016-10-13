# Network Configuration Updates

Message sent with the network wide configuration values including shutdown hours and evergreen video settings

<!-- TOC depthFrom:1 depthTo:6 withLinks:1 updateOnSave:1 orderedList:0 -->

- [Network Configuration Updates](#network-configuration-updates)
	- [Key/Value Glossary](#keyvalue-glossary)
	- [Ideal Path](#ideal-path)
		- [What GSTV Sends to Invenco](#what-gstv-sends-to-invenco)
		- [What Invenco Sends to GSTV on a Successful Download](#what-invenco-sends-to-gstv-on-a-successful-download)
		- [What Invenco Sends to GSTV once Network Configuration Updates have been Applied](#what-invenco-sends-to-gstv-once-network-configuration-updates-have-been-applied)
	- [Error Path](#error-path)
		- [What Invenco Sends if the Network Configuration Update Can Not Be Parsed](#what-invenco-sends-if-the-network-configuration-update-can-not-be-parsed)
		- [What Invenco Sends if the Shutdown Hours are Missing from the Network Configuration Update](#what-invenco-sends-if-the-shutdown-hours-are-missing-from-the-network-configuration-update)
		- [What Invenco Sends if the Filename in a Node is Missing from the Network Configuration Update](#what-invenco-sends-if-the-filename-in-a-node-is-missing-from-the-network-configuration-update)
		- [What Invenco Sends if the expiryHours Key is Missing from the Network Configuration Update](#what-invenco-sends-if-the-expiryhours-key-is-missing-from-the-network-configuration-update)
	- [Standard Operating Procedure](#standard-operating-procedure)
		- [Applying Configuration Updates](#applying-configuration-updates)
		- [Error Handling](#error-handling)
			- [Default Error Handling](#default-error-handling)
			- [Default Configuration Error Handling](#default-configuration-error-handling)

<!-- /TOC -->

## Key/Value Glossary
### Field from GSTV Messages
- **guid** - TBD
- **updatedOn** - TBD
- **configuration** - TBD
		- **shutdownHours** - Number of hours a site should continue to play without connectivity. If site goes beyond this number of hours without connectivity, playback should halt at the site.
		- **evergreen** - Configuration to control swapping video files when updates to specific files are not received.
			- **filename** - Filename - including file extension - of video to control.
			- **expiryHours** - The number of hours a video can play before expiring and being swapped out or removed from playback. The timing starts from the time the site receives the video file.
			- **swapFilename** - Filename - including file extension - of video file to play if the expiryHours value has been exceeded. If blank, no video should play in the loop during the spot.

### Additional Fields in Invenco Responses

## Ideal Path
### What GSTV Sends to Invenco
```javascript
{
  "guid": String,
  "updatedOn": String,
  "configuration": [
    {
		  "shutdownHours": Number,
		  "evergreen":[
		    {
		      "filename": String,
		      "expiryHours": Number,
		      "swapFilename": String
		    },
		    {
		      "filename": String,
		      "expiryHours": Number,
		      "swapFilename": String
		    },
		    {
		      "filename": String,
		      "expiryHours": Number,
		      "swapFilename": String
		    },
		    {
		      "filename": String,
		      "expiryHours": Number,
		      "swapFilename": String
		    },
		    {
		      "filename": String,
		      "expiryHours": Number,
		      "swapFilename": String
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
  "notificationType": "CONFIGURATION_NETWORK_DOWNLOADED",
  "siteId": String,
  "status": "success",
}
```

### What Invenco Sends to GSTV once Network Configuration Updates have been Applied
```javascript
{
  "guid": String,
  "id": String,
  "notificationTimestamp": String
  "notificationType": "CONFIGURATION_NETWORK_APPLIED",
  "siteId": String,
  "status": "success",
}
```

## Error Path
If any part of a message causes an error the entire update will be rejected.

### What Invenco Sends if the Network Configuration Update Can Not Be Parsed
Follow [Default Configuration Error Handling](#default-configuration-error-handling).

```javascript
{
  "guid": String,
  "id": String,
  "notificationTimestamp": String
  "notificationType": "CONFIGURATION_NETWORK_MALFORMED_DATA",
  "siteId": String,
  "status": "failure",
  "additionalInformation": ""
}
```

#### Specific Examples

### What Invenco Sends if the Network Configuration Update Notification Contains Unexpected Values
Follows [Default Configuration Error Handling](#default-configuration-error-handling)

```javascript
{
  "guid": String,
  "id": String,
  "notificationTimestamp": String
  "notificationType": "CONFIGURATION_NETWORK_UNEXPECTED_VALUE",
  "siteId": String,
  "status": "failure",
  "additionalInformation": ""
}
```

#### Specific Examples

### What Invenco Sends if the Site Configuration Update Notification is Missing Values
Follows [Default Configuration Error Handling](#default-configuration-error-handling)

The additionalInformation field will contain a comma separated list of the keys without values.

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

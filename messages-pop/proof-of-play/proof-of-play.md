# POP Messages - Proof of Play

<!-- TOC depthFrom:1 depthTo:6 withLinks:1 updateOnSave:1 orderedList:0 -->

- [Proof of PLay Updates](#proofofplay-updates)
	- [Key/Value Glossary](#keyvalue-glossary)
		- [Field from Invenco Messages](#field-from-invenco-messages)
	- [Ideal Path](#ideal-path)
		- [What Invenco Sends to GSTV](#what-invenco-sends-to-gstv)
	- [Error Path](#error-path)
		- [What Invenco Sends if Post to GSTV Fails](#what-invenco-sends-if-post-to-gstv-fails)

<!-- /TOC -->


## Key/Value Glossary
### Field from Invenco Messages
- **filename** -	Name of the video asset that has been displayed on a screen at a site.
- **assetId** -	Number assigned to the media asset by GSTV.  This number should be carried over from the playlist update notification.
- **tiNumber** -	The insertion order number that the asset was purchased as part of.  This value is carried over from the playlist update notification.
- **startTimestamp** -	The time in which the video asset started to play in yyyy-mm-dd HH:MM:SS format.
- **endTimestamp** - The time in which the video asset stopped playing in yyyy-mm-dd HH:MM:SS format.
- **screenState** -	For the 12", what state was the screen in during playback.
  - **Values** : "Full", "Partial"
- **siteId** - The Invenco name of the site.
- **screenId** - The id of the screen at the site YES.

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

## Standard Operating Procedure
### Applying Media Updates
1. Media is played on screen
2. Player generates POP message
3. POP message is sent to Invenco Cloud
  - **if failure**
	  - **Retry until success - Invenco must retain POP messages until successfully sent to GSTV
	- **if success**
	  - **Invenco sends POP message to GSTV
		  - **if failue**
			  - **Retry until sucess - Invenco must retain POP messages until successfully sent to GSTV
				- **If not successful after 3 retries, Follow [What Invenco Sends if Post to GSTV Fails](#what-invenco-sends-if-post-to-gstv-fails) 



## Error Path
### What Invenco Sends if Post to GSTV Fails

```javascript

{
  "id": String,
  "notificationType": String, // TBD
  "status": "failure",
  "additionalInformation": "Failed to post POP"
}

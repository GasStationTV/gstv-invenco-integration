# Playlist Updates

<!-- TOC depthFrom:1 depthTo:6 withLinks:1 updateOnSave:1 orderedList:0 -->

- [Playlist Updates](#playlist-updates)
	- [Key/Value Glossary](#keyvalue-glossary)
		- [Field from GSTV Messages](#field-from-gstv-messages)
	- [Ideal Path](#ideal-path)
		- [What GSTV Sends to Invenco](#what-gstv-sends-to-invenco)
		- [What Invenco Sends to GSTV on a Successful Download](#what-invenco-sends-to-gstv-on-a-successful-download)
		- [What Invenco Sends to GSTV once Playlist Updates have been Applied at a Site](#what-invenco-sends-to-gstv-once-playlist-updates-have-been-applied-at-a-site)
	- [Error Path](#error-path)
		- [What Invenco Sends If Playlist can't be parsed](#what-invenco-sends-if-playlist-cant-be-parsed)
		- [What Invenco Sends If Site in Playlist does not exist](#what-invenco-sends-if-site-in-playlist-does-not-exist)
		- [What Invenco Sends If Media File in Playlist Does Not Exist in Invenco Library](#what-invenco-sends-if-media-file-in-playlist-does-not-exist-in-invenco-library)
		- [Error Handling](#error-handling)
			- [Playlist Error Handling](#playlist-error-handling)

<!-- /TOC -->

## Key/Value Glossary
### Field from GSTV Messages
- **playListUpdatedOn** - UTC datetime the playlist was updated.
- **guid** - Unique number generated for playlist. This value should be sent back to GSTV in applicable notification packet messages.
- **playList** - Detailed settings for playlist.
  - **siteId** - The Invenco name of the site.
    - **banners** -  Node to specify information about playing banner static image.  If this node is not present, no banner will play.
      - **filename** -  Name of image to be displayed as banner.
      - **start** -  Date in which the banner image should begin displaying.
      - **end** -  Date in which the banner image should end displaying.
      - **type** -  Specify's in which part of the fuelig transaction the image should display.  Values:  "Prefueling", "Postfueling"
  - **schedules** -  Node to specify the playlist details.
    - **date** -  specify's the date that the playlist is active.
    - **loops** -  Node which will describe each loop details for the day.
      - **loopNumber** -  Specify's the loop number. Each day will have multiple loops. Each loop should be played sequentially and repeated once the last loop has been played.
      - **assets** -  Node to specify the details of each asset to be played within the loop.
        - **assetId** -  Number assigned to the media asset by GSTV. This number should be included in the ProofofPlay packet coming from Invenco to GSTV.
        - **filename** -  Filename of the video to be played.
        - **type** -  The type of video. Values:  "Advertising", "Programming", "BrandedMessaging", and "RPA"
        - **start** -  Date in which the video should begin displaying.
        - **end** -  Date in which the video should end displaying.
        - **ioNumber** -  The insertion order number that the asset was purchased as part of. This value needs to be passed back to GSTV on the ProofofPlayPacket.
        - **dayparts** -  Node to specify specifc times of the day that a video should play. If no daypart is present, the video should play without regard to time.
          - **start** -  Local site time in which the asset should start playing if daypart is present
          - **end** -  Local site time in which the asset should stop playing if daypart is present



## Ideal Path
### What GSTV Sends to Invenco
```javascript
{
 "playListUpdatedOn": String, // UTC datetime
 "playList": [
   {
    "site": "FSD002",
    "banners": [
      {
        "filename": String,
        "start": String,
        "end": String,
        "type": "prefueling"
      },
      {
        "filename": String,
        "start": String,
        "end": String,
        "type": "postfueling"
      }
    ],
    "schedules": [
      {
        "date": String,
        "loops": [
          {
            "loopNumber": Number,
            "assets": [
              {
                "filename": String,
                "type": "BrandedMessaging",
                "dayparts": [
                  {
                    "start": String,
                    "end": String
                  },
                  {
                    "start": String,
                    "end": String
                  }
                ]
              },
              {
                "filename": String,
                "type": "Programming",
                "dayparts": [
                  {
                    "start": String,
                    "end": String
                  }
                ]
              },
              {
                "filename": String,
                "type": "Programming",
                "dayparts": [
                  {
                    "start": String,
                    "end": String
                  }
                ]
              },
              {
                "filename": String,
                "type": "Advertising",
                "start": String,
                "end": String,
                "ioNumber": Number,
                "dayparts": []
              },
              {
                "filename": String,
                "type": "BrandedMessaging",
                "dayparts": []
              },
              {
                "filename": String,
                "type": "RPA",
                "start": String,
                "end": String,
                "ioNumber": Number,
                "dayparts": []
              },
              {
                "filename": String,
                "type": "Programming",
                "dayparts": []
              }
            ]
          },
          {
            "loopNumber": Number,
            "assets": [
              {
                "filename": String,
                "type": "BrandedMessaging",
                "dayparts": []
              },
              {
                "filename": String,
                "type": "Programming",
                "dayparts": []
              },
              {
                "filename": String,
                "type": "BrandedMessaging",
                "dayparts": []
              },
              {
                "filename": String,
                "type": "Programming",
                "dayparts": []
              }
            ]
          },
          {
            "loopNumber": Number,
            "assets": [
              {
                "filename": String,
                "type": "BrandedMessaging",
                "dayparts": []
              },
              {
                "filename": String,
                "type": "Programming",
                "dayparts": []
              },
              {
                "filename": String,
                "type": "BrandedMessaging",
                "dayparts": []
              },
              {
                "filename": String,
                "type": "Programming",
                "dayparts": []
              }
            ]
          }
        ]
      }
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
  "notificationType": "", // TBD
  "siteId": String,
  "status": "success",
}
```

### What Invenco Sends to GSTV once Playlist Updates have been Applied at a Site
```javascript
{
  "guid": String,
  "id": String,
  "notificationTimestamp": String
  "notificationType": "", // TBD
  "siteId": String,
  "status": "success",
}
```

## Error Path
### What Invenco Sends If Playlist can't be parsed
Follow [Playlist Error Handling](#playlist-error-handling).

```javascript
{
  "id": String,  // invenco generated per notification
  "siteId": String,
  "guid": String,  // echo this value from the playlist if playlist change
  "notificationType": String, // one of the defined notifications
  "status": "failure"
  "additionalInformation": "Playlist can't be parsed"
}
```
### What Invenco Sends If Site in Playlist does not exist
Follow [Playlist Error Handling](#playlist-error-handling).

```javascript
{
  "id": String,  // invenco generated per notification
  "siteId": String,
  "guid": String,  // echo this value from the playlist if playlist change
  "notificationType": String, // one of the defined notifications
  "status": "failure"
  "additionalInformation": "Site does not exist"
}
```

### What Invenco Sends If Media File in Playlist Does Not Exist in Invenco Library
1. Invenco should retry downloading the file three times.
1. If the download is still unsuccessful follow [Playlist Error Handling](#playlist-error-handling).

```javascript
{
  "id": String,  // invenco generated per notification
  "siteId": String,
  "guid": String,  // echo this value from the playlist if playlist change
  "filename": String,
  "notificationType": String, // one of the defined notifications
  "status": "failure"
  "additionalInformation": "File not found in Invenco Library"
}
```

### Error Handling
#### Playlist Error Handling
1. Send a notification message to GSTV alerting that an error has occurred.
1. Playback does not stop.
1. GSTV sends another notification update message.

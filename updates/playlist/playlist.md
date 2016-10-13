# Playlist Updates

## Key/Value Glossary
### Field from GSTV Messages

- **playListUpdatedOn** - UTC datetime the playlist was updated.
- **guid** - Unique number generated for playlist.  This value should be sent back to GSTV in applicable notification packet messages.
- **playList** - Detailed settings for playlist.
- **siteId** - The Invenco name of the site.
  - **banners** -	Node to specify information about playing banner static image.  If this node is not present, no banner will play.
    - **filename** -	Name of image to be displayed as banner.
    - **start** -	Date in which the banner image should begin displaying.
    - **end** -	Date in which the banner image should end displaying.
    - **type** -	Specify's in which part of the fuelig transaction the image should display.  Values:  "Prefueling", "Postfueling"
- **schedules** -	Node to specify the playlist details.
  - **date** -	specify's the date that the playlist is active.
  - **loops** -	Node which will describe each loop details for the day.
  - **loopNumber** -	Specify's the loop number.  Each day will have multiple loops.  Each loop should be played sequentially and repeated once the last loop has been played.
  - **assets** -	Node to specify the details of each asset to be played within the loop.
    - **assetId** -	Number assigned to the media asset by GSTV.  This number should be included in the ProofofPlay packet coming from Invenco to GSTV.
    - **filename** -	Filename of the video to be played.
    - **type** -	The type of video.  Values:  "Advertising", "Programming", "BrandedMessaging", "RPA"
    - **start** -	Date in which the video should begin displaying.
    - **end** -	Date in which the video should end displaying.
    - **ioNumber** -	The insertion order number that the asset was purchased as part of.  This value needs to be passed back to GSTV on the ProofofPlayPacket.
    - **dayparts** -	Node to specify specifc times of the day that a video should play.  If no daypart is present, the video should play without regard to time.
      - **start** -	Local site time in which the asset should start playing if daypart is present
      - **end** -	Local site time in which the asset should sop playing if daypart is present



## Ideal Path
### What GSTV Sends to Invenco
```javascript
```

### What Invenco Sends to GSTV on Success
``` javascript
```

## Error Path

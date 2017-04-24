# Functional Requirements - Video Playback

The video playback system will allow for the following conditions:

1. Playback will be at 30FPS
1. One channel will exist. Assets for both the 5" and 12" model will be formatted as widescreen assets.
1. When downloading an asset, the player will ensure that the asset has been successfully transferred in full  
1. An asset may not play in every single rotation of the loop
	1. There will be up to 24 variations to a loop
		1. Assets will play in one or more loop variation
1. All assets may have a start datetime and/or an end datetime
	1. If an asset has a start datetime in the future the playback of that asset will not begin until that time
	1. Dayparts
		1. An asset may play for only a portion of the day - for example only before 12pm
		1. The start and end times for a daypart will be flexible
      1. We should be able to start playing an asset at 12:37 PM
	1. Weekparts
		1. An asset may play only on certain dates - for example only on July 14, but not on July 13.
1. All assets will have a type
	1. Advertising
	1. Programming
	1. Branded Messaging
	1. RPAs
1. All assets may have additional metadata
	1. TI Number
1. Programming assets will have a TTL - if a new file has not been downloaded in that amount of time the asset will be swapped for a predefined evergreen file
	1. If a predefined evergreen asset is not defined nothing will play
		1. We would rather not include AccuWeather than play an out of date forecast.
	1. The evergreen assets will be downloaded and stored as soon as possible - not when necessitated by TTL


| ID | Summary | Expected Results | Message to Reproduce This Test Case |
|---|---|---|---|
| 165 | Playlist - Update - Notifications - Update with all valid parameters | Correct number of MEDIA_CHECKS success message delivered to GSTV queue. PLAYLIST_CONFIGURATION success message delivered to GSTV queue. |  |
| 170 | Playlist - Playback - Playback supports a playlist file with a single date |  |  |
| 171 | Playlist - Playback - Playback supports a playlist file with a multiple dates |  |  |
| 172 | Playlist - Playback - Daypart - Playback of asset starts at defined start time |  |  |
| 173 | Playlist - Playback - Daypart - Playback of asset ends at defined end time |  |  |
| 174 | Playlist - Playback - Daypart - Playback supports a playlist file with more than one dayparts that run at different times |  |  |
| 175 | Playlist - Playback - Playback supports a playlist file with 24 loop numbers |  |  |
| 176 | Playlist - Playback - Asset - Playback of an asset starts at a defined start date |  |  |
| 177 | Playlist - Playback - Asset - Playback of an asset ends at a defined end date |  |  |
| 178 | Playlist - Playback - Connectivity Issues - When connectivity is lost the last date for a playlist will continue playing and respect the ends dates on the assets - not the date of the schedule |  |  |
| 179 | Playlist - Playback - Banner - Prefueling - Playback of the banner happens in the pre-fueling state |  |  |
| 180 | Playlist - Playback - Banner - Postfueling - Playback of the banner happens in the post-fueling state |  |  |
| 181 | Playlist - Playback - Banner - Prefueling - Playback of the banner starts at the defined start date |  |  |
| 182 | Playlist - Playback - Banner - Playback of the banner ends at the defined end date |  |  |
| 183 | Playlist - Playback - Business Case - Playback of a playlist with an asset scheduled at greater than 100 percent SOV |  |  |
| 184 | Playlist - Playback - Business Case - Playback of a playlist with an asset scheduled at less than 100 percent SOV |  |  |
| 185 | Playlist - Playback - Business Case - Playback of playlist with rotating assets - 2 assets |  |  |
| 186 | Playlist - Playback - Business Case - Playback of playlist with rotating assets - 3 assets |  |  |
| 187 | Playlist - Playback - Business Case - Playback of playlist with rotating assets - 4 assets |  |  |
| 188 | Playlist - Playback - Business Case - Playback of playlist non-contiguous weekparts |  |  |
| 189 | Playlist - Playback - Business Case - Playback of playlist contiguous weekparts |  |  |
| 190 | Playlist - Playback - Synchronization - Playback is synchronization among multiple terminals |  |  |
| 191 | Playlist - Playback - Synchronization - If an asset is missing from one terminal continue synchronized playback on all other terminals |  |  |
| 192 | Playlist - Playback - Synchronization - Verify a placeholder image is shown on the non-playing terminal |  |  |
| 193 | Playlist - Playback - Synchronization - Start and continue synchronized playback on all terminals when the next asset present on all terminal |  |  |
| 194 | Playlist - Playback - Distribution - Media changes must be reflected within two hours |  |  |
| 195 | Playlist - Playback - Fueling States - Playback during fueling displays in fullscreen mode |  |  |
| 196 | Playlist - Playback - Fueling State - Playback during prefueling and post-fueling plays in PIP mode |  |  |
| 197 | Playlist - Playback - Fueling State - Playback transitions from PIP to fullscreen |  |  |
| 198 | Playlist - Playback - Fueling State - Playback transitions from fullscreen to PIP |  |  |
| 199 | Playlist - Update - Notifications - GUID - Entry is missing | PLAYLIST_VALIDATION failure message delivered to GSTV queue |  |
| 200 | Playlist - Update - Notifications - GUID - Empty string | PLAYLIST_VALIDATION failure message delivered to GSTV queue |  |
| 201 | Playlist - Update - Notifications - UpdatedOn - Is Missing | PLAYLIST_VALIDATION failure message delivered to GSTV queue |  |
| 202 | Playlist - Update - Notifications - UpdatedOn - Dates with different format other then specified by GSTV requirements | PLAYLIST_VALIDATION failure message delivered to GSTV queue |  |
| 203 | Playlist - Update - Notifications - UpdatedOn - Invalid date | PLAYLIST_VALIDATION failure message delivered to GSTV queue |  |
| 204 | Playlist - Update - Notifications - UpdatedOn - Date in the past |  |  |
| 205 | Playlist - Update - Notifications - UpdatedOn - One file with some date, followed by another file with a date prior to the first file |  |  |
| 206 | Playlist - Update - Notifications - Playlist - Array is missing | PLAYLIST_VALIDATION failure message delivered to GSTV queue |  |
| 207 | Playlist - Update - Notifications - Playlist - Empty playlist object in the array | PLAYLIST_VALIDATION failure message delivered to GSTV queue |  |
| 208 | Playlist - Update - Notifications - Playlist - Array containing more than one object | PLAYLIST_VALIDATION failure message delivered to GSTV queue |  |
| 209 | Playlist - Update - Notifications - Banner - Missing file extension | PLAYLIST_VALIDATION failure message delivered to GSTV queue |  |
| 210 | Playlist - Update - Notifications - Schedule Date - Incorrectly formatted | PLAYLIST_VALIDATION failure message delivered to GSTV queue |  |
| 211 | Playlist - Update - Notifications - Loop Number - Incorrectly formatted | PLAYLIST_VALIDATION failure message delivered to GSTV queue |  |
| 212 | Playlist - Update - Notifications - Asset - Filename missing extension | PLAYLIST_VALIDATION failure message delivered to GSTV queue |  |
| 213 | Playlist - Update - Notifications - Start Date - Incorrectly formatted | PLAYLIST_VALIDATION failure message delivered to GSTV queue |  |
| 214 | Playlist - Update - Notifications - End Date - Incorrectly formatted | PLAYLIST_VALIDATION failure message delivered to GSTV queue |  |
| 215 | Playlist - Update - Notifications - Start Time - Incorrectly formatted | PLAYLIST_VALIDATION failure message delivered to GSTV queue |  |
| 216 | Playlist - Update - Notifications - End Time - Incorrectly formatted | PLAYLIST_VALIDATION failure message delivered to GSTV queue |  |
| 217 | Playlist - Update - Notifications - SiteId is Missing | PLAYLIST_VALIDATION failure message delivered to GSTV queue |  |
| 218 | Playlist - Update - Notifications - Banner - Missing filename | PLAYLIST_VALIDATION failure message delivered to GSTV queue |  |
| 219 | Playlist - Update - Notifications - Banner - Type missing | PLAYLIST_VALIDATION failure message delivered to GSTV queue |  |
| 220 | Playlist - Update - Notifications - Banner - Start date missing | PLAYLIST_VALIDATION failure message delivered to GSTV queue |  |
| 221 | Playlist - Update - Notifications - Banner - End date missing | PLAYLIST_VALIDATION failure message delivered to GSTV queue |  |
| 222 | Playlist - Update - Notifications - Schedules - Array is missing | PLAYLIST_VALIDATION failure message delivered to GSTV queue |  |
| 223 | Playlist - Update - Notifications - Schedules - Array with an empty object | PLAYLIST_VALIDATION failure message delivered to GSTV queue |  |
| 224 | Playlist - Update - Notifications - segmentId - Is missing | PLAYLIST_VALIDATION failure message delivered to GSTV queue |  |
| 225 | Playlist - Update - Notifications - Loop - Array is missing | PLAYLIST_VALIDATION failure message delivered to GSTV queue |  |
| 226 | Playlist - Update - Notifications - Loop - Empty loop object in the array | PLAYLIST_VALIDATION failure message delivered to GSTV queue |  |
| 227 | Playlist - Update - Notifications - Loop - loopNumber - Is missing | PLAYLIST_VALIDATION failure message delivered to GSTV queue |  |
| 228 | Playlist - Update - Notifications - asset array is missing or there is an empty asset object in the array | PLAYLIST_VALIDATION failure message delivered to GSTV queue |  |
| 229 | Playlist - Update - Notifications - assetId is missing | PLAYLIST_VALIDATION failure message delivered to GSTV queue |  |
| 230 | Playlist - Update - Notifications - Asset - Missing filename | PLAYLIST_VALIDATION failure message delivered to GSTV queue |  |
| 231 | Playlist - Update - Notifications - Asset - Missing type | PLAYLIST_VALIDATION failure message delivered to GSTV queue |  |
| 232 | Playlist - Update - Notifications - Asset - Missing start date | PLAYLIST_VALIDATION failure message delivered to GSTV queue |  |
| 233 | Playlist - Update - Notifications - Asset - Missing end date | PLAYLIST_VALIDATION failure message delivered to GSTV queue |  |
| 234 | Playlist - Update - Notifications - Daypart - Array exists and any object in that array is missing the start | PLAYLIST_VALIDATION failure message delivered to GSTV queue |  |
| 235 | Playlist - Update - Notifications - Daypart - Array exists and any object in that array is missing the end | PLAYLIST_VALIDATION failure message delivered to GSTV queue |  |
| 236 | Playlist - Update - Notifications - Banner - Start Date is After End Date | PLAYLIST_VALIDATION failure message delivered to GSTV queue |  |
| 237 | Playlist - Update - Notifications - Asset - Start Date is After the End Date | PLAYLIST_VALIDATION failure message delivered to GSTV queue |  |
| 238 | Playlist - Update - Notifications - Daypart - Start Time is After End Time | PLAYLIST_VALIDATION failure message delivered to GSTV queue |  |
| 239 | Playlist - Update - Notifications - siteId - Does not exist | PLAYLIST_VALIDATION failure message delivered to GSTV queue |  |

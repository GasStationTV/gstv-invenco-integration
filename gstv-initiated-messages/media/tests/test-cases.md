| ID | Summary | Expected Results | Message to Reproduce This Test Case |
|---|---|---|---|
| 156 | Media - Update - Notifications - GUID - Entry is missing | CONFIGURATION_VALIDATION failure message delivered to GSTV queue. |  |
| 157 | Media - Update - Notifications - GUID - Empty string | CONFIGURATION_VALIDATION failure message delivered to GSTV queue. |  |
| 158 | Media - Update - Notifications - UpdatedOn - Is Missing | CONFIGURATION_VALIDATION failure message delivered to GSTV queue. |  |
| 159 | Media - Update - Notifications - UpdatedOn - Dates with different format other then specified by GSTV requirements | CONFIGURATION_VALIDATION failure message delivered to GSTV queue. |  |
| 160 | Media - Update - Notifications - UpdatedOn - Date in past |  |  |
| 161 | Media - Update - Notifications - UpdatedOn - One file with some date, followed by another file with a date prior to the first file |  |  |
| 162 | Media - Update - Notifications - Checksum - Is missing | CONFIGURATION_VALIDATION failure message delivered to GSTV queue. |  |
| 163 | Media - Update - Notifications - Checksum - Does not match with the actual checksum of the file |  |  |
| 164 | Media - Update - Notifications - File not present in the GSTV S3 bucket | MEDIA_VALIDATION success message delivered to GSTV queue. MEDIA_DOWNLOAD failure message delivered to GSTV queue. |  |
| 166 | Media - Update - Notifications - Update with all parameters valid |  |  |
| 167 | Media - Playback - Update with all parameters valid reflected |  |  |
| 168 | Media - Playback - Update with all parameters valid reflected at more than one terminal at a site |  |  |
| 169 | Media - Playback - Playback reflects new asset with the same name as an asset already at the terminal |  |  |

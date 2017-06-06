| ID | Summary | Expected Results | Message to Reproduce This Test Case |
|---|---|---|---|
| 131 | Configuration - Site - Update - Notifications - Update with all with parameters valid |  |  |
| 132 | Configuration - Site - Playback - Update with all parameters valid |  |  |
| 133 | Configuration - Site - Playback - Update with all parameters valid reflected at more than one terminal at a site |  |  |
| 134 | Configuration - Site - Playback - blankoutVideo - Playback reflects asset during next shutdown time that is different from the asset defined in Configuration - Network |  |  |
| 135 | Configuration - Site - Playback - hours - Playback shutdown times reflect the current day of the week at local time |  |  |
| 136 | Configuration - Site - Playback - hours - Playback shutdown time extends beyond 24 hours |  |  |
| 137 | Configuration - Site - Playback - volume - Playback sets volume level at value of startTime |  |  |
| 138 | Configuration - Site - Playback - volume - Playback increases or decreases volume for each new startTime |  |  |
| 139 | Configuration - Site - Playback - blankoutVideo - Playback reflects new asset during next shutdown period defined by openAt and closeAt |  |  |
| 140 | Configuration - Site - Playback - hours - Playback reflects changing values |  |  |
| 141 | Configuration - Site - Playback - volume - Playback reflects changing/removing values |  |  |
| 142 | Configuration - Site - Update - Notifications - GUID - Entry is missing | CONFIGURATION_VALIDATION failure message delivered to GSTV queue |  |
| 143 | Configuration - Site - Update - Notifications - GUID - Empty string | CONFIGURATION_VALIDATION failure message delivered to GSTV queue |  |
| 144 | Configuration - Site - Update - Notifications - UpdatedOn - Is missing | CONFIGURATION_VALIDATION failure message delivered to GSTV queue |  |
| 145 | Configuration - Site - Update - Notifications - UpdatedOn - Dates with different format other then specified by GSTV requirements | CONFIGURATION_VALIDATION failure message delivered to GSTV queue |  |
| 146 | Configuration - Site - Update - Notifications - UpdatedOn - Invalid date | CONFIGURATION_VALIDATION failure message delivered to GSTV queue |  |
| 147 | Configuration - Site - Update - Notifications - UpdatedOn - Date is in the past |  |  |
| 148 | Configuration - Site - Update - Notifications - Site-id does not exist | CONFIGURATION_VALIDATION failure message delivered to GSTV queue |  |
| 149 | Configuration - Site - Update - Notifications - Open At Time incorrectly formatted for a given day | CONFIGURATION_VALIDATION failure message delivered to GSTV queue |  |
| 150 | Configuration - Site - Update - Notifications - Close At Time incorrectly formatted for a given day | CONFIGURATION_VALIDATION failure message delivered to GSTV queue |  |
| 151 | Configuration - Site - Update - Notifications - Volume - Level incorrectly formatted | CONFIGURATION_VALIDATION failure message delivered to GSTV queue |  |
| 152 | Configuration - Site - Update - Notifications - Volume - Start Time incorrectly formatted | CONFIGURATION_VALIDATION failure message delivered to GSTV queue |  |
| 153 | Configuration - Site - Update - Notifications - Blankout video filename missing extension | CONFIGURATION_VALIDATION success message delivered to GSTV queue. MEDIA_CHECK failure message delivered to GSTV queue |  |
| 154 | Configuration - Site - Update - Notifications - Open At is later than Close At for a given day | CONFIGURATION_VALIDATION failure message delivered to GSTV queue |  |
| 155 | Configuration - Site - Update - Notifications - More than one object in the site-configuration update under the configuration array | CONFIGURATION_VALIDATION failure message delivered to GSTV queue |  |

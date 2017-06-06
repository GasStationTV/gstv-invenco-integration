| Test Case ID | Test Case Summary | Expected Results | Suppporting Requirements |
|---|---|---|---|
| 101 | Configuration - Network - Update - Notifications - Update with all parameters valid | Configuration - Network Update Notification Posted to Queue. |  |
| 102 | Configuration - Network - Playback - Update with all parameters valid |  |  |
| 103 | Configuration - Network - Playback - Update with all parameters valid reflected at more than one terminal at a site |  |  |
| 104 | Configuration - Network - Playback - shutdownHours - Playback stops after counter from last connectivity reaches the value defined in shutdownHours |  |  |
| 105 | Configuration - Network - Playback - blankoutvideo - Playback displays asset during next shutdown time period defined by openAt and closeAt in Configuration - Site |  |  |
| 106 | Configuration - Network - Playback - evergreen - Playback switches to asset defined by swapFilename after counter from last connectivity reaches value defined in expiryHours |  |  |
| 107 | Configuration - Network - Playback - shutdownHours - Playback functionality reflects changing values |  |  |
| 108 | Configuration - Network - Playback - blankoutvideo - Playback reflects new asset during next shutdown time period defined by openAt and closeAt in Configuration - Site |  |  |
| 109 | Configuration - Network - Playback - evergreen - Playback functionality reflects changing/removing values |  |  |
| 110 | Configuration - Network - Update - Notifications - GUID - Entry is missing | CONFIGURATION_VALIDATION failure message delivered to GSTV queue | https://github.com/GasStationTV/gstv-invenco-integration/blob/master/gstv-initiated-messages/configuration-network/configuration-network.md |
| 111 | Configuration - Network - Update - Notifications - GUID - Empty string | CONFIGURATION_VALIDATION failure message delivered to GSTV queue |  |
| 112 | Configuration - Network - Update - Notifications - UpdatedOn - Dates with different format other then specified by GSTV requirements | CONFIGURATION_VALIDATION failure message delivered to GSTV queue |  |
| 113 | Configuration - Network - Update - Notifications - UpdatedOn - Invalid date | CONFIGURATION_VALIDATION failure message delivered to GSTV queue |  |
| 114 | Configuration - Network - Update - Notifications - UpdatedOn - Date is in the past | CONFIGURATION_VALIDATION failure message delivered to GSTV queue |  |
| 115 | Configuration - Network - Update - Notifications - Shutdown hours - Negative | CONFIGURATION_VALIDATION failure message delivered to GSTV queue | https://github.com/GasStationTV/gstv-invenco-integration/blob/master/gstv-initiated-messages/configuration-network/configuration-network.md |
| 116 | Configuration - Network - Update - Notifications - Shutdown hours - With Characters | CONFIGURATION_VALIDATION failure message delivered to GSTV queue | https://github.com/GasStationTV/gstv-invenco-integration/blob/master/gstv-initiated-messages/configuration-network/configuration-network.md |
| 117 | Configuration - Network - Update - Notifications - Missing required field |  |  |
| 118 | Configuration - Network - Update - Notifications - Evergreen - Filename - Not specified | CONFIGURATION_VALIDATION failure message delivered to GSTV queue |  |
| 119 | Configuration - Network - Update - Notifications - Evergreen - Filename - Incorrect | Received a MEDIA_CHECK failure for the file that had the incorrect name. The CONFIGURATION_VALIDATION message contains a success status. |  |
| 120 | Configuration - Network - Update - Notifications - Evergreen - Filename - Different video format than supported |  |  |
| 121 | Configuration - Network - Update - Notifications - Evergreen - Expiry - Negative | CONFIGURATION_VALIDATION failure message delivered to GSTV queue | https://github.com/GasStationTV/gstv-invenco-integration/blob/master/gstv-initiated-messages/configuration-network/configuration-network.md |
| 122 | Configuration - Network - Update - Notifications - Evergreen - Expiry - With Characters | CONFIGURATION_VALIDATION failure message delivered to GSTV queue | https://github.com/GasStationTV/gstv-invenco-integration/blob/master/gstv-initiated-messages/configuration-network/configuration-network.md |
| 123 | Configuration - Network - Update - Notifications - Evergreen - Expiry - Value set to 0, Swapfilename not specified |  |  |
| 124 | Configuration - Network - Update - Notifications - Evergreen - Expiry - Value set to 0, Swapfilename incorrect | CONFIGURATION_VALIDATION failure message delivered to GSTV queue |  |
| 125 | Configuration - Network - Update - Notifications - Blankout - Filename is not specified | CONFIGURATION_VALIDATION failure message delivered to GSTV queue |  |
| 126 | Configuration - Network - Update - Notifications - Volume - Array present - Only start time is specified | CONFIGURATION_VALIDATION failure message delivered to GSTV queue |  |
| 127 | Configuration - Network - Update - Notifications - Volume - Array present - Start time in invalid format | CONFIGURATION_VALIDATION failure message delivered to GSTV queue |  |
| 128 | Configuration - Network - Update - Notifications - Volume - Array present - Only volume level is specified | CONFIGURATION_VALIDATION failure message delivered to GSTV queue |  |
| 129 | Configuration - Network - Update - Notifications - Volume - Array present - Level less than 0 | CONFIGURATION_VALIDATION failure message delivered to GSTV queue |  |
| 130 | Configuration - Network - Update - Notifications - Volume - Array present - Level greater than 100 | CONFIGURATION_VALIDATION failure message delivered to GSTV queue |  |\

## Global Processing
### Default File Missing at Terminal
  - Terminal will check Invenco cloud for required media
    - **If success**
      - Download required media to terminal
    - **If failure**
      - Invenco sends notification to GSTV to resend media update notification
      - GSTV sends media update notification to Invenco

### Update Notification Processing
- Media update notifications should be processed before playlist update notifications
  - If a playlist update is being processed when more media updates arrive, processing of the playlist should be completed prior to media updates
- Configuration changes are processed as they arrive, but site playback should not be interrupted

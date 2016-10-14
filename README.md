## Global Processing
### Site requires media that is not in its library
  - **Site will check Invenco cloud for required media**
    - **Invenco cloud has required media - YES**
      - **Download required media to site**
    - **Invenco cloud has required media - NO**
      - **Invenco sends notification to GSTV to resend media update notification**
      - **GSTV sends media update notification to Invenco
      
### Media update notifications should be processed before playlist update notifications
### Configuration changes are processed as they arrive, but site playback should not be interrupted
### If a playlist update is being processed when more media updates arrive, processing of the playlist should be completed prior to media updates


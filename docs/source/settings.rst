Settings
========

These are all the possible settings in settings.json.

.. code:: d

   string[string] fonts;
   string[] backupFonts;
   string defaultFont;

   bool muteMusic;
   bool muteSoundEffects;
   int volume;

   string mainScript;
   int textSpeed;
   string title;
   string loadTitle;
   SaveFile[string] saves;

   bool fullScreen;

   string[string] defaultCharacterNameColors;
   string dialoguePanelBackgroundColor;
   string dialoguePanelBorderColor;
   string namePanelBackgroundColor;
   string namePanelBorderColor;

   string loadText;
   string backText;

   string[string] meta;

   string saveButtonText;
   string exitButtonText;
   string settingsButtonText;
   string autoButtonTextOn;
   string autoButtonTextOff;

   bool dialogueHistory;

   string customStartView;

   string videoLoadingScreen;
   string videoLoadingMusic;

   bool disableLoadScreenMusic;

This is the default settings.json

.. code:: json

   {
       "fonts": {
           "msgothic": "data/fonts/msgothic.ttc",
           "Calibri": "data/fonts/calibri.ttf"
       },
       "backupFonts": [
           "msgothic"
       ],
       "defaultFont": "Calibri",
       "muteMusic": false,
       "muteSoundEffects": false,
       "volume": 20,
       "mainScript": "main",
       "textSpeed": 32,
       "title": "PROJECT DVN",
       "loadTitle": "LOADING PROJECT DVN",
       "saves": {},
       "fullScreen": false,
       "defaultCharacterNameColors": {},
       "dialoguePanelBackgroundColor": "000",
       "dialoguePanelBorderColor": "000",
       "namePanelBackgroundColor": "000",
       "namePanelBorderColor": "000",
       "loadText": "Load: ",
       "backText": "Back",
       "meta": null,
       "saveButtonText": "Save",
       "exitButtonText": "Exit",
       "settingsButtonText": "Settings",
       "autoButtonTextOn": "Auto: On",
       "autoButtonTextOff": "Auto: Off",
       "dialogueHistory": false,
       "disableLoadScreenMusic": true
   }

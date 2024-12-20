Customizing The Main Menu
=========================

You’re able to customize the main menu without building Project DVN.

Simply open the file *data/game/views/mainmenuview.json* to get started.

It looks like this by default:

.. code:: json

   {
     "items": [{
         "image": {
           "source": "MainMenuBackground",
           "position": [0,0],
           "location": "center"
         }
       }, {
         "image": {
           "source": "Logo",
           "position": [0,0],
           "location": "topCenter",
           "relativeY": "12"
         }
       }, {
         "label": {
           "name": "playLabel",
           "text": "New Game",
           "location": "center",
           "fontSize": 32,
           "shadow": true,
           "link": true,
           "events": ["initialize", "mouseUp"]
         }
       }, {
         "label": {
           "name": "loadLabel",
           "text": "Load Game",
           "location": "topCenter",
           "relativeY": "playLabelY+playLabelHeight+16",
           "fontSize": 32,
           "shadow": true,
           "link": true,
           "events": ["initialize", "mouseUp"]
         }
       }, {
         "label": {
           "name": "settingsLabel",
           "text": "Settings",
           "location": "topCenter",
           "relativeY": "loadLabelY+loadLabelHeight+16",
           "fontSize": 32,
           "shadow": true,
           "link": true,
           "events": ["initialize", "mouseUp"]
         }
       }, {
         "label": {
           "name": "exitLabel",
           "text": "Exit",
           "location": "topCenter",
           "relativeY": "settingsLabelY+settingsLabelHeight+16",
           "fontSize": 32,
           "shadow": true,
           "link": true,
           "events": ["initialize", "mouseUp"]
         }
       }]
   }

Full set of component properties can be seen here:

.. code:: d

   private alias UIItem = UIItemEntry[string];

   public final class UIItemEntry
   {
     // shared
     int[] position;
     string location;
     string[string] visibleWhen;
     int[] margin;
     int[] size;
     string name;
     string relativeX;
     string relativeY;
     string relativeW;
     string relativeH;
     string[] events;
     int addIndex;
     string fontName;
     size_t fontSize;

     // image, video & animation
     string source;

     // video & animation
     bool repeat;

     // label
     string text;
     bool shadow;
     bool link;

     // panel
     bool hasDisplay;
     UIItem[] items;

     // textbox
     int maxCharacters;
     int textPadding;
     string hideCharacter;

     // button
     bool fitToSize;
   }

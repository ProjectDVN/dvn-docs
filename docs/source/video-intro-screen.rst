Video Intro Screen
==================

First you must have video frames added to a folder. See
https://dvn-docs.readthedocs.io/en/latest/adding-video.html for more
information.

Next thing just open your settings.json and add the following
properties:

.. code:: json

   "videoLoadingScreen": "path/to/video/folder",
   "videoLoadingMusic": "NameOfMusic"

*videoLoadingMusic* is optional and if not specified then no music will
be played.

Where *path/to/video/folder* is the path to your video folder that
contains the video frames and *NameOfMusic* is a given entry of music in
the music.json file.

To add music see:
https://dvn-docs.readthedocs.io/en/latest/adding-music-and-sound-effects.html

After adding that setting then a video will be displayed before the main
menu is shown.

*Note: This will not override custom start view and thus a custom start
view will always take precedence over this view.)*

Adding Video
============

Video files are not supported, BUT Project DVN does support framed
videos in that every frame from a video can be extracted and played
back.

Basically extract all frames from a video using something like
https://www.ffmpeg.org/ then place them in a folder ex.
“data/game/videos/myvideo” where each file is named something like
“1.png” “2.png” etc. in the order you want them played.

When that is finished you can create a video component in your view and
display the video like below:

.. code:: d

   auto video = new Video(window, "data/game/videos/myvideo");
   addComponent(video);
   video.size = IntVector(1280, 720);
   video.position = IntVector(0,0);

You can use the event *onFinishedVideo* to handle when a video has
finished playing. This is useful if you have an intro view before the
main menu view and want the main menu displayed after the video
finishes.

Example:

.. code:: d

   video.onFinishedVideo({
       displayView("MainMenu");
   });

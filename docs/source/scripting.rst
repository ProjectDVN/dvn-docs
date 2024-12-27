Scripting
=========

In the folder data/game/scripts add your .vns files (short for Visual
Novel Script)

The file structure of a .vns file is simply an expanded upon INI file.

You may add folders to keep your files structured etc.

*main* is by default the main script executed when a new game is
started.

File Structure
--------------

Each script file has the following structure:

.. code:: ini

   [scene-name]
   script-properties

   [scene-name]
   script-properties

   ...

The first scene is generally called “main”.

The following example is the “Hello World!” of Project DVN.

.. code:: ini

   [main]
   t=Hello World!

Comments
--------

To add comments simply prefix a line with #.

Comments must be on a line by themselves, meaning they cannot be after a
statement etc.

Example:

.. code:: ini

   # This is a comment

.. code:: ini

   # The main script
   [main]
   # The text for the main script
   text:end=Hello World!

Properties
----------

Properties that must be present every time are:

-  text, option, act or view.

background=VALUE (bg=VALUE)
~~~~~~~~~~~~~~~~

Where *VALUE* is the name given for a background entry within the
resource file data/game/backgrounds.json

Example:

.. code:: ini

   background=MyBackground

music=VALUE (m=VALUE)
~~~~~~~~~~~

Where *VALUE* is the name given for a music entry within the resource
file data/game/music.json

Example:

.. code:: ini

   music=MyMusicTrack

sound=VALUE (s=VALUE)
~~~~~~~~~~~

Where *VALUE* is the name given for a sound effect entry within the
resource file data/game/music.json

Example:

.. code:: ini

   sound=MySoundEffect

char=VALUE (c=VALUE)
~~~~~~~~~~

Where *VALUE* is the name given for a character entry within the
resource file data/game/characters.json.

Creates a new character entry within the scene.

Example:

.. code:: ini

   char=Sakura_Casual_Smile

charName=VALUE (n=VALUE)
~~~~~~~~~~~~~~

Where *VALUE* is the name of the character speaking.

Example:

.. code:: ini

   charName=Sakura

charNamePos=VALUE (np=VALUE)
~~~~~~~~~~~~~~~~~

Where *VALUE* is a given value for the position of the name. Values
supported are *left*, *center* and *right*

Example:

.. code:: ini

   charNamePos=left

charColor=VALUE (cc=VALUE)
~~~~~~~~~~~~~~~

Where *VALUE* is a given hex code ex. fff for white; this sets the
character name color.

Example:

.. code:: ini

   charColor=fff

These values can be set per character name in settings.json using the
“defaultCharacterNameColors” property.

Example:

.. code:: json

   "defaultCharacterNameColors": {
       "Sakura": "f00"
   }

If not specified then it defaults to *fff*

charPos=VALUE (cp=VALUE)
~~~~~~~~~~~~~

Where *VALUE* is a given value for the position of the character. Values
supported are *topLeft*, *topCenter*, *topRight*, *left*, *center*,
*right*, *bottomLeft*, *bottomCenter*, *bottomRight*

Example:

.. code:: ini

   charPos=bottomLeft

If not specified then this defaults to *bottomLeft*.

charMovement=VALUE (cm=VALUE)
~~~~~~~~~~~~~

Where *VALUE* is a given movement value such as *top*, *right*, *bottom* or *left*.

Example:

.. code:: ini

   charMovement=left

charMovementSpeed=VALUE (cms=VALUE)
~~~~~~~~~~~~~

Where *VALUE* is a given integer for movement speed.

This can be used to override the default speed of 42.

Example:

.. code:: ini

   charMovementSpeed=50

characterFadeIn (cf)
~~~~~~~~~~~~~

Fades in the current character.

Example:

.. code:: ini

   characterFadeIn

text=VALUE (t=VALUE)
~~~~~~~~~~~~~~~~

Where *VALUE* is the text to display.

This has two purposes, showing text with options, when options are enabled as buttons OR
to create a new scene entry copying every scene entry asset from last scene entry. This simplifies scene writing.

Example:

.. code:: ini

   text=What do you want to do?
   option:park=Go to the park.
   option:train=Take the train.

Example:

.. code:: ini

   text=First text of the scene.
   text=Second text of the scene.
   text:next-scene=Final text of the scene.

text:SCENE=VALUE (t:SCENE=VALUE)
~~~~~~~~~~~~~~~~

Where *SCENE* is the next scene entry and *VALUE* is the text to
display. If *SCENE* is *end* then the story ends and the player will be
returned to the main menu.

Example:

.. code:: ini

   text:end=Hello Project DVN!

animation:X,Y=VALUE (ani:X,Y=VALUE)
~~~~~~~~~~~~~~~~~~~

Where *VALUE* is the source of the animation, *X* and *Y* are given x
and y coordinates for the animation to be displayed. Remember to add the
animation to the resource file data/game/animations.json

Example:

.. code:: ini

   animation:150,150=MyAnimation

animation:X,Y:REPEAT=VALUE (ani:X,Y:REPEAT=VALUE)
~~~~~~~~~~~~~~~~~~~~~~~~~~

Where *REPEAT* is a boolean value of whether the animation repeats until
next scene. Values supported are *true* and *false*.

Example:

.. code:: ini

   animation:150,150:true=MyAnimation

animation:X,Y:REPEAT:POSITION=VALUE (ani:X,Y:REPEAT:POSITION=VALUE)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Where *POSITION* is a given position for the animation. Values supported
are *topLeft*, *topCenter*, *topRight*, *left*, *center*, *right*,
*bottomLeft*, *bottomCenter*, *bottomRight*

Example:

.. code:: ini

   animation:0,0:true:center=MyAnimation

When position is used then it’s generally adviced to have x and y as
both 0.

image:X,Y=VALUE (i:X,Y=VALUE)
~~~~~~~~~~~~~~~

Where *VALUE* is the source of the image, *X* and *Y* are given x and y
coordinates for the image to be displayed. Remember to add the image to
the resource file data/resources/main.json

Example:

.. code:: ini

   image:150,150=MyImage

image:X,Y:POSITION=VALUE (i:X,Y:POSITION=VALUE)
~~~~~~~~~~~~~~~~~~~~~~~~

Where *POSITION* is a given position for the image. Values supported are
*topLeft*, *topCenter*, *topRight*, *left*, *center*, *right*,
*bottomLeft*, *bottomCenter*, *bottomRight*

Example:

.. code:: ini

   image:0,0:center=MyImage

When position is used then it’s generally adviced to have x and y as
both 0.

option:SCENE=VALUE (o:SCENE=VALUE)
~~~~~~~~~~~~~~~~~~

Where *SCENE* is the next scene entry when the option is chosen and
*VALUE* is the text to display for the option.

Example:

.. code:: ini

   [main]
   text:select=Do you enjoy Project DVN?

   [select]
   option:yes=Yes!
   option:no=No.

   [yes]
   text:end=Thank you so much!

   [no]
   text:end=Aw... How come?

act:SCENE:CONTINUE_TEXT=VALUE (a:SCENE:CONTINUE_TEXT=VALUE)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Where *SCENE* is the next scene entry, *CONTINUE_TEXT* is the text of
the continue label, *VALUE* is the text of the act view.

Example:

.. code:: ini

   [main]
   act:start:Start Story=The Beginning

   [start]
   text:end=Welcome to my story!

label:FONT_SIZE:X,Y:COLOR=VALUE (l:FONT_SIZE:X,Y:COLOR=VALUE)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Where *FONT_SIZE* is the size of the font, *X* is the x position, *Y* is
the y position, *COLOR* is the text color and *VALUE* is the text to
display.

Example:

.. code:: ini

   label:24:150,150:fff=This is some text on the screen!

view=VALUE
~~~~~~~~~~

Where *VALUE* is the name of the custom view to display.

Example:

.. code:: ini

   view=CustomView

hideDialogue
~~~~~~~~~~~~

Example:

.. code:: ini

   hideDialogue

hideButtons
~~~~~~~~~~~

Example:

.. code:: ini

   hideButtons

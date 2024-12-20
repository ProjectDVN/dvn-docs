Getting Started
===============

To create your first visual novel with Project DVN simply follow this
guide.

Requirements
------------

-  (Optional) Download a D compiler such as DMD from here:
   https://dlang.org/download.html
-  (Optional) Download dub (if not installed with the D compiler) here:
   https://github.com/dlang/dub/releases
-  (Required) Download the empty visual novel project here:
   https://github.com/ProjectDVN/Empty/archive/refs/heads/main.zip
   (Source Code + Windows x86_64 build)

You may skip downloading the D compiler and dub if you don’t wish to
modify any code and only wish to script your visual novel.

In that case skip **Building and running** and go straight to
https://dvn-docs.readthedocs.io/en/latest/getting-started.html#change-titles

Building (Compiling) (Optional)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

For Windows you can simply run the **build.bat** script which will
automatically build the project for you.

For other platforms such as Linux/macOS please compile using ex.
``dub build -a=x86_64`` on the correct folder.

You must modify dub.json to suit your platform, if you’re not on
Windows.

You may inspect build.bat and copy the behavior manually.

**Note: This step is only required if you downloaded a d compiler, dub
and wish to modify any code OR you want to run it on another platform
than Windows.**

For events you can use in your code etc. please see:
https://github.com/ProjectDVN/dvn?tab=readme-ov-file#events

1. Change titles
----------------

-  Open build/client/data/settings.json
-  Change “title” and “loadTitle” to whatever you desire.

2. Changing main backgrounds
----------------------------

-  Open build/client/data/backgrounds
-  Change the two black images to images you desire.

**loading.png** is used for the loading screen

**main.png** is used for the main menu, settings menu and by default the
act screen

3. Changing logo
----------------

-  Open build/client/data/game/images
-  Change logo.png to your desired image
-  Open build/client/data/resources/main.json
-  Change the size of the “Logo” entry to the size of your logo.

4. Changing game background
---------------------------

-  Open build/client/data/game/backgrounds/bg.png
-  Change it to your desired image

\**Note: It’s important the image has the size 1280x720 for it to work
optimally.

5. Changing character
---------------------

-  Open build/client/data/game/characters/Stickman.png
-  Change it to your desired image
-  Open build/client/data/game/characters.json
-  Change the size of the Stickman entry to match your desired image
   size.

**Note: If you change name of Stickman.png then you must also change the
path in characters.json**

6. Creating your first script
-----------------------------

-  Open build/client/data/game/scripts/main.vns
-  Change **background** to match your given background resource.
-  Change **char** to match your given character resource.
-  Change “Hello World!” to something else such as “Hello DVN!”.

7. Running your visual novel
----------------------------

-  Open build/client/DVN.exe

8. Changing Name And Icon
-------------------------

See:
https://github.com/ProjectDVN/dvn/wiki/9.-Changing-Executable-Name-And-Icon

Your visual novel should now be running.

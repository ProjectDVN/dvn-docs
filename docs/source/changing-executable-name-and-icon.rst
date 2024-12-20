Changing Executable Name And Icon
=================================

Changing Executable Name
------------------------

-  Open source/client/dub.json
-  Change ``"targetName": "DVN"``
-  Open build.bat
-  Change ``set CLIENT_OUTPUT="DVN.exe"`` to the new name.

*Alternatively you can just rename DVN.exe.*

Changing Executable Icon
------------------------

This is a little more tricky than just changing the name of the
executable.

First you need to download `Resource
Hacker `__

You must also have an icon ready already ex. a 128x128 .ico file.

Now follow the following steps.

-  Open ResourceHacker
-  Click on “Open” and find the executable file, by default “DVN.exe”
-  Click on the add image icon. |Add image icon|
-  Click “Select File …” and select your icon file.
-  Make sure Resource_Type is “ICONGROUP” and Resource Name is “ICON”
-  Click “Add Resource”
-  Now press “Save”

Your executable should now have the selected icon.

Example:

.. figure:: https://i.imgur.com/ACayMV8.png
   :alt: Example

   Example

.. |Add image icon| image:: https://i.imgur.com/zXIfoyV.png

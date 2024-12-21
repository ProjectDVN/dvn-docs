Modules And Functions
=====================

Here’s a list of modules, structs, classes and functions that can be
used during event handlers or in custom views.

There exist other functions and modules of course, but these are the
one’s recommended to use only.

import dvn;
-----------

These are all functions related to dvn directly.

.. code:: d

   void saveGame(GameSettings settings, string id, string scene, string background, string music);
   GameSettings getGlobalSettings();
   void saveGameSettings(string path);
   string getCurrentSaveId();
   SaveFile getCurrentSaveFile();
   string getMusicPath(string music);
   void displayView(string name);
   void displayLastSceneView();
   void displayScene(string scene);

   public Application getApplication();

   int EXT_GetApplicationFps();
   IntVector EXT_GetMousePosition();
   uint EXT_GetTicks();
   uint EXT_GetTicksRaw();
   void EXT_DisableSound();
   void EXT_EnableSound();
   void EXT_DisableMusic();
   void EXT_EnableMusic();
   void EXT_SetSoundVolume(int volume);
   void EXT_PlayLastMusic();
   void EXT_PlayMusic(string path);
   void EXT_PauseMusic();
   void EXT_StopMusic();
   void EXT_PlaySound(string path);
   int EXT_GetFps();

   Color getColorByHex(string hex);
   Color getColorByInteger(uint integer);
   uint getIntegerByColor(Color color);
   string getHexByColor(Color color);
   string getNameByColor(Color color);
   Color getColorByName(string name, int alpha = 0xff);
   Color getColorByRGB(int r, int g, int b, int a = 0xff);
   Color changeAlpha(Color color, int a);

   ulong runDelayedTask(uint delay, void delegate() task, bool repeat = false);
   ulong runDelayedTask(uint delay, bool delegate(DelayedTask) task, bool repeat = false);
   void removeDelayedTask(ulong id);

   bool isForeignCharacter(dchar c);
   bool isForeignText(dstring s);

   Json!S parseJson(S = string)(S jsonString);
   bool parseJsonSafe(S = string)(S jsonString, out Json!S json, out S[] errorMessages);
   T deserializeJson(T,S = string)(S jsonString);
   bool deserializeJsonSafe(T,S = string)(S jsonString, out T value, out S[] errorMessages);
   bool deserializeJsonObjectSafe(T,S = string)(Json!S json, out T value, out S[] errorMessages);
   S serializeJson(T,S = string)(T value, bool pretty = false);
   bool serializeJsonSafe(T,S = string)(T value, out S jsonString, bool pretty = false);
   Json!S serializeJsonObject(T,S = string)(T value);
   bool serializeJsonObjectSafe(T,S = string)(T value, out Json!S json);

These are all structs/classes related to UI.

.. code:: d

   public final class Application {}
   public abstract class View {}
   public final class Window {}

   struct Color(ubyte r, ubyte g, ubyte b, ubyte a);
   struct IntVector(int x, int y);

   public abstract class Component {}

   public final class Animation : Component {}

   public final class Button : Component {}
   public final class CheckBox : Component {}
   public final class DropDown : Component {}
   public final class Image : Component {}
   public final class Label : Component {}
   public final class Panel : Component {}
   public final class ScrollBar : Component {}
   public final class TextBox : Component {}

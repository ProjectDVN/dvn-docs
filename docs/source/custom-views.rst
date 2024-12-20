Custom Views
============

Creating The View
-----------------

First you need to create the view class.

.. code:: d

   public final class CustomView : View
   {
       public:
       final:
       this(Window window)
       {
           super(window);
       }

       protected override void onInitialize(bool useCache)
       {
           EXT_DisableKeyboardState();

           auto window = super.window;

           // Add components to the view here
       }
   }

Then you need to handle the ``loadingViews`` event, so you can add the
view to the current window.

.. code:: d

       override void loadingViews(Window window)
       {
           window.addView!CustomView("CustomView");
       }

Now you just need to display the view

Example On Adding The View To Main Menu
---------------------------------------

The below code creates a label that goes to your custom view in the main
menu:

.. code:: d

       override void renderMainMenuView(Window window, Label titleLabel, Label playLabel, Label loadLabel, Label settingsLabel, Label exitLabel)
       {
           auto settings = getGlobalSettings();

           auto view = playLabel.view;

           auto viewLabel = new Label(window);
               view.addComponent(viewLabel);
               viewLabel.fontName = settings.defaultFont;
               viewLabel.fontSize = 24;
               viewLabel.color = "fff".getColorByHex;
               viewLabel.text = "Go To Custom View";
               viewLabel.shadow = true;
               viewLabel.isLink = true;
               viewLabel.position = IntVector(150, 150);
               viewLabel.updateRect();

               viewLabel.onMouseButtonUp(new MouseButtonEventHandler((b,p) {
                   displayView("CustomView");
               }));
       }

Adding The View To Scripts
--------------------------

Simply add a scene where the only entry is the ``view`` element like
below:

.. code:: ini

   [my-scene]
   view=CustomView

Whenever you enter “my-scene” then it will display your custom view.

Useful functions for custom views:
----------------------------------

.. code:: d

   void displayView(string name);
   void displayLastSceneView();
   void displayScene(string scene);

For other modules and useful functions see:
https://dvn-docs.readthedocs.io/en/latest/modules-and-functions.html

Example View
------------

This view will go back to the main menu when you press “Go Back” and
goes to scene “test-scene” when you press “Next Scene”.

.. code:: d

   public final class CustomView : View
   {
       public:
       final:
       this(Window window)
       {
           super(window);
       }

       protected override void onInitialize(bool useCache)
       {
           import std.conv : to;
           import dvn.views.settingsview : backToScene;

           EXT_DisableKeyboardState();

           auto window = super.window;
           auto settings = getGlobalSettings();
           
           auto backLabel = new Label(window);
               addComponent(backLabel);
               backLabel.fontName = settings.defaultFont;
               backLabel.fontSize = 24;
               backLabel.color = "fff".getColorByHex;
               backLabel.text = "Go Back";
               backLabel.shadow = true;
               backLabel.isLink = true;
               backLabel.position = IntVector(16, 16);
               backLabel.updateRect();

               backLabel.onMouseButtonUp(new MouseButtonEventHandler((b,p) {
               displayView("MainMenu");
               }));

           auto nextLabel = new Label(window);
               addComponent(nextLabel);
               nextLabel.fontName = settings.defaultFont;
               nextLabel.fontSize = 24;
               nextLabel.color = "fff".getColorByHex;
               nextLabel.text = "Next Scene";
               nextLabel.shadow = true;
               nextLabel.isLink = true;
               nextLabel.position = IntVector(150, 150);
               nextLabel.updateRect();

               nextLabel.onMouseButtonUp(new MouseButtonEventHandler((b,p) {
                       displayScene("test-scene");
               }));
       }
   }

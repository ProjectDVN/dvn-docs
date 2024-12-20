Events
======

To control most of the engine there are a set of events that can be
called.

Simply define a class like below:

.. code:: d

   public final class Events : DvnEvents
   {
       public:
       final:
       // override events here ...
   }

Then override the event functions you need.

Ex.

.. code:: d

   public final class Events : DvnEvents
   {
       public:
       final:
       override void renderGameViewCharacterName(SceneCharacterName characterName, Label label, Panel panel)
       {
           panel.position = IntVector(150, 150); // The name panel will always be displayed at 150,150
       }
   }

Afterwards call the function ``DvnEvents.setEvents(new Events);`` to set
the events.

This can be called in your main function (In most cases it will be
called mainEx)

Full event function list:

.. code:: d

       // Global
       void loadingGame() {}
       void loadedGame() {}
       void savingGame(SaveFile[string] saves, SaveFile saveFile) {}
       void loadingViews(Window window) {}

       // Act View
       void beginActView(string actName, string continueText, string background, string sceneName) {}

       void renderActBackgroundImage(Image image) {}
       void renderActTitleLabel(Label label) {}
       void renderActBeginLabel(Label label) {}

       void endActView() {}

       // Game View
       void loadingGameScripts() {}
       void loadedGameScripts(SceneEntry[string] scenes) {}
       
       void beginGameView(string sceneName, string loadBackground, string loadMusic) {}
       
       void beginHandleScene(SceneEntry scene, SceneEntry nextScene, bool isEnding) {}
       
       void playingMusic(string music) {}
       void playingSound(string sound) {}

       void renderGameViewOverplayBegin(Panel overlay) {}
       void renderGameViewBackground(Image background) {}
       void renderGameViewCharacter(SceneCharacter character, Image image) {}
       void renderGameViewImage(SceneImage image, Image imageComponent) {}
       void renderGameViewAnimation(SceneAnimation animation, Animation animationComponent) {}
       void renderGameViewLabel(SceneLabel label, Label labelComponent) {}
       void renderGameViewDialoguePanel(Panel panel) {}
       void renderGameViewCharacterName(SceneCharacterName characterName, Label label, Panel panel) {}
       void renderGameViewOption(Label option) {}
       void renderGameViewOptionsFinished() {}
       void renderGameViewSaveButton(Button button) {}
       void renderGameViewExitButton(Button button) {}
       void renderGameViewSettingsButton(Button button) {}
       void renderGameViewAutoButton(Button button) {}
       void renderGameViewOverplayEnd(Panel overlay) {}
       void renderGameViewTextFinished(Label textLabel) {}

       void endGameView() {}

       // Settings View
       void renderSettingsDropDown(DropDown dropdown) {}
       void renderSettingsCheckBox(CheckBox checkbox) {}

       // Main Menu View
       void renderMainMenuView(Window window, Label titleLabel, Label playLabel, Label loadLabel, Label settingsLabel, Label exitLabel) {}

Production Example
==================

Here’s an example used in production by a visual novel that uses Project
DVN.

.. code:: d

   private const buttonBackgroundColor = "f48fb1";
   private const buttonBackgroundBottomColor = "f06292";
   private const buttonBorderColor = "ec407a";
   private const buttonShadowColor = "000";

   private const dropDownBackgroundColor = "f48fb1";
   private const dropDownBorderColor = "ec407a";
   private const dropDownShadowColor = "000";

   private const checkBoxBackgroundColor = "f48fb1";
   private const checkBoxBorderColor = "ec407a";

   public final class Events : DvnEvents
   {
       public:
       final:
       // override events here ...
       override void renderActTitleLabel(Label label)
       {
           auto window = label.window;
           auto view = label.view;

           auto logoImage = new Image(window, "LogoAlt");
           view.addComponent(logoImage);
           logoImage.position = IntVector(window.width - logoImage.width, 0);
           logoImage.show();
       }

       private Panel dialoguePanel;

       override void renderGameViewDialoguePanel(Panel panel)
       {
           dialoguePanel = panel;

           auto window = panel.window;

           panel.position = IntVector(16, panel.y);

           panel.size = IntVector(
               (window.width / 100) * 90,
               panel.height
           );
       }

       private Button saveButton;

       override void renderGameViewSaveButton(Button button)
       {
           saveButton = button;

           button.size = IntVector(138, button.height);
           button.position = IntVector(
               dialoguePanel.x + dialoguePanel.width + 16,
               dialoguePanel.y
           );

           button.defaultPaint.backgroundColor = buttonBackgroundColor.getColorByHex;
           button.defaultPaint.backgroundBottomColor = buttonBackgroundBottomColor.getColorByHex;
           button.defaultPaint.borderColor = buttonBorderColor.getColorByHex;
           button.defaultPaint.shadowColor = buttonShadowColor.getColorByHex;

           button.hoverPaint.backgroundColor = button.defaultPaint.backgroundColor.changeAlpha(220);
           button.hoverPaint.backgroundBottomColor = button.defaultPaint.backgroundBottomColor.changeAlpha(220);
           button.hoverPaint.borderColor = button.defaultPaint.borderColor.changeAlpha(220);
           button.hoverPaint.shadowColor = buttonShadowColor.getColorByHex;

           button.clickPaint.backgroundColor = button.defaultPaint.backgroundColor.changeAlpha(240);
           button.clickPaint.backgroundBottomColor = button.defaultPaint.backgroundBottomColor.changeAlpha(240);
           button.clickPaint.borderColor = button.defaultPaint.borderColor.changeAlpha(240);
           button.clickPaint.shadowColor = buttonShadowColor.getColorByHex;

           button.restyle();
           button.show();
       }
       
       override void renderGameViewExitButton(Button button)
       {
           auto window = button.window;
           button.position = IntVector(window.width - (button.width + 16), 16);

           button.defaultPaint.backgroundColor = buttonBackgroundColor.getColorByHex;
           button.defaultPaint.backgroundBottomColor = buttonBackgroundBottomColor.getColorByHex;
           button.defaultPaint.borderColor = buttonBorderColor.getColorByHex;
           button.defaultPaint.shadowColor = buttonShadowColor.getColorByHex;

           button.hoverPaint.backgroundColor = button.defaultPaint.backgroundColor.changeAlpha(220);
           button.hoverPaint.backgroundBottomColor = button.defaultPaint.backgroundBottomColor.changeAlpha(220);
           button.hoverPaint.borderColor = button.defaultPaint.borderColor.changeAlpha(220);
           button.hoverPaint.shadowColor = buttonShadowColor.getColorByHex;

           button.clickPaint.backgroundColor = button.defaultPaint.backgroundColor.changeAlpha(240);
           button.clickPaint.backgroundBottomColor = button.defaultPaint.backgroundBottomColor.changeAlpha(240);
           button.clickPaint.borderColor = button.defaultPaint.borderColor.changeAlpha(240);
           button.clickPaint.shadowColor = buttonShadowColor.getColorByHex;

           button.restyle();
           button.show();
       }
       
       override void renderGameViewSettingsButton(Button button)
       {
           button.size = IntVector(saveButton.width, button.height);

           button.defaultPaint.backgroundColor = buttonBackgroundColor.getColorByHex;
           button.defaultPaint.backgroundBottomColor = buttonBackgroundBottomColor.getColorByHex;
           button.defaultPaint.borderColor = buttonBorderColor.getColorByHex;
           button.defaultPaint.shadowColor = buttonShadowColor.getColorByHex;

           button.hoverPaint.backgroundColor = button.defaultPaint.backgroundColor.changeAlpha(220);
           button.hoverPaint.backgroundBottomColor = button.defaultPaint.backgroundBottomColor.changeAlpha(220);
           button.hoverPaint.borderColor = button.defaultPaint.borderColor.changeAlpha(220);
           button.hoverPaint.shadowColor = buttonShadowColor.getColorByHex;

           button.clickPaint.backgroundColor = button.defaultPaint.backgroundColor.changeAlpha(240);
           button.clickPaint.backgroundBottomColor = button.defaultPaint.backgroundBottomColor.changeAlpha(240);
           button.clickPaint.borderColor = button.defaultPaint.borderColor.changeAlpha(240);
           button.clickPaint.shadowColor = buttonShadowColor.getColorByHex;

           button.restyle();
           button.show();
       }

       override void renderGameViewAutoButton(Button button)
       {
           button.size = IntVector(saveButton.width, button.height);

           button.defaultPaint.backgroundColor = buttonBackgroundColor.getColorByHex;
           button.defaultPaint.backgroundBottomColor = buttonBackgroundBottomColor.getColorByHex;
           button.defaultPaint.borderColor = buttonBorderColor.getColorByHex;
           button.defaultPaint.shadowColor = buttonShadowColor.getColorByHex;

           button.hoverPaint.backgroundColor = button.defaultPaint.backgroundColor.changeAlpha(220);
           button.hoverPaint.backgroundBottomColor = button.defaultPaint.backgroundBottomColor.changeAlpha(220);
           button.hoverPaint.borderColor = button.defaultPaint.borderColor.changeAlpha(220);
           button.hoverPaint.shadowColor = buttonShadowColor.getColorByHex;

           button.clickPaint.backgroundColor = button.defaultPaint.backgroundColor.changeAlpha(240);
           button.clickPaint.backgroundBottomColor = button.defaultPaint.backgroundBottomColor.changeAlpha(240);
           button.clickPaint.borderColor = button.defaultPaint.borderColor.changeAlpha(240);
           button.clickPaint.shadowColor = buttonShadowColor.getColorByHex;

           button.restyle();
           button.show();
       }

       override void renderSettingsCheckBox(CheckBox checkbox)
       {
           checkbox.fillColor = checkBoxBackgroundColor.getColorByHex;
           checkbox.borderColor = checkBoxBorderColor.getColorByHex;
       }

       override void renderSettingsDropDown(DropDown dropdown)
       {
           dropdown.defaultPaint.backgroundColor = dropDownBackgroundColor.getColorByHex;
           dropdown.defaultPaint.backgroundBottomColor = dropDownBackgroundColor.getColorByHex;
           dropdown.defaultPaint.borderColor = dropDownBorderColor.getColorByHex;
           dropdown.defaultPaint.shadowColor = dropDownShadowColor.getColorByHex;

           dropdown.hoverPaint.backgroundColor = dropdown.defaultPaint.backgroundColor.changeAlpha(220);
           dropdown.hoverPaint.backgroundBottomColor = dropdown.defaultPaint.backgroundBottomColor.changeAlpha(220);
           dropdown.hoverPaint.borderColor = dropdown.defaultPaint.borderColor.changeAlpha(220);
           dropdown.hoverPaint.shadowColor = dropDownShadowColor.getColorByHex;

           dropdown.restyle();
           dropdown.show();
       }
   }

The above code makes the layout look like this:

.. figure:: https://i.imgur.com/pIazvMW.png
   :alt: Event preview result

   Event preview result

For a full list of modules and functions that can be used check out:
https://dvn-docs.readthedocs.io/en/latest/modules-and-functions.html

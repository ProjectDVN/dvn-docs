External Functions
============

Below is a list of all external types, functions etc. that interacts with or is a direct alias to SDL.

.. code-block:: d

    // Public aliases
    public alias EXT_GetWindowFlags          = SDL_GetWindowFlags;
    public alias EXT_WindowFlags             = SDL_WindowFlags;
    public alias EXT_GetError                = SDL_GetError;
    public alias EXT_SetWindowBordered       = SDL_SetWindowBordered;
    public alias EXT_bool                    = SDL_bool;
    public alias EXT_DestroyWindow           = SDL_DestroyWindow;
    public alias EXT_HideWindow              = SDL_HideWindow;
    public alias EXT_ShowWindow              = SDL_ShowWindow;
    public alias EXT_StopTextInput           = SDL_StopTextInput;
    public alias EXT_StartTextInput          = SDL_StartTextInput;
    public alias EXT_SetWindowFullscreen     = SDL_SetWindowFullscreen;
    public alias EXT_CreateRGBSurface        = SDL_CreateRGBSurface;
    public alias EXT_PIXELFORMAT_ARGB8888    = SDL_PIXELFORMAT_ARGB8888;
    public alias EXT_TEXTUREACCESS_STREAMING = SDL_TEXTUREACCESS_STREAMING;
    public alias EXT_SaveBMP                 = SDL_SaveBMP;
    public alias EXT_RenderReadPixels        = SDL_RenderReadPixels;
    public alias EXT_IMG_SavePNG             = IMG_SavePNG;
    public alias EXT_SetTextureAlphaMod      = SDL_SetTextureAlphaMod;
    public alias EXT_QueryTexture            = SDL_QueryTexture;
    public alias EXT_Point                   = SDL_Point;

    public alias Color                       = SDL_Color;
    public alias EXT_GetWindowFromID         = SDL_GetWindowFromID;

    public alias EXT_Window                  = SDL_Window*;
    public alias EXT_Screen                  = SDL_Renderer*;

    public alias EXT_Rectangle               = SDL_Rect*;
    public alias EXT_RectangleNative         = SDL_Rect;

    public alias EXT_Font                    = TTF_Font*;
    public alias EXT_Texture                 = SDL_Texture*;

    public alias EXT_IMG_Load                = IMG_Load;
    public alias EXT_RWFromConstMem          = SDL_RWFromConstMem;
    public alias EXT_IMG_Load_RW             = IMG_Load_RW;
    public alias EXT_RWops                   = SDL_RWops*;

    public alias EXT_RenderCopy              = SDL_RenderCopy;
    public alias EXT_RenderCopyEx            = SDL_RenderCopyEx;
    public alias EXT_DestroyTexture          = SDL_DestroyTexture;
    public alias EXT_FreeSurface             = SDL_FreeSurface;
    public alias EXT_RendererFlip            = SDL_RendererFlip;
    public alias EXT_Surface                 = SDL_Surface*;
    public alias EXT_CreateTextureFromSurface = SDL_CreateTextureFromSurface;
    public alias EXT_CreateTexture           = SDL_CreateTexture;
    public alias EXT_LockTexture             = SDL_LockTexture;
    public alias EXT_UnlockTexture           = SDL_UnlockTexture;
    public alias EXT_RenderUnicodeText       = TTF_RenderUNICODE_Blended;
    public alias EXT_UnicodeTextSize         = TTF_SizeUNICODE;
    public alias EXT_SetRenderRectangle      = SDL_RenderSetClipRect;

    public alias EXT_Delay                   = SDL_Delay;

    // Private aliases
    private alias EXT_SoundChunk             = Mix_Chunk*;
    private alias TextureAtlas               = EXT_Texture[];

    // Top-level functions

    // Texture / query helpers
    EXT_Point EXT_QueryTextureSize(EXT_Texture texture);

    // Initialization
    void EXT_Initialize();

    // Main loop timing
    void EXT_PreAplicationLoop(int fps);
    int  EXT_GetApplicationFps();
    int  EXT_GetRecommendedMovementFps();
    void EXT_PostApplicationLoop(int fps);

    // Mouse position
    IntVector EXT_GetMousePosition();

    // Event control
    void EXT_DisableEvents();
    void EXT_EnableEvents();
    bool EXT_ProcessEvents(Window[] windows);

    // Input mapping
    MouseButton EXT_MouseButton(SDL_D_MouseButton button);
    KeyboardKey EXT_KeyboardKey(SDL_Keycode keyCode);

    // Window / renderer creation
    EXT_Window EXT_CreateWindow(string title, IntVector size, bool isFullScreen);
    EXT_Screen EXT_CreateScreen(EXT_Window nativeWindow);

    // Rectangles
    EXT_Rectangle EXT_CreateEmptyRectangle();
    EXT_Rectangle EXT_CreateRectangle(Rectangle rectangle);

    // Drawing helpers
    bool EXT_SetScreenDrawColor(EXT_Screen screen, Color color);
    bool EXT_FillRectangle(EXT_Screen screen, EXT_Rectangle nativeRectangle);
    bool EXT_DrawRectangle(EXT_Screen screen, EXT_Rectangle nativeRectangle);
    bool EXT_ClearScreen(EXT_Screen screen);
    void EXT_PresentScreen(EXT_Screen screen);

    // Fonts
    EXT_Font EXT_GetFont(string path, size_t size);
    int      EXT_FontGlyphSupport(EXT_Font font, dchar c);

    // Sheets / tiles
    struct EXT_Sheet
    {
        EXT_Texture sheet;
        IntVector   columnSize;
        int         columnCount;
    }

    struct EXT_SheetEntry
    {
        EXT_Rectangle rect;
        EXT_Rectangle textureRect;
    }

    struct EXT_SheetRender
    {
        EXT_SheetEntry* entry;
        EXT_Texture     texture;
        IntVector       size;
    }

    EXT_Sheet      EXT_CREATE_TILESET(EXT_Screen screen, string path, IntVector columnSize, int columnCount);
    void           EXT_CLEAR_TILESET(EXT_Sheet tileset);
    EXT_Texture    EXT_CREATE_SHEET(SDL_Renderer* renderer, string path);
    EXT_Texture    EXT_CREATE_SHEET_BUFFER(SDL_Renderer* renderer, ubyte[] b);
    EXT_SheetEntry EXT_CREATE_SHEET_ENTRY(EXT_Texture sheet, FloatVector position, IntVector size, int row, int columns);

    // Ticks / timing / FPS
    void EXT_SetTicks();
    uint EXT_GetTicks();
    uint EXT_GetTicksRaw();
    int  EXT_GetFps();

    // Keyboard state & movement helpers
    void EXT_AllowWASDMovement();
    void EXT_DisallowWASDMovement();
    void EXT_EnableKeyboardState();
    void EXT_DisableKeyboardState();
    void EXT_InitializeKeyboardState();

    bool EXT_HoldsControl();
    bool EXT_MoveUp();
    bool EXT_MoveRight();
    bool EXT_MoveDown();
    bool EXT_MoveLeft();

    // Cursor helpers
    void EXT_CreateCursors();
    void EXT_ResetCursor();
    void EXT_SetIBeamCursor();
    void EXT_SetHandCursor();
    void EXT_BeginWait();
    void EXT_EndWait();
    void EXT_SetWaitCursor();

    // Ping
    void EXT_SetPing(long ping);
    long EXT_GetPing();

    // Sound / music enable/disable
    void EXT_DisableSound();
    void EXT_EnableSound();
    void EXT_DisableMusic();
    void EXT_EnableMusic();
    void EXT_DisableSoundEffects();
    void EXT_EnableSoundEffects();

    // Music control
    void EXT_SetSoundVolume(int volume);
    void EXT_ValidateMusic();
    void EXT_PlayLastMusic();
    void EXT_PlayMusic(string path);
    void EXT_PauseMusic();
    void EXT_StopMusic();

    // Sound effects
    void EXT_PlaySound(string path);

    // Texture atlas
    struct EXT_TextureAsset
    {
        EXT_Rectangle[] states;
        EXT_Texture     texture;
    }

    void               EXT_InitializeTextureAtlas(string name, int pageCount);
    void               EXT_AddTextureAtlasPage(EXT_Screen screen, string name, string path, int page);
    EXT_Texture        EXT_GetTextureAtlas(string name, int page);
    EXT_TextureAsset*  EXT_GetTextureAsset(string atlasName, int page, Rectangle location, int columns);

    // Types

    public class EXT_TextEntry
    {
        EXT_Texture   _texture;
        EXT_Rectangle _rect;
    }

    public class EXT_TextLabel
    {
        this(EXT_Screen screen, Application application);
        @property IntVector position();
        @property void      position(IntVector newPosition);
        @property int       x();
        @property int       y();
        @property string    fontName();
        @property void      fontName(string newFontName);
        @property size_t    fontSize();
        @property void      fontSize(size_t newFontSize);
        @property Color     color();
        @property void      color(Color newColor);
        @property dstring   text();
        @property void      text(dstring newText);
        @property IntVector size();
        @property int       width();
        @property int       height();
        @property bool      shadow();
        @property void      shadow(bool hasShadow);

        protected bool measureComponentSize(out IntVector size);
        public void update();
        void        show();
        void        hide();
        public void render();
        void        clean();
    }

    public class EXT_Panel
    {
        this(EXT_Screen screen, Application application);
        @property IntVector position();
        @property void      position(IntVector newPosition);
        @property int       x();
        @property int       y();
        @property Color     fillColor();
        @property void      fillColor(Color newColor);
        @property Color     borderColor();
        @property void      borderColor(Color newColor);
        @property IntVector size();
        @property void      size(IntVector newSize);
        @property int       width();
        @property int       height();

        void  update();
        void  show();
        void  hide();
        public void render();
        void  clean();
    }

    public class EXT_Image
    {
        this(Window window, string name);
        @property IntVector position();
        @property void      position(IntVector newPosition);
        @property int       x();
        @property int       y();
        @property Color     fillColor();
        @property void      fillColor(Color newColor);
        @property Color     borderColor();
        @property void      borderColor(Color newColor);
        @property IntVector size();
        @property int       width();
        @property int       height();
        @property string    name();
        @property void      name(string newName);

        void  update();
        void  show();
        void  hide();
        public void render();
        void  clean();
    }

    private final class EXT_Music
    {
        this();
        bool openFromFile(string music);
        void play();
        void pause();
        void stop();
        void clean();
    }

If you need something else you can import these modules:

.. code:: d
  
    import derelict.sdl2.sdl;
    import derelict.sdl2.image;
    import derelict.sdl2.mixer;
    import derelict.sdl2.ttf;
    import derelict.sdl2.net;

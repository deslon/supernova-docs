
## Description

This class return all platform system information that engine is running. This class is as singleton, all methods are virtual and in C++ should be acessed by [instance()](#instance). In Lua they can be acessed directly. For example:

=== ":octicons-file-code-16: `C++`"

    ``` c++
    int screenWidth = System::instance().getScreenWidth();
    ```

=== ":material-language-lua: `Lua`"

    ``` lua
    screenWidth = System.getScreenWidth()
    ```

### Methods

| Type          | Name                      |  Langs      |
| -----         | -----------               | ----------  |
| static System& | [instance](#instance) | :material-language-cpp: |
| virtual int | [getScreenWidth](#getscreenwidth) | :material-language-cpp: \| :material-language-lua: |
| virtual int | [getScreenHeight](#getscreenheight) | :material-language-cpp: \| :material-language-lua: |
| virtual void | [showVirtualKeyboard](#showvirtualkeyboard) | :material-language-cpp: \| :material-language-lua: |
| virtual void | [isFullscreen](#isfullscreen) | :material-language-cpp: \| :material-language-lua: |
| virtual void | [requestFullscreen](#requestfullscreen) | :material-language-cpp: \| :material-language-lua: |
| virtual void | [exitFullscreen](#exitfullscreen) | :material-language-cpp: \| :material-language-lua: |
| virtual void | [getDirSeparator](#getdirseparator) | :material-language-cpp: \| :material-language-lua: |
| virtual void | [getAssetPath](#getassetpath) | :material-language-cpp: \| :material-language-lua: |
| virtual void | [getUserDataPath](#getuserdatapath) | :material-language-cpp: \| :material-language-lua: |
| virtual void | [getLuaPath](#getluapath) | :material-language-cpp: \| :material-language-lua: |
| virtual void | [getShaderPath](#getshaderpath) | :material-language-cpp: \| :material-language-lua: |

## Methods details

### instance (:material-language-cpp:)

 * static System& **instance**()

Return instace of singleton System class.

 ---

### getScreenWidth

 * virtual int **getScreenWidth**()

Return size o screen width based on system platform resolution.

 ---

### getScreenHeight

 * virtual int **getScreenHeight**()

Return size o screen height based on system platform resolution.

 ---

### showVirtualKeyboard

 * virtual void **showVirtualKeyboard**()

Show virtual keyboard if device supports it.

 ---

### hideVirtualKeyboard

 * virtual void **hideVirtualKeyboard**()

Hide virtual keyboard if device supports it.

 ---

### isFullscreen

 * virtual bool **isFullscreen**()

Return true if fullscreen.

 ---

### isFullscreen

 * virtual bool **isFullscreen**()

Return true if fullscreen.

 ---

### requestFullscreen

 * virtual void **requestFullscreen**()

Request system for enter fullscreen.

 ---

### exitFullscreen

 * virtual void **exitFullscreen**()

Request system for exit fullscreen.

 ---

### getDirSeparator

 * virtual char **getDirSeparator**()

Return system dir separador. Ex: "/" for Linux and "\" for Windows

 ---

### getAssetPath

 * virtual std::string **getAssetPath**()

Return assets directory path.

 ---

### getUserDataPath

 * virtual std::string **getUserDataPath**()

Return user data directory path with write permission.

 ---

### getLuaPath

 * virtual std::string **getLuaPath**()

Return Lua directory path.

 ---

### getShaderPath

 * virtual std::string **getShaderPath**()

Return shader data directory.

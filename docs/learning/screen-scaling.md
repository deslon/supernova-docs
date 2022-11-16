To handle with the variety of resolutions and screen sizes of devices, Supernova have some options to choose the better scaling mode. All project code you must declare the size of canvas:

=== ":octicons-file-code-16: `C++`"
    ``` c++
    Engine::setCanvasSize(1000,480);
    ```
=== ":material-language-lua: `Lua`"
    ``` lua
    Engine.setCanvasSize(1000,480)
    ```

This is the base size you must use for design your project. For 3D projects this is used only for perspective view aspect, but for 2D projects this sizes are very important to positioning objects in screen.

There are 6 types of scaling mode divided by 2 categories.

## Dynamic canvas size modes

### FitWidth

This is **default** mode. This keeps canvas width but floats height. Canvas can be changed from original format, but only height changes. Should be used ```getPreferedCanvasWidth()```and ```getPreferedCanvasHeight()``` to get original canvas size.

=== ":octicons-file-code-16: `C++`"
    ``` c++
    Engine::setScalingMode(Scaling::FITWIDTH);
    ```
=== ":material-language-lua: `Lua`"
    ``` lua
    Engine.scalingMode = Scaling::FITWIDTH
    ```

![Fitwidth](../images/scaling/Fitwidth.png)

### FitHeight

It is similar to FitWidth. This keeps canvas height but floats width. Canvas can be changed from original format, but only width changes. Should be used ```getPreferedCanvasWidth()```and ```getPreferedCanvasHeight()``` to get original canvas size.

=== ":octicons-file-code-16: `C++`"
    ``` c++
    Engine::setScalingMode(Scaling::FITHEIGHT);
    ```
=== ":material-language-lua: `Lua`"
    ``` lua
    Engine.scalingMode = Scaling::FITHEIGHT
    ```

![Fitheight](../images/scaling/Fitheight.png)

### Native

This keeps canvas with native window resolution (width and height) and ignore canvas size by ``setCanvasSize()``.

=== ":octicons-file-code-16: `C++`"
    ``` c++
    Engine::setScalingMode(Scaling::NATIVE);
    ```
=== ":material-language-lua: `Lua`"
    ``` lua
    Engine.scalingMode = Scaling::NATIVE
    ```

![Stretch](../images/scaling/Native.png)

## Static canvas size modes

### Letterbox

This keeps canvas width and height but empty spaces can be show on screen.

=== ":octicons-file-code-16: `C++`"
    ``` c++
    Engine::setScalingMode(Scaling::LETTERBOX);
    ```
=== ":material-language-lua: `Lua`"
    ``` lua
    Engine.scalingMode = Scaling::LETTERBOX
    ```

![Letterbox](../images/scaling/Letterbox.png)

### Crop

This keeps canvas width and height but part of canvas can be out of screen (not in visible area).

=== ":octicons-file-code-16: `C++`"
    ``` c++
    Engine::setScalingMode(Scaling::CROP);
    ```
=== ":material-language-lua: `Lua`"
    ``` lua
    Engine.scalingMode = Scaling::CROP
    ```

![Crop](../images/scaling/Crop.png)

### Stretch

This keeps canvas width and height but scene objects can deform.

=== ":octicons-file-code-16: `C++`"
    ``` c++
    Engine::setScalingMode(Scaling::STRETCH);
    ```
=== ":material-language-lua: `Lua`"
    ``` lua
    Engine.scalingMode = Scaling::STRETCH
    ```

![Stretch](../images/scaling/Stretch.png)

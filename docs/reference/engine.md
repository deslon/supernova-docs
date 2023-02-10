
## Description

Control engine properties and define defaults to be used in all project. Also ```Engine``` class provides canvas info.

### Properties

| Type | Name | Default | Langs  |
| ----- | ----------- | ---------- | --------- |
| static [Scaling](#scaling) | [scalingMode](#scalingmode) | Scaling::FITWIDTH | :material-language-cpp: \| :material-language-lua:  |
| static [TextureStrategy](#texturestrategy) | [textureStrategy](#texturestrategy_1) | TextureStrategy::RESAMPLE | :material-language-cpp: \| :material-language-lua: |
| static bool | [callMouseInTouchEvent](#callmouseintouchevent) | false | :material-language-cpp: \| :material-language-lua: |
| static bool | [callTouchInMouseEvent](#calltouchinmouseevent) | false | :material-language-cpp: \| :material-language-lua: |
| static bool | [useDegrees](#usedegrees) | true | :material-language-cpp: \| :material-language-lua: |
| static bool | [automaticTransparency](#automatictransparency) | true | :material-language-cpp: \| :material-language-lua: |
| static bool | [allowEventsOutCanvas](#alloweventsoutcanvas) | false | :material-language-cpp: \| :material-language-lua: |
| static bool | [fixedTimeSceneUpdate](#fixedtimesceneupdate) | false | :material-language-cpp: \| :material-language-lua: |
| static bool | [updateTime](#updatetime) | 0.03 | :material-language-cpp: \| :material-language-lua: |

### Methods

| Type          | Name                      |  Langs      |
| -----         | -----------               | ----------  |
| static void | [setScene](#setscene) | :material-language-cpp: \| :material-language-lua: |
| static Scene\* | [getScene](#getscene) | :material-language-cpp: \| :material-language-lua: |
| static void | [addSceneLayer](#addscenelayer) | :material-language-cpp: \| :material-language-lua: |
| static int | [getCanvasWidth](#getcanvaswidth) | :material-language-cpp: \| :material-language-lua: |
| static int | [getCanvasHeight](#getcanvasheight) | :material-language-cpp: \| :material-language-lua: |
| static int | [getPreferedCanvasWidth](#getpreferedcanvaswidth) | :material-language-cpp: \| :material-language-lua: |
| static int  | [getPreferedCanvasHeight](#getpreferedcanvasheight) | :material-language-cpp: \| :material-language-lua: |
| static [Rect](rect.md)  | [getViewRect](#getviewrect)     | :material-language-cpp: \| :material-language-lua: |
| static void  | [setUpdateTimeMS](#setupdatetimems)     | :material-language-cpp: \| :material-language-lua: |
| static void  | [getSceneUpdateTime](#getsceneupdatetime)     | :material-language-cpp: \| :material-language-lua: |
| static [Platform](#platform)  | [getPlatform](#getplatform)     | :material-language-cpp: \| :material-language-lua: |
| static [GraphicBackend](#graphicbackend)  | [getGraphicBackend](#getgraphicbackend)     | :material-language-cpp: \| :material-language-lua: |
| static void  | [isOpenGL](#isopengl)     | :material-language-cpp: \| :material-language-lua: |
| static void  | [getFramerate](#getframerate)     | :material-language-cpp: \| :material-language-lua: |
| static void  | [getDeltatime](#getdeltatime)     | :material-language-cpp: \| :material-language-lua: |

### Callback events

| Callback          | Name                      |  Langs      |
| -----         | -----------               | ----------  |
| void() | [onViewLoaded](#onviewloaded) | :material-language-cpp: \| :material-language-lua: |
| void() | [onViewChanged](#onviewchanged) | :material-language-cpp: \| :material-language-lua: |
| void() | [onDraw](#ondraw) | :material-language-cpp: \| :material-language-lua: |
| void() | [onUpdate](#onupdate) | :material-language-cpp: \| :material-language-lua: |
| void() | [onShutdown](#onshutdown) | :material-language-cpp: \| :material-language-lua: |
| void(int,float,float) | [onTouchStart](#ontouchstart) | :material-language-cpp: \| :material-language-lua: |
| void(int,float,float) | [onTouchEnd](#ontouchend) | :material-language-cpp: \| :material-language-lua: |
| void(int,float,float) | [onTouchMove](#ontouchmove) | :material-language-cpp: \| :material-language-lua: |
| void() | [onTouchCancel](#ontouchcancel) | :material-language-cpp: \| :material-language-lua: |
| void(int,float,float,int) | [onMouseDown](#onmousedown) | :material-language-cpp: \| :material-language-lua: |
| void(int,float,float,int) | [onMouseUp](#onmouseup) | :material-language-cpp: \| :material-language-lua: |
| void(float,float,int) | [onMouseScroll](#onmousescroll) | :material-language-cpp: \| :material-language-lua: |
| void(float,float,int) | [onMouseMove](#onmousemove) | :material-language-cpp: \| :material-language-lua: |
| void() | [onMouseEnter](#onmouseenter) | :material-language-cpp: \| :material-language-lua: |
| void() | [onMouseLeave](#onmouseleave) | :material-language-cpp: \| :material-language-lua: |
| void(int,bool,int) | [onKeyDown](#onkeydown) | :material-language-cpp: \| :material-language-lua: |
| void(int,bool,int) | [onKeyUp](#onkeyup) | :material-language-cpp: \| :material-language-lua: |
| void(wchar_t) | [onCharInput](#oncharinput) | :material-language-cpp: \| :material-language-lua: |


### Tutorials

 * [Screen Scaling](../learning/screen-scaling.md)

##  Enumerations

### Scaling

* **FITWIDTH** - Keeps canvas width but floats height
* **FITHEIGHT** - Keeps canvas height but floats width
* **LETTERBOX** - Keeps canvas width and height but empty spaces can be show on screen
* **CROP** - Keeps canvas width and height but part of canvas can be out of screen
* **STRETCH** - Keeps canvas width and height but scene objects can deform
* **NATIVE** - Keeps canvas with native window resolution (width and height)

 ---

### TextureStrategy

* **FIT** - Uses FIT algorithm to change texture resolution
* **RESAMPLE** - Uses RESAMPLE algorithm to change texture resolution
* **NONE** - No changes in texture resolution

 ---

### Platform

* **MacOS** - The engine is running on MacOS
* **iOS** - The engine is running on iOS
* **Web** - The engine is running in WebGL/HTML5
* **Android** - The engine is running on Android
* **Linux** - The engine is running on Linux
* **Windows** - The engine is running in Windows

 ---

### GraphicBackend

* **GLCORE33** - The engine graphic backend is OpenGL 3.3
* **GLES2** - The engine graphic backend is OpenGL ES 2
* **GLES3** - The engine graphic backend is OpenGL ES 3
* **D3D11** - The engine graphic backend is DirectX 11
* **METAL** - The engine graphic backend is Metal
* **WGPU** - The engine graphic backend is WebGPU (*for future use*)


## Property details


### scalingMode

* *Setter*: static void **setScalingMode**([Scaling](#scaling) scalingMode) 
* *Getter*: static [Scaling](#scaling) **getScalingMode**() 

Change scaling mode of screen depending of device resolution. Details in tutorial [Screen Scaling](../learning/screen-scaling.md)

 ---

### textureStrategy

* *Setter*: static void **setTextureStrategy**([TextureStrategy](#texturestrategy) textureStrategy)
* *Getter*: static [TextureStrategy](#texturestrategy) **getTextureStrategy()**

Change texture strategy to resize non power-of-two textures.

 ---

### callMouseInTouchEvent

* *Setter*: static void **setCallMouseInTouchEvent**(bool callMouseInTouchEvent)
* *Getter*: static bool **isCallMouseInTouchEvent**()

Call mouse events if touch events is called.

 ---

### callTouchInMouseEvent

* *Setter*: static void **setCallTouchInMouseEvent**(bool callTouchInMouseEvent)
* *Getter*: static bool **isCallTouchInMouseEvent**()

Call touch events if mouse events is called.

 ---

### useDegrees

* *Setter*: static void **setUseDegrees**(bool useDegrees)
* *Getter*: static bool **isUseDegrees**()

Uses degress as default of engine angles. If not it uses radian.

 ---

### automaticTransparency

* *Setter*: static void **setAutomaticTransparency**(bool automaticTransparency)
* *Getter*: static bool **isAutomaticTransparency**()

Set automatic transparency detection in all objects. It doesn't affect transparency itself, just detection to sort transparent objects in scene, for example.

 ---

### allowEventsOutCanvas

* *Setter*: static void **setAllowEventsOutCanvas**(bool allowEventsOutCanvas)
* *Getter*: static bool **isAllowEventsOutCanvas**();

Allow mouse events to be mapped out of canvas.

 ---

### fixedTimeSceneUpdate

* *Setter*: static void **setFixedTimeSceneUpdate**(bool fixedTimeSceneUpdate)
* *Getter*: static bool **isFixedTimeSceneUpdate**();

If true, scene update events will be called by a fixed time defined by ```setUpdateTime()```, if false scene update events will be called with draw events.

 ---

### updateTime

* *Setter*: static void **setUpdateTime**(float updateTime)
* *Getter*: static float **getUpdateTime**();

Define update time in **seconds** for update events callbacks. If ```setFixedTimeSceneUpdate()``` is set true, scene update events is also called by fixed time.

## Methods details

### setScene

 * static void **setScene**(Scene* scene)

Set main scene of project.

 ---

### getScene

 * static Scene\* **getScene**()

Get main scene of project.

 ---

### addSceneLayer

 * static void **addSceneLayer**(Scene\* scene)

Added a scene to stay one layer below main scene. Could be used in a GUI scene.

 ---

### getCanvasWidth

 * static int **getCanvasWidth**()

Get canvas width. This value can be affected by screen scaling mode.

 ---

### getCanvasHeight

 * static int **getCanvasHeight**()

Get canvas height. This value can be affected by screen scaling mode.

 ---

### setCanvasSize

 * static void **setCanvasSize**(int canvasWidth, int canvasHeight)

Set prefered canvas size for screen. The values setted could be affected by scaling mode. Original setted value can get by [getPreferedCanvasWidth()](#getpreferedcanvaswidth) and [getPreferedCanvasHeight()](#getpreferedcanvasheight).

 ---

### getPreferedCanvasWidth

 * static int **getPreferedCanvasWidth**()

Get canvas width that is not modified by screen scaling setup. Prefered canvas is the same value setted in engine.

 ---

### getPreferedCanvasHeight

 * static int **getPreferedCanvasHeight**()

Get canvas height that is not modified by screen scaling setup. Prefered canvas is the same value setted in engine.

  ---

### getViewRect

 * static Rect **getViewRect**()

Get viewport sizes calculaded based on *canvas size*, *screen size* and *scaling mode*.

  ---

### setUpdateTimeMS

 * static void **setUpdateTimeMS**(unsigned int updateTimeMS)

The same of [updateTime](#updatetime) but this method accept time in **milliseconds**.

  ---

### getSceneUpdateTime

 * static float **getSceneUpdateTime**()

Return update time in **seconds** of scene. If  [fixedTimeSceneUpdate](#fixedtimesceneupdate) is true, return the same value of [updateTime](#updatetime). If not true, return the same of  [getDeltatime()](#getdeltatime).

  ---

### getPlatform

 * static [Platform](#platform) **getPlatform**()

Return system platform that engine is running.

  ---

### getGraphicBackend

 * static [GraphicBackend](#graphicbackend) **getGraphicBackend**()

Return graphic backend that engine is running.

  ---

### isOpenGL

 * static bool **isOpenGL**()

Return true if OpenGL (version 3.3, ES 2 or ES 3) is running as graphic backend.

  ---

### getFramerate

 * static float **getFramerate**()

Return framerate (FPS) of engine.

  ---

### getDeltatime

 * static float **getDeltatime**()

Return deltatime in **seconds** of engine. Deltatime is the duration of the draw frame.

## Callback event details

### onViewLoaded

 * *Property*: static FunctionSubscribe<void()\> **onViewLoaded**

Called when graphic backend canvas is ready to draw.

  ---

### onViewChanged

 * *Property*: static FunctionSubscribe<void()\> **onViewChanged**
 * *Callback*: void()

Called when graphic backend canvas size is changed.

  ---

### onDraw

 * *Property*: static FunctionSubscribe<void()\> **onDraw**
 * *Callback*: void()

Called when graphic backend draw a frame.

  ---

### onUpdate

 * *Property*: static FunctionSubscribe<void()\> **onUpdate**
 * *Callback*: void()

Called in a fixed time based on [updateTime](#updatetime).

!!! note ""

    This update callback is not affected by [fixedTimeSceneUpdate](#fixedtimesceneupdate)

  ---

### onShutdown

 * *Property*: static FunctionSubscribe<void()\> **onShutdown**
 * *Callback*: void()

Called when application is closed.

  ---

### onTouchStart

 * *Property*: static FunctionSubscribe<void(int,float,float)\> **onTouchStart**
 * *Callback*: void(int pointer, float x, float y)
    * **pointer** - For multitouch reference
    * **x** - Position in canvas
    * **y** - Position in canvas

Called when touch starts.

  ---

### onTouchEnd

 * *Property*: static FunctionSubscribe<void(int,float,float)\> **onTouchEnd**
 * *Callback*: void(int pointer, float x, float y)
    * **pointer** - For multitouch reference
    * **x** - Position in canvas
    * **y** - Position in canvas

Called when touch is finished.

   ---

### onTouchMove

 * *Property*: static FunctionSubscribe<void(int,float,float)\> **onTouchMove**
 * *Callback*: void(int pointer, float x, float y)
    * **pointer** - For multitouch reference
    * **x** - Position in canvas
    * **y** - Position in canvas

Called when touch is moved.

   ---

### onTouchCancel

 * *Property*: static FunctionSubscribe<void()\> **onTouchCancel**
 * *Callback*: void()

Called when touch movement is cancelled by system.

   ---

### onMouseDown

 * *Property*: static FunctionSubscribe<void(int,float,float,int)\> **onMouseDown**
 * *Callback*: void(int button, float x, float y, int mods)
     * **button** - Mouse button reference
    * **x** - Position in canvas
    * **y** - Position in canvas
    * **mods** - Modifier based on [Input](input.md)

Called when one of mouse buttons is down.

   ---

### onMouseUp

 * *Property*: static FunctionSubscribe<void(int,float,float,int)\> **onMouseUp**
 * *Callback*: void(int button, float x, float y, int mods)
    * **button** - Mouse button reference
    * **x** - Position in canvas
    * **y** - Position in canvas
    * **mods** - Modifier based on [Input](input.md)

Called when one of mouse buttons is up.

   ---

### onMouseMove

 * *Property*: static FunctionSubscribe<void(float,float,int)\> **onMouseMove**
 * *Callback*: void(float x, float y, int mods)
    * **x** - Position in canvas
    * **y** - Position in canvas
    * **mods** - Modifier based on [Input](input.md)

Called when one of mouse buttons is moving. If [allowEventsOutCanvas](#alloweventsoutcanvas) is true this event is also called if mouse is outside canvas.

   ---

### onMouseScroll

 * *Property*: static FunctionSubscribe<void(float,float,int)\> **onMouseScroll**
 * *Callback*: void(float xoffset, float yoffset, int mods)
    * **xoffset** - Scroll x position
    * **yoffset** - Scroll y position
    * **mods** - Modifier based on [Input](input.md)

Called when mouse scroll is changed.

   ---

### onMouseEnter

 * *Property*: static FunctionSubscribe<void()\> **onMouseEnter**
 * *Callback*: void()

Called when mouse pointer enter in canvas boundary.

   ---

### onMouseLeave

 * *Property*: static FunctionSubscribe<void()\> **onMouseLeave**
 * *Callback*: void()

Called when mouse pointer leave in canvas boundary.

   ---

### onKeyDown

 * *Property*: static FunctionSubscribe<void(int,float,float)\> **onKeyDown**
 * *Callback*: void(int key, bool repeat, int mods)
    * **xoffset** - Scroll x position
    * **yoffset** - Scroll y position
    * **mods** - Modifier based on [Input](input.md)

Called when any keyboard key is down.

   ---

### onKeyUp

 * *Property*: static FunctionSubscribe<void(int,float,float)\> **onKeyUp**
 * *Callback*: void(int key, bool repeat, int mods)
    * **key** - Key code based on [Input](input.md)
    * **repeat** - True if key is keep pressed
    * **mods** - Modifier based on [Input](input.md)

Called when any keyboard key is up.

   ---

### onCharInput

 * *Property*: static FunctionSubscribe<void(wchar_t)\> **onCharInput**
 * *Callback*: void(wchar_t codepoint)
    * **codepoint** - Codepoint of inserted char

Called when any keyboard key is down, but it sends char information. For example, combination keys can be used to generate accented chars.

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


## Property details


### scalingMode

Change scaling mode of screen depending of device resolution. Details in tutorial [Screen Scaling](../learning/screen-scaling.md)

* *Setter*: static void **setScalingMode**([Scaling](#scaling) scalingMode) 
* *Getter*: static [Scaling](#scaling) **getScalingMode**() 

 ---

### textureStrategy

Change texture strategy to resize non power-of-two textures.

* *Setter*: static void **setTextureStrategy**([TextureStrategy](#texturestrategy) textureStrategy)
* *Getter*: static [TextureStrategy](#texturestrategy) **getTextureStrategy()**

 ---

### callMouseInTouchEvent

Call mouse events if touch events is called.

* *Setter*: static void **setCallMouseInTouchEvent**(bool callMouseInTouchEvent)
* *Getter*: static bool **isCallMouseInTouchEvent**()

 ---

### callTouchInMouseEvent

Call touch events if mouse events is called.

* *Setter*: static void **setCallTouchInMouseEvent**(bool callTouchInMouseEvent)
* *Getter*: static bool **isCallTouchInMouseEvent**()

 ---

### useDegrees

Uses degress as default of engine angles. If not it uses radian.

* *Setter*: static void **setUseDegrees**(bool useDegrees)
* *Getter*: static bool **isUseDegrees**()

 ---

### automaticTransparency

Set automatic transparency detection in all objects. It doesn't affect transparency itself, just detection to sort transparent objects in scene, for example.

* *Setter*: static void **setAutomaticTransparency**(bool automaticTransparency)
* *Getter*: static bool **isAutomaticTransparency**()

## Methods details

### setScene

Set main scene of project.

 * static void **setScene**(Scene* scene)

 ---

### getScene

Get main scene of project.

 * static Scene\* **getScene**()

 ---

### addSceneLayer

Added a scene to stay one layer below main scene. Could be used in a GUI scene.

 * static void **addSceneLayer**(Scene\* scene)


 ---

### getCanvasWidth

Get canvas width. This value can be affected by screen scaling mode.

 * static int **getCanvasWidth**()

 ---

### getCanvasHeight

Get canvas height. This value can be affected by screen scaling mode.

 * static int **getCanvasHeight**()

 ---

### setCanvasSize

Set prefered canvas size for screen. The values setted could be affected by scaling mode. Original setted value can get by ```getPreferedCanvasWidth``` and ```getPreferedCanvasHeight```

 * static void **setCanvasSize**(int canvasWidth, int canvasHeight)

 ---

### getPreferedCanvasWidth

Get canvas width that is not modified by screen scaling setup. Prefered canvas is the same value setted in engine.

 * static int **getPreferedCanvasWidth**()

 ---

### getPreferedCanvasHeight

Get canvas height that is not modified by screen scaling setup. Prefered canvas is the same value setted in engine.

 * static int **getPreferedCanvasHeight**()

  ---

### getViewRect

Get viewport sizes calculaded based on *canvas size*, *screen size* and *scaling mode*.

 * static Rect **getViewRect**()
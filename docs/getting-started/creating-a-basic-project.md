In this example we will create a simple triangle. The same sample code can be used in any platform.

## File organization tree

 - :open_file_folder: engine
    * :file_folder: core
    * :file_folder: libs
    * :file_folder: renders
    * :file_folder: shaders
 - :open_file_folder: platform
    * :file_folder: android
    * :file_folder: apple
    * :file_folder: emscripten
    * :file_folder: glfw
    * :file_folder: sokol
 - :open_file_folder: **project** `(your project here)`
    * :file_folder: assets
    * :open_file_folder: lua
        + :octicons-file-code-16: **main.lua**
    + :octicons-file-code-16: **main.cpp**
 - :open_file_folder: tools
    * :file_folder: bin
    * :file_folder: binshaders
    * :file_folder: shaderlib
 - :open_file_folder: workspaces
    * :file_folder: androidstudio
    * :file_folder: xcode

## 1. Using C++

In Supernova file tree there is a ```main.cpp``` file located in ```project/``` folder. This file is used to start the game development in C++. As you can see, there is a call for ```supernova.h```, that will call ```init()``` function when game started.

Edit it with the code:

``` c++
#include "Supernova.h"
using namespace Supernova;

#include "Polygon.h"

Scene scene;
Polygon triangle(&scene);

void init(){
    triangle.addVertex(0, -100);
    triangle.addVertex(-50, 50);
    triangle.addVertex(50, 50);

    triangle.setPosition(Vector3(300,300,0));
    triangle.setColor(0.6, 0.2, 0.6, 1);

    Engine::setCanvasSize(1000,480);
    Engine::setScene(&scene);
}
```

## 2. Using Lua

In Supernova file tree there is a ```main.lua``` file located in ```assets/lua/``` folder. This file is used to start the game development in Lua. You can call any other Lua files by this.

Edit it with the code:

``` lua
scene = Scene()
triangle = Polygon(scene)

triangle:addVertex(0, -100)
triangle:addVertex(-50, 50)
triangle:addVertex(Vector3(50, 50,0))

triangle.position = Vector3(300,300,0)
triangle:setColor(0.6, 0.2, 0.6, 1)

Engine.setCanvasSize(1000,480)
Engine.setScene(scene)
```

Now you can **run** to see the result.

!!! warning
    If you have both Lua and C++ calling Supernova static method ```setScene()```, the last call will be from C++, so Lua code will not work. Use ```NO_CPP_INIT``` or ```NO_LUA_INIT``` macro to avoid init to be called.
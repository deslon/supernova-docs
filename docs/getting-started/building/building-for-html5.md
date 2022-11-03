## For all platforms

### 1. Clone Supernova project

```git clone https://github.com/supernovaengine/supernova.git```

### 2. Download and install Emscripten

[Download](https://emscripten.org/docs/getting_started/downloads.html) Emscripten and follow install [instructions](https://emscripten.org/docs/getting_started/downloads.html#installation-instructions-using-the-emsdk-recommended).

### 3. Compile Supernova

#### For Linux and OSX:

Add Emscripten root path to a system environment variable:

```export $EMSCRIPTEN=<path_to_emscripten>```

#### For Windows:

Download and install [MinGW](https://sourceforge.net/projects/mingw-w64/) and [CMake](https://cmake.org/download/).

!!! note
    MinGW and CMake must be in PATH environment variable of Windows. To test it, try to run ```mingw32-make``` and ```cmake``` in Prompt.

#### For all platforms

The directory where you clone Supernova go to: ```workspaces/emscripten/``` execute in terminal:

```
python3 supernova.py --build --platform web
```

When finished you can see generated **```.js```** and **```.html```** files in ```build/web``` folder. Open with any browser.

!!! warning

    Open ```.html``` locally can result some Javascript errors. You can use command ```python3 -m http.server``` to deploy a simple HTTP server and open in browser ```http://127.0.0.1:8000```.
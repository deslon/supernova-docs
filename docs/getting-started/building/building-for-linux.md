### 1. Clone Supernova repo

```git clone https://github.com/supernovaengine/supernova.git```

### 2. Install dependencies

* libglfw3-dev
* libxi-dev
* libxcursor-dev
* libgl1-mesa-dev
* ninja-build cmake

### 3. Build for Linux
#### a. Using build tool

In ```tools``` directory:

```
python3 supernova.py --build --platform linux
```

#### b. Using CMake

In Supernova root directory:

```
mkdir build
```
```
mkdir instdir
```
```
cmake \
-S . \
-B build \
-DCMAKE_BUILD_TYPE=${{env.BUILD_TYPE}} \
-G "${{ matrix.config.generators }}" \
-DCMAKE_INSTALL_PREFIX:PATH=instdir
```
### 1. Clone Supernova repo

```git clone https://github.com/supernovaengine/supernova.git```

### 2. Install dependencies

* cmake
* ninja

### 3. Build for Windows
#### a. Using build tool

In ```tools``` directory:

```
python3 supernova.py --build --platform macos
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
-DCMAKE_BUILD_TYPE=Debug \
-G "Ninja" \
-DCMAKE_INSTALL_PREFIX:PATH=instdir
```
```
cmake --build build --config Debug --target supernova-project
```
```
cmake --install build --config Debug --strip
```
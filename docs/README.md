Dear ImGui
=====

### About
This repository aims to integrate imgui with cmake, turning possible to
integrate it with existing cmake projects.

[Original ImGui repository link](https://github.com/ocornut/imgui/)

[See online examples with live code](https://pthom.github.io/imgui_explorer/)

### Include in your CMake
```
set(IMGUI_VERSION master)

# dependency: raylib
FetchContent_Declare(
  raylib
  GIT_REPOSITORY https://github.com/natancamargo/imgui
  GIT_TAG ${IMGUI_VERSION}
  GIT_SHALLOW TRUE
)
FetchContent_MakeAvailable(imgui)
...
target_link_libraries(${YOUR_LIBRARY_NAME} PUBLIC
  imgui
)
```

### Build
```shell
cmake -DCXX=g++ -S . -B ./build -G "Ninja"
cmake --build build
```

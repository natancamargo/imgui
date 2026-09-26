cmake_minimum_required(VERSION 3.5.0)
project(imgui VERSION 1.0.0)

include(FetchContent)

# build type and others
# ---------------------
set(CMAKE_BUILD_TYPE Release)

# generate compile_commands.json
set(CMAKE_EXPORT_COMPILE_COMMANDS ON)

# c standard
# ----------
set(CMAKE_CXX_STANDARD          17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS        OFF)

# compile options
# ---------------
if(CMAKE_CXX_COMPILER_ID MATCHES "GNU")
  add_compile_options(
    -Wall
    -Wno-enum-compare
    -Wno-error=maybe-uninitialized
  )
elseif(CMAKE_CXX_COMPILER_ID MATCHES "MSVC")
  add_compile_options(/W4)
endif()

# target library
# --------------
# light weight (not including demo)
set(LIBRARY_NAME imgui-light)
add_library(${LIBRARY_NAME} STATIC
  "${CMAKE_SOURCE_DIR}/imconfig.h"
  "${CMAKE_SOURCE_DIR}/imgui.cpp"
  "${CMAKE_SOURCE_DIR}/imgui.h"
  "${CMAKE_SOURCE_DIR}/imgui_draw.cpp"
  "${CMAKE_SOURCE_DIR}/imgui_internal.h"
  "${CMAKE_SOURCE_DIR}/imgui_tables.cpp"
  "${CMAKE_SOURCE_DIR}/imgui_widgets.cpp"
  "${CMAKE_SOURCE_DIR}/imstb_rectpack.h"
  "${CMAKE_SOURCE_DIR}/imstb_textedit.h"
  "${CMAKE_SOURCE_DIR}/imstb_truetype.h"
)

set(LIBRARY_NAME imgui)
add_library(${LIBRARY_NAME} STATIC
  "${CMAKE_SOURCE_DIR}/imconfig.h"
  "${CMAKE_SOURCE_DIR}/imgui.cpp"
  "${CMAKE_SOURCE_DIR}/imgui.h"
  "${CMAKE_SOURCE_DIR}/imgui_demo.cpp"
  "${CMAKE_SOURCE_DIR}/imgui_draw.cpp"
  "${CMAKE_SOURCE_DIR}/imgui_internal.h"
  "${CMAKE_SOURCE_DIR}/imgui_tables.cpp"
  "${CMAKE_SOURCE_DIR}/imgui_widgets.cpp"
  "${CMAKE_SOURCE_DIR}/imstb_rectpack.h"
  "${CMAKE_SOURCE_DIR}/imstb_textedit.h"
  "${CMAKE_SOURCE_DIR}/imstb_truetype.h"
)

target_include_directories(${LIBRARY_NAME} PUBLIC "${CMAKE_SOURCE_DIR}/")
target_include_directories(${LIBRARY_NAME} PUBLIC "${CMAKE_SOURCE_DIR}/backends")

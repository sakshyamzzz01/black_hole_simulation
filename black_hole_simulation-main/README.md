# Black Hole Simulation — Project Summary & Setup Guide

## (you can skip this)
I was just surfing in youtube and I got recommended by a video by kavan called "simulating blackhole in c++".
And as a second semester student I got so highly motivated that I decided to build it as my semester project.
I dont know how many times I watched the video by kavan(He is the goat).
And finally after nearly 3 months in a midnight, it was completed.
I did the mistake to remember every code syntax and functions. Then after some weeks of boring diary writing and remembering i found out that "apparently there are broiler plates for alot of chunks of codes where we can just copy the code and manipulate it for what we want."

## Controls
- **Left Mouse Click + Drag**: Orbit the camera around the black hole.
- **Scroll Wheel**: Zoom in and out.
- **G Key**: Toggle N-body gravity on/off.
- **Right Mouse Button (Hold)**: Enable gravity while held.

## Files in the workspace
Tracked source files:
- black_hole.cpp — 3D black hole raytracer (OpenGL 4.3 compute shader)
- 2D_lensing.cpp — 2D Schwarzschild geodesic lensing demo
- ray_tracing.cpp — additional ray tracing source
- CPU-geodesic.cpp — CPU-side geodesic reference
- geodesic.comp — compute shader used by black_hole.cpp
- grid.vert & grid.frag — vertex/fragment shaders for the spacetime grid
- CMakeLists.txt — CMake build configuration
- vcpkg.json — vcpkg manifest (glew, glfw3, glm)
- vcpkg-configuration.json — vcpkg registry config

## Environment used
- Microsoft Visual Studio Community 2026 (18.9.2)
- MSVC 19.51 / Windows SDK 10.0.26100.0
- CMake 4.4
- vcpkg(glew, glfw3, glm installed for `x64-windows`)

## How to build and run from a clean state

### 1. Prerequisites
- Visual Studio IDE 2022/2026 with C++ workload and Windows SDK
- CMake
- vcpkg with these packages installed for `x64-windows`:
  
  glew
  glfw3
  glm
 
  If using a standalone vcpkg, note its path (e.g. `C:\Users\sakshyam\path_to\vcpkg`).
  They may require manifestation, prepare a manifest file called vcpkg.json.

### 2. Configure
Open PowerShell in the repo root and run:
powershell:
cmake -S C:\black_hole_simulation -B C:\black_hole_simulation\out\build\x64-Debug -DCMAKE_TOOLCHAIN_FILE=C:\your\path\to\vcpkg\scripts\buildsystems\vcpkg.cmake

If your vcpkg is elsewhere, replace the toolchain path accordingly.
If CMake ever complains about a stale cache, delete `out/build/x64-Debug` and rerun the configure command.

### 3. Build
powershell:
cmake --build C:\black_hole_simulation\out\build\x64-Debug --config Debug


### 4. Run
powershell:
# 3D black hole
C:\black_hole_simulation\out\build\x64-Debug\Debug\BlackHole3D.exe

# 2D geodesic lensing demo
C:\black_hole_simulation\out\build\x64-Debug\Debug\BlackHole2D.exe

### How to run in Visual Studio
1. Open Visual Studio and select **Open a local folder**, then choose the project directory.
2. Wait for CMake to configure the project automatically. (Ensure your vcpkg toolchain path is configured in `CMakeSettings.json` or CMake presets if necessary).
3. In the toolbar, click the **Select Startup Item** dropdown and choose `BlackHole3D.exe` or `BlackHole2D.exe`.
4. Press **F5** or click the green **Start** button to build and run.

### How to run in Antigravity IDE
1. Open the project folder in Antigravity IDE.
2. You can open a new terminal (Ctrl+`) and run the CMake configure and build commands listed above.
3. Alternatively, simply ask the Antigravity assistant: "Build and run the 3D black hole simulation" and it will handle the environment setup and execution for you!
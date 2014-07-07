ParticleSimulator
=================

A particle simulator written with C++ SFML OpenGL. 

*The website is out of date and needs updating, I will get to that shortly:*
**Read more about this project at http://syntaf.github.io/ParticleSimulator/**

![gif](http://i.imgur.com/ihMnqs3.gif)

Or see the full video here: https://vimeo.com/98855736  (**Password:** particles)

**Required Libraries**
--------------------------------------------------------

| Library        | Minimum Version | Architecture |Header Only  |
| -------------  |:-------------:  | :---------:  |-----:       |
| GLM            | 0.9.5.3         | N/A          |  Yes        |
| GLEW           | 1.5.3           | x64          |  No         |
| SFML           | 2.1             | x64          |  No         |

[**GLM**](http://glm.g-truc.net/0.9.5/index.html):  A header only C++ mathematics library for graphics software based on the OpenGL Shading Language (GLSL) specification and released under the MIT license.

[**GLEW**](http://glew.sourceforge.net/):   A cross-platform open-source C/C++ extension loading library. GLEW provides efficient run-time mechanisms for determining which OpenGL extensions are supported on the target platform. OpenGL core and extension functionality is exposed in a single header file. GLEW has been tested on a variety of operating systems, including Windows, Linux, Mac OS X, FreeBSD, Irix, and Solaris.
  
[**SFML**](http://www.sfml-dev.org/):   SFML provides a simple interface to the various components of your PC, to ease the development of games and multimedia applications.

**Compiler Support**
--------------------------------------------------------

|  Compilers  |  Recommended Version  |  Minimum Version  |
| ----------- | --------------------- | ----------------- |
| MSVC | `v110` |  `v100` |
| GNU Compiler Collection(G++) | `?` | `?` |
| Clang | `?` | `?` |

| Build System | Recommended Version | Minimum Version |
|--------------|---------------------|-----------------|
| CMake | `2.8.4` | `2.8.4` |


Build
-----------------
Before beginning to build this application, make sure you have downloaded the prerequisites above.

Windows
--------
1. Clone the master Particle Simulator repository in a directory of your choice.

2. Create a build folder. This project requires and out-of-tree-build. This means you ~~will be unable to~~ **should not** run CMake in the Particle Simulator folder

3. Open up the CMake GUI. In the input box labelled "Where is the source code:", enter the full path to the source folder. In the input box labelled "Where to build the binaries:", enter the full path to the build folder you created in step 2

4. Add CMake variable definitions, you will need three to configure and generate the project. They are:
    * `SFML_ROOT` - The root folder of SFML (e.g. *c:/local/sfml-2.1*)
    * `GLM_ROOT` - The root folder of GLM (e.g. *c:/local/glm*)
    * `GLEW_ROOT` - The root folder of GLEW (e.g. *c:/loacl/glew*)
    * CMake will search for glew libraries in {GLEW_ROOT}/lib/release/x64 `{GLEW_ROOT}/lib/Release/x64/glew32.lib`, to change this path edit line `53` in `CMakeLists.txt`
    * `USE_OPENCL` - Currently an unfinished experimental implementation with OpenCL, default `false` is it is unfinished

5. Press the "Configure" button. A window will pop up asking you which compiler to use. Select your x64 version of your preferred compiler. Note that it is possible to build x32 without running into any errors, feel to modify your build to build x86 if you wish.

6. If the "Generate" button is not clickable, press "Configure" again. Repeat this step until the "Generate" button becomes clickable.

7. Press "Generate".

8. Open up the build folder, and double-click ParticleSimulator.sln

9. Build the particle simulator target, **only** build in debug if you *actually* want to debug something; without optimizations the simulator will run extremely slow. CMake copies the source files shaders to the executable directory, in this case you will find the shaders and textures in `{BINARY_DIR}/Release/`. Running in debug will require you to copy these files to the Debug directory, I am working on a fix that will place all executables into the same Release directory.

10. copy the required DLL's into your Debug/Release folder, these would be
    * `sfml-graphics-2.dll`
    * `sfml-system-2.dll`
    * `sfml-window-2.dll`
    * `glew32.dll`
    * for Debug mode make sure to use the debug SFML DLLS, the one's with a trailing `-d`. Previous versions of SFML do not have the `2` either as listed here.

Linux
------
*support coming soon*

OS X (Mac)
----------
*support coming soon*

To-Do
-------------------
- [x] Begin GUI development
- [ ] Optimize particle container(chunking)
- [x] Provide a CMake build system
- [ ] Implement highly customizable enviroment
- [ ] Move particle calculations to GPU

Additional Notes
-------------------------
- Intel HD 4000 graphics cards currently have issues running ModernGL, however this should not inhibit the simulator from running
- A thanks to opengl-tutorial.org for code structure and teachings

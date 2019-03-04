# Dependancies

You have to install CMake and Git.
Other libraries will be installed automatically.
- CMake, [Install it your self](https://cmake.org/download/)
- Git, [Install it your self](https://git-scm.com/downloads)
- {[glfw](https://github.com/glfw/glfw.git) | [glut](https://github.com/dcnieho/FreeGLUT.git)}, Windowing library (You can use it either of one)
- [glad](https://github.com/Dav1dde/glad.git), OpenGL function loading library
- [glm](https://github.com/g-truc/glm.git), Math library for OpenGL and GLSL shader
- [tinyobjloader](https://github.com/syoyo/tinyobjloader.git), Minimal Wavefront .obj file loading library


# Installation

Use git recursive clone to download the template.

Clone entire branch

If you want to change the branch see [here](#change-the-repository-branch)


If you changed your branch and you are suffering build error see [here](#submodule-init-and-update)
```sh
git clone --recursive https://github.com/sleepyeye/glSkeleton.git
```

Clone master branch only. (Implemented with glfw)


```sh
git clone --recursive -b master --single-branch https://github.com/sleepyeye/glSkeleton.git
```


Clone freeglut branch only. (Implemented with freeglut)


```sh
git clone --recursive -b freeglut --single-branch https://github.com/sleepyeye/glSkeleton.git
```




# Build

Two step build process.

1. Generate the project

You need to re-run cmake command whenever you add more source files (\*.h, \*.cpp)
See more deatil about this at [here](#add-more-source-files).
```sh
mkdir build
cd build
cmake ..
```

2. Build the project

For *windows* user
  1. Go to build folder
  2. Open *glSkeleton.sln* file
  3. Make *glSkeleton* as startup proejct and build it.


For *linux* user
```sh
cd build
make
```


After the build process you will get directory structure like this.
```
.
├── build 
│   ├── CMakeFiles
│   ├── bin                                                # you can find your executable here
│   ├── extern
│   ├── lib                                                # you can find your static libraries
│   └── src
├── extern                                                 # external projects
│   ├── CMakeLists.txt                                     # DO NOT TOUCH THIS
│   ├── freeglut
│   ├── glad
│   ├── glm
│   └── tinyobjloader
└── src                                                    # your source code
    └── CMakeLists.txt
└── CMakeLists.txt                                           # in this file 
12 directories
```



# How to

## Add more source files

If you want to add more sources to build your executable, see following instruction

1. Open the *CMakeLists.txt* in src folder
2. Add your sources (headers(*.h) or sources(*.cpp))

```cmake
add_executable(glskeleton
  main.cpp
  ...
  your_source_file.h
  your_source_file.cpp
  ...
  )
```

3. Rerun cmake (See [here](#build) for details)

## Change the project name

1. Open the *CMakeLists.txt* in project root
2. Change the string in project function

```cmake
project(glskeleton)                                          # Change this
```

## Change the executable name


1. Open the *CMakeLists.txt* in src folder
2. Change the *glskeleton* to 

```cmake
add_executable(glskeleton                                   # Change this word
  main.cpp
  ...
  )
```


## Change the repository branch

```sh
git checkout master                                         # from master to freeglut
git checkout freeglut                                       # from freeglut to master
```

## Submodule init and update

This repository only has two branches(master and glut)
Two branch use different submodule.
You should initalize the submodule if you changed the branch. You only need to this once when you first checkout your branch.
```sh
git submodule init
git submodule update
```



# Scope

This project template does not cover features in below
- GLSL shader,
- OpenGL (3.x >) APIs
- Texture loading

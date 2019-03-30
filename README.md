[![Project Status: Active – The project has reached a stable, usable state and is being actively developed.](http://www.repostatus.org/badges/latest/active.svg)](http://www.repostatus.org/#active)
[![Build Status](https://travis-ci.com/stelro/cpp-boilerplate.svg?branch=master)](https://travis-ci.org/stelro/cpp-boilerplate)
[![Codacy Badge](https://api.codacy.com/project/badge/Grade/bf7a73f977ab49a7845f0a4a1ff5a3fb)](https://app.codacy.com/app/stelro/cpp-boilerplate?utm_source=github.com&utm_medium=referral&utm_content=stelro/cpp-boilerplate&utm_campaign=Badge_Grade_Dashboard)
[![license](https://img.shields.io/badge/license-Unlicense-blue.svg)](https://github.com/stelro/cpp-boilerplate/blob/master/LICENSE)
# Boiler plate for C++ projects 

This is a boiler plate C++ project. Inspired by [bsamseth](https://github.com/bsamseth/cpp-project) and [Jason Turner](https://github.com/lefticus/cpp_starter_project)

## Structure
``` text
.
├── CMakeLists.txt
├── app
│   └── main.cpp
├── include
│   ├── example.h
│   └── exampleConfig.h.in
├── src
│   └── example.cpp
└── tests
    ├── dummy.cpp
    └── main.cpp
```

Sources go in [src/](src/), header files in [include/](include/), main programs in [app/](app), and
tests go in [tests/](tests/) (compiled to `unit_tests.x` by default). 

If you add a new executable, say `app/hello.cpp`, you only need to add the following two lines to [CMakeLists.txt](CMakeLists.txt): 

``` cmake
add_executable(main.x app/main.cpp)   # Name of exec. and location of file.
target_link_libraries(main.x PRIVATE engine)  # Link the executable to `engine` (if it uses it).
                                              # `engine` is the default name of the library built from src/*.cpp
```

You can find the example source code that builds the `main.x` executable in [app/main.cpp](app/main.cpp) under the `Build` section in [CMakeLists.txt](CMakeLists.txt). 
If the executable you made does not use the library in [src/](src), then only the first line is needed.

## Building
Build by making a build directory (i.e. `build/`), run `cmake` in that dir, and then use `make` to build the desired target.

Example:

``` bash
> mkdir build && cd build
> cmake .. -DCMAKE_BUILD_TYPE=[Debug | Release]
> make
> ./main.x
> make catch     # Makes and runs the tests.
> make doc       # Generate html documentation.
```

## .gitignore
The [.gitignore](.gitignore) file is a copy of the [Github C++.gitignore file](https://github.com/github/gitignore/blob/master/C%2B%2B.gitignore),
with the addition of ignoring the build directory (`build/`).

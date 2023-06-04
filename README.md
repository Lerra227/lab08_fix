## Laboratory work VI


## Homework

```sh
lera@Lerra:~/lab08$ sudo docker build -t logger .
```
<!--[+] Building 6.0s (14/14) FINISHED
 => [internal] load .dockerignore                                                                                  0.0s
 => => transferring context: 2B                                                                                    0.0s
 => [internal] load build definition from Dockerfile                                                               0.0s
 => => transferring dockerfile: 386B                                                                               0.0s
 => [internal] load metadata for docker.io/library/ubuntu:18.04                                                    1.3s
 => [1/9] FROM docker.io/library/ubuntu:18.04@sha256:152dc042452c496007f07ca9127571cb9c29697f42acbfad72324b2bb2e4  0.0s
 => [internal] load build context                                                                                  0.0s
 => => transferring context: 10.60kB                                                                               0.0s
 => CACHED [2/9] RUN apt update                                                                                    0.0s
 => CACHED [3/9] RUN apt install -yy gcc g++ cmake                                                                 0.0s
 => [4/9] COPY . print/                                                                                            0.1s
 => [5/9] WORKDIR print                                                                                            0.0s
 => [6/9] RUN cmake -H. -B_build -DCMAKE_BUILD_TYPE=Release -DCMAKE_INSTALL_PREFIX=_install                        2.2s
 => [7/9] RUN cmake --build _build                                                                                 1.5s
 => [8/9] RUN cmake --build _build --target install                                                                0.6s
 => [9/9] WORKDIR /print/_install/bin                                                                              0.0s
 => exporting to image                                                                                             0.1s
 => => exporting layers                                                                                            0.1s
 => => writing image sha256:5fc76752de8ef66b18b492a6e987fac6116bb10739a0edf7563e4ea901c58caf                       0.0s
 => => naming to docker.io/library/logger                                                                          0.0s
-->
```sh
lera@Lerra:~/lab08$ docker images
REPOSITORY   TAG       IMAGE ID       CREATED              SIZE
logger       latest    5fc76752de8e   About a minute ago   334MB
<none>       <none>    4b35a9f879b0   25 hours ago         334MB
lera@Lerra:~/lab08$ sudo docker run -it -v "$(pwd)/logs/:/home/logs/" logger
text1
text2
text3
lera@Lerra:~/lab08$ docker inspect logger
```
<!--[
    {
        "Id": "sha256:5fc76752de8ef66b18b492a6e987fac6116bb10739a0edf7563e4ea901c58caf",
        "RepoTags": [
            "logger:latest"
        ],
        "RepoDigests": [],
        "Parent": "",
        "Comment": "buildkit.dockerfile.v0",
        "Created": "2023-06-04T13:38:50.865882347+03:00",
        "Container": "",
        "ContainerConfig": {
            "Hostname": "",
            "Domainname": "",
            "User": "",
            "AttachStdin": false,
            "AttachStdout": false,
            "AttachStderr": false,
            "Tty": false,
            "OpenStdin": false,
            "StdinOnce": false,
            "Env": null,
            "Cmd": null,
            "Image": "",
            "Volumes": null,
            "WorkingDir": "",
            "Entrypoint": null,
            "OnBuild": null,
            "Labels": null
        },
        "DockerVersion": "",
        "Author": "",
        "Config": {
            "Hostname": "",
            "Domainname": "",
            "User": "",
            "AttachStdin": false,
            "AttachStdout": false,
            "AttachStderr": false,
            "Tty": false,
            "OpenStdin": false,
            "StdinOnce": false,
            "Env": [
                "PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin",
                "LOG_PATH=/home/logs/log.txt"
            ],
            "Cmd": null,
            "Image": "",
            "Volumes": {
                "/home/logs": {}
            },
            "WorkingDir": "/print/_install/bin",
            "Entrypoint": [
                "/bin/sh",
                "-c",
                "./demo"
            ],
            "OnBuild": null,
            "Labels": {
                "org.opencontainers.image.ref.name": "ubuntu",
                "org.opencontainers.image.version": "18.04"
            }
        },
        "Architecture": "amd64",
        "Os": "linux",
        "Size": 333834105,
        "VirtualSize": 333834105,
        "GraphDriver": {
            "Data": {
                "LowerDir": "/var/lib/docker/overlay2/cpc5cbsiayk32wqn5g67ug4mw/diff:/var/lib/docker/overlay2/sdx7ihyvrufd77qy89gc9bjp7/diff:/var/lib/docker/overlay2/mlud4tz1fh1f2n24t8r9k3zsw/diff:/var/lib/docker/overlay2/f3ndqz75dl223k1acymca2fn5/diff:/var/lib/docker/overlay2/xtbe7846pi1xblqqgopxe9fhi/diff:/var/lib/docker/overlay2/nhp5s9k7y35rzvysleh6khshr/diff:/var/lib/docker/overlay2/iip2ev2noe4sh0d6qqnuer4iu/diff:/var/lib/docker/overlay2/a50cee9edda3be3bf5ac99d588a70bc2ba62538454a313e9399d0afd5f7bbb2d/diff",
                "MergedDir": "/var/lib/docker/overlay2/rwi5oyx1r711vhtn3qgjf9ml9/merged",
                "UpperDir": "/var/lib/docker/overlay2/rwi5oyx1r711vhtn3qgjf9ml9/diff",
                "WorkDir": "/var/lib/docker/overlay2/rwi5oyx1r711vhtn3qgjf9ml9/work"
            },
            "Name": "overlay2"
        },
        "RootFS": {
            "Type": "layers",
            "Layers": [
                "sha256:548a79621a426b4eb077c926eabac5a8620c454fb230640253e1b44dc7dd7562",
                "sha256:81735417d158a38738d3a432ec769032051f3e21225283f154d621389fb58998",
                "sha256:3e5224b6e027bc697d0e7649cdeefa16ad153322c55de809846a36f2fca60a37",
                "sha256:91b4252814bee9711d07a9f82828665a07724a47b2755cc378b4e5076eae3d81",
                "sha256:5f70bf18a086007016e948b04aed3b82103a36bea41755b6cddfaf10ace3c6ef",
                "sha256:1a68d3aff5ed5cc6c3a5caafd350e19650f4d9942231ebbb7f4250d0b86d02a0",
                "sha256:32c18a3fd1a1925d343e02311dc7c7df12ee415741729fe22654c04c43b5794e",
                "sha256:5ac56b1af1f89bca9905cf743adb1469139f982345108c754a0f190e00ec3e09",
                "sha256:5f70bf18a086007016e948b04aed3b82103a36bea41755b6cddfaf10ace3c6ef"
            ]
        },
        "Metadata": {
            "LastTagTime": "2023-06-04T13:38:50.97708113+03:00"
        }
    }
]-->
```sh
lera@Lerra:~/lab08$ cat logs/log.txt
text1
text2
text3
<C-D>
text1
text2
text3
lera@Lerra:~/lab08$ nano logs/log.txt
lera@Lerra:~/lab08$ cat logs/log.txt
text1
text2
text3
```
```sh
lera@Lerra:~/lab06/lab04$ nano CPackConfig.cmake
```
```sh
include(InstallRequiredSystemLibraries)

set(CPACK_PACKAGE_CONTACT donotdisturb@yandex.ru)
set(CPACK_PACKAGE_VERSION_MAJOR ${PRINT_VERSION_MAJOR})
set(CPACK_PACKAGE_VERSION_MINOR ${PRINT_VERSION_MINOR})
set(CPACK_PACKAGE_VERSION_PATCH ${PRINT_VERSION_PATCH})
set(CPACK_PACKAGE_VERSION_TWEAK ${PRINT_VERSION_TWEAK})
set(CPACK_PACKAGE_VERSION ${PRINT_VERSION})

set(CPACK_PACKAGE_DESCRIPTION_SUMMARY "static C++ library for printing")

set(CPACK_RESOURCE_FILE_README \${CMAKE_CURRENT_SOURCE_DIR}/README.md)

set(CPACK_RPM_PACKAGE_NAME "solver")
set(CPACK_RPM_PACKAGE_LICENSE "MIT")
set(CPACK_RPM_PACKAGE_GROUP "print-solver")
set(CPACK_RPM_PACKAGE_VERSION CPACK_PACKAGE_VERSION)

set(CPACK_DEBIAN_PACKAGE_NAME "solver")
set(CPACK_DEBIAN_PACKAGE_PREDEPENDS "cmake >= 3.0")
set(CPACK_DEBIAN_PACKAGE_VERSION CPACK_PACKAGE_VERSION)

include(CPack)
```
```sh
lera@Lerra:~/lab06/lab04$ nano CMakeLists.txt
```
```sh
ccmake_minimum_required(VERSION 3.4)

set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

option(BUILD_EXAMPLES "Build examples" OFF)
option(BUILD_TESTS "Build tests" OFF)

project(print)
set(PRINT_VERSION_MAJOR 0)
set(PRINT_VERSION_MINOR 1)
set(PRINT_VERSION_PATCH 0)
set(PRINT_VERSION_TWEAK 0)
set(PRINT_VERSION
  ${PRINT_VERSION_MAJOR}.${PRINT_VERSION_MINOR}.${PRINT_VERSION_PATCH}.${PRINT_VERSION_TWEAK})
set(PRINT_VERSION_STRING "v${PRINT_VERSION}")

add_library(print STATIC ${CMAKE_CURRENT_SOURCE_DIR}/sources/print.cpp)

target_include_directories(print PUBLIC
  $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/include>
  $<INSTALL_INTERFACE:include>
)

if(BUILD_EXAMPLES)
  file(GLOB EXAMPLE_SOURCES "${CMAKE_CURRENT_SOURCE_DIR}/examples/*.cpp")
  foreach(EXAMPLE_SOURCE ${EXAMPLE_SOURCES})
    get_filename_component(EXAMPLE_NAME ${EXAMPLE_SOURCE} NAME_WE)
    add_executable(${EXAMPLE_NAME} ${EXAMPLE_SOURCE})
    target_link_libraries(${EXAMPLE_NAME} print)
    install(TARGETS ${EXAMPLE_NAME}
      RUNTIME DESTINATION bin
    )
  endforeach(EXAMPLE_SOURCE ${EXAMPLE_SOURCES})
endif()

install(TARGETS print
    EXPORT print-config
    ARCHIVE DESTINATION lib
    LIBRARY DESTINATION lib
)

install(DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}/include/ DESTINATION include)
install(EXPORT print-config DESTINATION cmake)

if(BUILD_TESTS)
    enable_testing()
    file(GLOB ${PROJECT_NAME}_TEST_SOURCES tests/*.cpp)
    add_executable(check ${${PROJECT_NAME}_TEST_SOURCES})
    target_link_libraries(check ${PROJECT_NAME} GTest::main)
    add_test(NAME check COMMAND check)
endif()

add_executable(demo demo/main.cpp)
target_link_libraries(demo print)
install(TARGETS demo RUNTIME DESTINATION bin)

include(CPackConfig.cmake)

```
```sh
lera@Lerra:~/lab06/lab04$ cd .github/workflows
lera@Lerra:~/lab06/lab04/.github/workflows$ nano CI.yml
```

```sh
name: CMake

on:
  push:
    branches: [main]
    tags: -"v*0.*"
  pull_request:
    branches: [main]
    
env:
  BUILD_TYPE: Release

jobs:
  build_Linux:
    runs-on: ubuntu-latest

    steps:
      - uses: actions/checkout@v3

      - name: Configure Solver
        run: cmake -H. -B_build -DCPACK_GENERATOR="TGZ"

      - name: Build Solver
        run: cmake --build _build --target package

      - name: Make Solver Package
        run: cd _build && cpack -G "DEB" &&
             cpack -G "RPM" &&
             mkdir ../artifacts &&
             mv *.tar.gz ../artifacts/ &&
             mv *.deb ../artifacts/ &&
             mv *.rpm ../artifacts/
      - name: Publish
        uses: actions/upload-artifact@v2
        with:
          name: DebRpm
          path: artifacts/
```
```sh 
lera@Lerra:~/lab06/lab04/.github/workflows$ cd ..
lera@Lerra:~/lab06/lab04/.github$ cd ..
lera@Lerra:~/lab06/lab04$ git add -A
lera@Lerra:~/lab08$ git commit -m "last"
[main c9911a7] last
 9 files changed, 118 insertions(+), 21 deletions(-)
 create mode 100644 .github/workflows/Cl.yml
 rewrite CMakeLists.txt (77%)
 create mode 100644 demo/main.cpp
 create mode 100644 include/print.hpp
 create mode 100644 include/print.hpp:Zone.Identifier
 create mode 100644 sources/print.cpp
 create mode 100644 sources/print.cpp:Zone.Identifier
 lera@Lerra:~/lab08$ git remote remove origin
 lera@Lerra:~/lab08$ git remote add origin https://github.com/Lerra227/lab08_fix
 lera@Lerra:~/lab08$ git push origin main
Username for 'https://github.com': Lerra227
Password for 'https://Lerra227@github.com':
Enumerating objects: 299, done.
Counting objects: 100% (299/299), done.
Delta compression using up to 20 threads
Compressing objects: 100% (135/135), done.
Writing objects: 100% (299/299), 107.60 KiB | 53.80 MiB/s, done.
Total 299 (delta 138), reused 277 (delta 135), pack-reused 0
remote: Resolving deltas: 100% (138/138), done.
To https://github.com/Lerra227/lab08_fix
 * [new branch]      main -> main
```
```
Copyright (c) 2015-2021 The ISC Authors
```

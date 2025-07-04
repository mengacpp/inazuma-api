# InazumaQuery

> [!CAUTION]
> This library it's still in early development phase (pre-alpha). Bugs have to be expected even during the installation phase.

A C API for querying and comparing Inazuma Eleven player stats.

## Table of contents

- [InazumaQuery](#inazumaquery)
  - [Table of contents](#table-of-contents)
  - [Features](#features)
  - [Getting started](#getting-started)
  - [Supported platform](#supported-platform)
  - [Dependencies](#dependencies)
  - [Installation](#installation)
  - [Credits](#credits)

## Features

**Currently available features:**

- Open the **Inazuma Eleven 1, 2, and 3 player databases** by default, or import your own
- **Filter and sort** players to get the ones you are looking for
- **Look for players** using their full name

**Features I’m currently working on and planned features:**

- Create built in compare functions to sort players by 'skills' rather than stats. (e.g. sorting by general ability to shoot rather than by kick statistic).  
- Adding secondary informations about players (team, recruitment method, recruitment location ..., move ids)

**Known bugs:**

- Some nicknames in the IE3 database and stats in the IE1 database (less than 5% I'd say) are subject to small decryption bugs that might influece accuracy
- Some players are duplicates, this is probably caused by the different versions of the same players depending on the game version

## Getting started

Using the API is straight forward: make sure you have all the required [dependencies](#dependencies), and then follow the [installation instructions](#installation).

I've provided some [examples](https://github.com/mengacpp/InazumaQuery/tree/main/examples) on how to use the library and i'll create a small wiki as soon as the API is in a more stable status and the first official version is released.

## Supported platform

Every platform is theroetically supported, as there are no platform specific dependencies, but only MacOS has been tested right now.

> [!IMPORTANT]
> I will create issue templates in the near future so that you can point out bugs you've found.

## Dependencies

The library does not depend on any external libraries. However, to install it on your device you will need the following tools installed on your device:

- Git
- CMake
- Python (required only for a fast installation)

## Installation

You can use CMake to build and install InazumaQuery on your device. **The process is the same on every platform**.

1. **Clone the repostory on your device**

    You can clone this repostory on your device using git:

    ```terminal
    git clone https://github.com/mengacpp/InazumaQuery.git
    ```

2. **Test the project**

    If you want, you can skip this step and install the library right away.

    You can tell cmake to build the tests by setting the `INA_BUILD_TEST` option to `ON`. Run:

    ```terminal
    mkdir build
    cmake -B build -S . -DINA_BUILD_TEST=ON -DCMAKE_BUILD_TYPE=Debug
    ```

    Now, navigate to the `build` directory and run:

    ```terminal
    cmake --build .
    ctest
    ```

    If you don't see any error message, you are good to go. I'd recommend deleting the `build` directory before going to the next step.

3. **Build and install the library on your device**

    Generate the cmake project using the `CMAKE_BUILD_TYPE` option set to `Release`. The library gets build as shared by default, but you can build it as static by setting the `INA_BUILD_SHARED` option to false.

    ```terminal
    cmake -B build -S . -DCMAKE_BUILD_TYPE=Release -DINA_BUILD_SHARED=OFF
    ```

    Now, build and install the library. If you want, you can specify the install directory using the `--prefix` option when running `cmake --install`.

    ```terminal
    cd build
    cmake --build .
    cmake --install InazumaQuery --prefix your_installation_path
    ```

## Credits

- Player stats and data used in this project were sourced from [SwareJonge](https://github.com/SwareJonge)'s comprehensive [Inazuma Eleven databases](https://docs.google.com/spreadsheets/d/1qfanvDyPubSLyfcOMuXN9IbGtr7U1jr-5FRCf2R7FQA/edit?gid=469737450#gid=469737450). Huge thanks to their work!

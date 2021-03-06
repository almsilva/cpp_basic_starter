# cpp_basic_starter

This is my version of the boiler plate code to start a C++ project with the basic settings to:

* Build the project using **cmake** as an *executable*, *static library* or *shared library*.
* Compile the project using **clang**.
* Write unit tests using **Boost.Test** and execute them using **ctest**.

## Getting started

The following steps will give you a copy of the project ready to be used locally for any purpose. This is the most simple boiler plate structure that I could figure out to have a basic C++ project ready to be developed. It won't cover all the use cases.

### Prerequisites

This project was developed and tested using the following components:

| Component | Version | Description                  |
|-----------|---------|------------------------------|
| LLVM      | 3.4     | Compiling infrastructure.    |
| CMake     | 2.8.12  | Build and executing tests.   |
| Boost     | 1.67.0  | Library used for unit tests. |

### Installing

Please, refer to the aforementioned components official documentation to obtain the details about the installation and configuration of each one of them. It is out of the scope of this documentation to walk you through this process.

However, keep in mind that this project uses **Boost.Test** as shared libraries, which means that its libraries must be compiled and installed locally.

### Assumptions

The following assumptions are taken by the project's settings:

* The project adopts the [Semantic Versioning](https://semver.org/).
* All the application source files will be located in the **/src** folder.
* All the public headers will be located in the **/include** folder.
* All the unit test sources will be located in the **/test** folder.
* All the binaries will be generated in the **/build** folder.
* For executable, the main function is located in the **/src/main.cpp** file and this file won't be tested.
* The final artifact name will be **<project_name>-<major_version>.<minor_version>.<patch_version>**.

### Building settings

To change the project's settings, edit the **CMakeLists.txt** file located in the project's root folder. Inside of it, you can find the following parameters to customize the project:

| Parameter | Example | Description |
|-----------|---------|-------------|
| project | sandbox | Project's name. Will be used to compose the final artifact name.|
| PROJECT_TYPE | EXEC | Type of the artifact being generated by the project. Can be: EXEC (executable), STATIC_LIB (static library) or SHARED_LIB (shared library).
| MAJOR_VERSION | 0 | Project's current major version. |
| MINOR_VERSION | 1 | Project's current minor version. |
| PATCH_VERSION | 0 | Project's current patch version. |

Feel free to change the other settings if you know what are you doing.

### Building

From the inside of the **/build** folder, execute the following command:

```bash
cmake ..
```

It will create all the artifacts required to build the project and run the unit tests inside the **/build** folder. To build the project, compiling the sources and the tests into binary artifacts, execute the command:

```bash
make
```

It will generate all the binaries inside the **/build** folder. By default, an executable named *sandbox-0.1.0* and a test named *main_test*.

### Running the tests

Still from the inside of the **/build** folder, execute the following command:

```bash
ctest
```

You must receive the following output:

```bash
Test project /vagrant/cpp_basic_starter/build
    Start 1: main_test
1/1 Test #1: main_test ........................***Failed    0.01 sec

0% tests passed, 1 tests failed out of 1

Total Test time (real) =   0.07 sec

The following tests FAILED:
          1 - main_test (Failed)
Errors while running CTest
```

This is the expected result, once that the **/test/main.cpp** was planned to fail.


## License

This project is licensed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details

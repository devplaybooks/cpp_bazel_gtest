[![Build and Test](https://github.com/devplaybooks/cpp_cmake_gtest/actions/workflows/test.yml/badge.svg)](https://github.com/devplaybooks/cpp_cmake_gtest/actions/workflows/test.yml)
[![Contributor Covenant](https://img.shields.io/badge/Contributor%20Covenant-2.1-4baaaa.svg)](CODE_OF_CONDUCT.md)

# C++ Gtest Bazek Playbook

C++ template for CMake and Google Test with a custom GitHub [Action](https://github.com/features/actions) and
[Codespace](https://github.com/features/codespaces).  

## Usage

```
$❯ cmake -S . -B build
$❯ cmake --build build
$❯ cd build
$❯ make test
$❯ cd ..
```

## Dependencies

* [Bazel](https://bazel.build/)
  * [Bazel Tutorial: Build a C++ Project ](https://bazel.build/start/cpp) 
  * Bazelisk [C++](https://docs.bazel.build/versions/main/tutorial/cpp.html)
* [GoogleTest](https://github.com/google/googletest)
    * [User’s Guide](https://google.github.io/googletest/)

## Resources

* [C++ Core Guidelines](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md)
* GitHub
  * [Codespaces](https://github.com/codespaces)
  * [DevContainers](https://code.visualstudio.com/docs/devcontainers/containers)
    * [C++ Development Container Images](https://mcr.microsoft.com/en-us/product/devcontainers/cpp/about)

### Copilot Babble

The actual path of your library should be specified in the `deps` section of the `cc_test` rule in your `BUILD` file. It typically points to the target defined in another `BUILD` file within your project.

For example, if your library is defined in a `BUILD` file located in the `src` directory, you might have something like this:

```python
cc_library(
    name = "your_library",
    srcs = ["your_library.cpp"],
    hdrs = ["your_library.h"],
)
```

Then, in your `BUILD` file for the tests, you would reference it as follows:

```python
cc_test(
    name = "sample_tests",
    srcs = ["example_test.cpp"],
    deps = [
        "//src:your_library",
        "@gtest//:gtest_main",
    ],
)
```

Make sure to replace `"//src:your_library"` with the actual path and target name of your library.

Bazelisk is a wrapper for Bazel that automatically downloads and installs the appropriate version of Bazel specified for a project. It simplifies managing Bazel versions, ensuring that the correct version is used without manual intervention.

### Key Features:
- **Automatic Version Management**: Bazelisk reads the version from a `.bazelversion` file or environment variables and downloads the specified version if it's not already installed.
- **Compatibility**: Ensures that the project builds with the correct Bazel version, avoiding issues caused by version mismatches.
- **Ease of Use**: Acts as a drop-in replacement for the `bazel` command, making it easy to integrate into existing workflows.

### Installation:
You can install Bazelisk using various methods, such as Homebrew on macOS:

```sh
brew install bazelisk
```

### Usage:
Once installed, you can use `bazelisk` just like `bazel`:

```sh
bazelisk build //...
```

### Configuration:
Create a `.bazelversion` file in your project root to specify the Bazel version:

```sh
echo "4.2.1" > .bazelversion
```

Bazelisk will ensure that this version of Bazel is used for all commands run in the project.
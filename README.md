[![Github releases](https://img.shields.io/github/release/Neargye/semver.svg)](https://github.com/Neargye/semver/releases)
[![Vcpkg package](https://img.shields.io/badge/Vcpkg-package-blueviolet)](https://github.com/microsoft/vcpkg/tree/master/ports/neargye-semver)
[![Conan package](https://img.shields.io/badge/Conan-package-blueviolet)](https://conan.io/center/recipes/neargye-semver)
[![License](https://img.shields.io/github/license/Neargye/semver.svg)](LICENSE)

C++ library compare and manipulate versions are available as extensions to the `<major>.<minor>.<patch>-<prerelease_tag>+<build_metadata>` format complying with [Semantic Versioning 2.0.0](https://semver.org)

## [Features & Examples](https://github.com/Neargye/semver/blob/master/example/)

* Parse

  ```cpp
  semver::version v1;
  if (semver::parse("1.4.3", v1)) {
    const int patch = v1.patch(); // 3
    // do something...
  }

  semver::version v2;
  if (semver::parse("1.2.4-alpha.10")) {
    const std::string prerelease_tag = v2.prerelease_tag() // alpha.10
    // do something...
  }
  ```

* Сomparison

  ```cpp
  assert(v1 != v2);
  assert(v1 > v2);
  assert(v1 >= v2);
  assert(v2 < v1);
  assert(v2 <= v1);
  ```

* Validate

  ```cpp
  const bool result = semver::valid("1.2.3-alpha+build");
  assert(result);
  ```

* Range matching

  ```cpp
  semver::range_set range;
  if (semver::parse(">=1.0.0 <2.0.0 || >3.2.1", range)) {
    semver::version version;
    if (semver::parse("1.2.3", version)) {
      assert(range.contains(version));
    }
  }
  ```

Check the *examples* folder to see more various usage examples

## Installation

Run:

```bash
$ npm i semver.cxx
```

And then include `semver.hpp` as follows:

```cxx
// main.cxx
#include <semver.hpp>

int main() { /* ... */ }
```

Finally, compile while adding the path `node_modules/semver.cxx` to your compiler's include paths.

```bash
$ clang++ -std=c++20 -I./node_modules/semver.cxx main.cxx  # or, use g++
$ g++     -std=c++20 -I./node_modules/semver.cxx main.cxx
```

You may also use a simpler approach with the [cpoach](https://www.npmjs.com/package/cpoach.sh) tool, which automatically adds the necessary include paths of all the installed dependencies for your project.

```bash
$ cpoach clang++ -std=c++20 main.cxx  # or, use g++
$ cpoach g++     -std=c++20 main.cxx
```

---

Alternatively, you should add required file [semver.hpp](semver.hpp).

If you are using [vcpkg](https://github.com/Microsoft/vcpkg/) on your project for external dependencies, then you can use the [neargye-semver](https://github.com/microsoft/vcpkg/tree/master/ports/neargye-semver).

If you are using [Conan](https://www.conan.io/) to manage your dependencies, merely add `neargye-semver/x.y.z` to your conan's requires, where `x.y.z` is the release version you want to use.


Alternatively, you can use something like [CPM](https://github.com/TheLartians/CPM) which is based on CMake's `Fetch_Content` module.

```cmake
CPMAddPackage(
    NAME semver
    GITHUB_REPOSITORY Neargye/semver
    GIT_TAG x.y.z # Where `x.y.z` is the release version you want to use.
)
```

## Compiler compatibility

* Clang/LLVM >= 5
* MSVC++ >= 14.11 / Visual Studio >= 2017
* Xcode >= 10
* GCC >= 7

## Licensed under the [MIT License](LICENSE)

<br>
<br>


[![](https://raw.githubusercontent.com/qb40/designs/gh-pages/0/image/11.png)](https://wolfram77.github.io)<br>
[![SRC](https://img.shields.io/badge/src-repo-green?logo=Org)](https://github.com/Neargye/semver)
[![ORG](https://img.shields.io/badge/org-nodef-green?logo=Org)](https://nodef.github.io)
![](https://ga-beacon.deno.dev/G-RC63DPBH3P:SH3Eq-NoQ9mwgYeHWxu7cw/github.com/nodef/semver.cxx)

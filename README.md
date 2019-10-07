# Coding Guidelines and Information

## Tech Stack

Following languages and technologies are part of our tech stack:
### Languages
- C++17 https://isocpp.org/
- Golang https://golang.org/
### Technologies
- Kubernetes https://kubernetes.io/
- Zookeeper http://zookeeper.apache.org/
- Kafka http://kafka.apache.org/
- Cassandra http://cassandra.apache.org/
### Libraries
- gRPC https://grpc.io/
- flatbuffers https://google.github.io/flatbuffers/
- Google Test https://github.com/google/googletest
- Google benchmark https://github.com/google/benchmark
- Lib UV https://github.com/libuv/libuv
- BorringSSL https://boringssl.googlesource.com/boringssl/
### Tools
- Bazelbuild https://www.bazel.build/
- Buildkite https://buildkite.com/
- ClangTidy https://clang.llvm.org/extra/clang-tidy/index.html
- ClangFormat https://clang.llvm.org/docs/ClangFormat.html

**Note** that this informations are prone to change 

## Coding Guidelines

### General Coding Guidelines

Some rules apply to all the languages in our stack
 - Name identifiers descriptively and never use acronyms or single characters (Not even in loops).
 - Aim for readability and split large procedures (15 lines should be the limit).
 - Comment your intent, not what the code is doing. The code should explain itself.
 - Prefer immutability and side-effect free functions.
 - Write code for the reader.
 
Ahiv uses a MIT style license, following code should be the header of every source file:
```
// Copyright 2019 Ahiv Authors. All rights reserved. Use of this source  code  
// is governed by a MIT-style license that can be found in the LICENSE file.
```
If the language does not support C++ style block comments, use the languages default style of comments.

### C++ Coding Guidelines

Our C++ guidelines are based on the [Google Style Guide](https://google.github.io/styleguide/cppguide.html),
with the following exceptions:

  - Pointer and reference characters should be left aligned:
    Thus `const Record &record` becomes `const Record& record`
  - Variables are written in `lowerCamelCase`, not `lower_underscore`
  - Instance fields have no trailing underscore.
  - Constants and enum fields are written `UpperCamelCase` without a leading `k`.
  - The name of accessors is the name of their properties: 
      `id()` instead of `GetId()`
  - Clang-tidy warnings should never be ignored. 
  - When the methods result should not be discarded, annotate the method with `[[nodiscard]]`.
  - When the method does never throw an exception, mark it with `noexcept`.
  - The name of mutators is the `UpperCamelCase` name of their properties with a leading `set`:
      `setZone(Zone)` instead of `zone(Zone)` or `SetZone(Zone)`.
    Note, that mutators should be used sparingly. Good alternatives to `setZone` would be:
      - `UpdateZone(Zone)`
      - `ChangeZone(Zone)`  
      
Following `.clang-format` configuration should be used throughout the project:
```yml
BasedOnStyle: Google
PointerAlignment: Left
```

### Go Coding Guidelines

Our Go guidelines are heavily based on the [Effective Go Article](https://golang.org/doc/effective_go.html),
with some exceptions:
  - As stated before, identifie, names should be descriptive and never acronyms or one character long.
    It's common for go code to use acronyms for receiver function parameters, **don't do that**.
  - Since go indentation is one tab, following lines of code should be in 
    every go containing repositories `.editorconfig`:
      
      ```editorconfig
      [*.go]
      tab_width = 2
      indent_style = tab
      indent_size = 2
      ```
### Commit Style Guide
This article explains how to write good commits: https://chris.beams.io/posts/git-commit/
Prepend an issue id, when fixing an issue with your commit.

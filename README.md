# Swift access to C HTSLIB

## Installation

### On OSX with Homebrew
1. `brew install homebrew/science/htslib`
2. Get to version 1.3 `brew switch htslib 1.3`

### General Unix isntallation
1. Download/compile `htslib` version 1.3
2. Install `htslib` with prefix `/usr/local/`

## Usage
See [jstjohn/swift-c-htslib-example](https://github.com/jstjohn/swift-c-htslib-example)

## Limitations

- No swift wrappers around the C objects returned by htslib functions, they are all of type `UnsafeMutablePointer<T>`
- No swift support for C macros. Many functions like `sam_open` are actually macros that call other functions. You need to call the underlying function that the macro calls in swift. The workaround would be to reimplement all `htslib` macros as swift functions that replicate the behavior of the macro.
- Non-flexible requirement that `htslib` is installed to `/usr/local/[include,lib,share]`. The current swift package system does not have a nice way to package c libraries in a portable way [Support for Other Build Systems](https://github.com/apple/swift-package-manager/blob/master/Documentation/PackageManagerCommunityProposal.md)


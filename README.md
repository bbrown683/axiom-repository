# Axiom Repository
This is the home of the axiom package repository. It contains TOML specifications on how to declaratively build and package the artifacts.
This is subject to change.
### Package
This section provides basic package information.
```toml
[package]
name = "m4"
license = ["GPL-3.0-or-later"]
homepage = "https://www.gnu.org/software/m4"
description = "GNU M4 is an implementation of the traditional Unix macro processor."
```
### Build
This section specifies how to build this package. This lets you configure the generator (autotools, meson, cmake, etc.) of choice,
and the system to use (make, ninja, etc.)
```toml
[build]
generator = "autotools"
system = "make"
```
#### Build Configuration
You can also configure the generators and system further.
```toml
[build.autotools]
config = { "prefix" = "/usr"}

[build.make]
threads = 10
silent = true
```
#### Build Dependencies
If your package requires dependencies, these can be specified here. These will also need a relevant definition in the repository.
```toml
[build.dependencies]
build = ["bash"]
required = ["glibc"]
optional = []
```
### Output
This section specifies what to do with the generated output.
```toml
[output]
binaries = ["m4"]
libraries = []
share = ["doc/m4.txt"]
manuals = ["m4.1.gz"]
```
#### Desktop 
You can also specify if a desktop entry should be generated for this package.
```toml
[output.desktop]
name = "IntelliJ IDEA"
exec = "idea"
icon = "intellij.svg"
category = ["Development", "Utility"]
```
### Version
This section specifies how to acquire the sources for building the package. Multiple `[[version]]` tables can be defined, 
with each entry being a new version. It will support Tarballs and Git.
#### Tarball
```toml
[[version]]
tag = "1.4.20"
tarball = { "url" = "https://ftp.gnu.org/gnu/m4/m4-1.4.20.tar.gz", "checksum" = "6ac4fc31ce440debe63987c2ebbf9d7b6634e67a7c3279257dc7361de8bdb3ef" }
```
#### Git
```toml
[[version]]
tag = "3.4.0"
git = { "url" = "https://github.com/libsdl-org/SDL", "tag" = "3.4.0", "branch" = "main", "commit" = "a962f40bbba175e9716557a25d5d7965f134a3d3" }
```
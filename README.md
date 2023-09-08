# little-hell




## Building

Builds are officially supported for Linux, macOS and Windows. Note that Windows builds require the use of [MSYS2](https://msys2.org).

### Troubleshooting

If you have difficulty getting any of this to work (whether the documentation be incomplete, unclear, or inaccurate) or otherwise have a bad developer experience that should be considered a _BUG_ and you should file a GitHub issue ❤️

### Dependencies

- SDL2
- SDL2_mixer
- SDL2_net
- Git
- Meson
- Python 3 (for Meson)
- CMake (for Meson and SDL)


### Setup for Linux and macOS (Nix Package Manager)

It's highly recommended that if you're on Linux or macOS, you install the [Nix](https://nixos.org/download) package manager. 
This will allow you to simultaneously obtain all the dependencies _and_ launch a virtual environment where they are all installed, with one command.

From the project root:

```nix-shell shell.nix```

Now the project dependencies are installed, and you're dropped into an environment primed and ready to [compile the project](#compiling).

### Setup for BSD

I haven't tried building yet on BSD, but there's no reason it shouldn't work. Refer to the [dependencies](#dependencies) section and find each of those packages in your ports tree and install them.
After that, you should be good to [compile the project](#compiling).


### Setup on Windows
The officially supported method of building Little Hell on Windows is to use [MSYS2](https://msys2.org). Refer to the MSYS2 documentation for installation. 

Choose the **MSYS2 UCRT64** terminal and enter the following:

``` 
pacman -S mingw-w64-ucrt-x86_64-meson mingw-w64-ucrt-x86_64-SDL2 mingw-w64-ucrt-x86_64-SDL2_mixer mingw-w64-ucrt-x86_64-SDL2_net mingw-w64-ucrt-x86_64-ninja mingw-w64-ucrt-x86_64-cmake mingw-w64-ucrt-x86_64-gcc
```

<!-- pacman -S mingw-w64-x86_64-SDL2_mixer mingw-w64-x86_64-meson mingw-w64-x86_64-ninja mingw-w64-x86_64-python3 mingw-w64-x86_64-SDL2 mingw-w64-x86_64-SDL2_net mingw-w64-x86_64-gcc mingw-w64-x86_64-cmake -->

Now you're ready to [compile the project](#compiling).

Note that while we are installing CMake as a package, it's being used by Meson to find dependencies (such as SDL). 

### Compiling

After you gotten the dependencies sorted out for your specific platform in the section(s) above, the rest of the build process is universal regardless of what system you're on, thanks to Meson and Ninja.

From the project directory, run the following at a terminal (Linux/macOS/BSD) or a MSYS2 MINGW64 shell (Windows):

```
meson setup build
ninja -C build
```

This _should work_. If it fails to find a dependency, ensure that you've installed them as above. If it still doesn't work for you, that's considered a bug and you should file a GitHub issue! If the actual code fails to compile, that is _also_ a bug and 
you should file a GitHub issue.



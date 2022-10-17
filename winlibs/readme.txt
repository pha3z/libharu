2022-Oct-16
By James Houx

On Linux and Mac OS, you don't need to worry about ZLIB and LIBPNG, because they should be automatically detected for builds.  For deployment, they are also included in most distros.  For MacOS if they're missing, all you have to do isa single "brew" cmd one-liner to install each of them.

Windows is a different story....
Building Haru on Windows requires ZLIB and LIBPNG static libraries to be explicitly referenced for cmake.  You have to get latest builds of the libraries yourself, put them in a folder, and then include them in the cmake command.

The point of this winlibs folder is to save you the step of hunting down the libraries and building them.  Zlib and Libpng .lib (static library) and .h (header files) are included in this winlibs folder.  All you have to do is include them in the cmake command using:

set CMAKE_INCLUDE_PATH=path_to_zlib_headers
set CMAKE_LIBRARY_PATH=path_to_zlib

Windows deployment will work without any hassles because you are building Haru with static zlib and libpng libraries.  The libraries will be baked into the haru build. They don't need to be present on deployment machine.
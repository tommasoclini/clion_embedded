# clion_embedded

This repository contains some informations about how to set up clion for embedded development.

| OS      | Support                             |
| ------- | ----------------------------------- |
| linux   | tested                              |
| macOS   | should work with some modifications |
| Windows | not supported                       |

Every platform has its own environment file, by default every environment "setup" file is going to sit in the `$HOME` directory, like this(`$HOME/.platform_setup`).

Whenever there's something to be done using that platform, the corresponding setup must be sourced.

All of the platforms supported here use CMake, CLion is great at working with CMake.

All supported platforms' environment files or "setups" are in the [ref](./environments_setups) directory, the user should adjust them to his needs(like changing home directory, these are just example setups).

As of now, only debug configurations are documented here as the rest of the configuration(toolchains) is well documented.

To import a debug configuration to a project, the user must copy the corresponding .xml file in the(maybe already created, if not, the user must create it) runConfigurations directory inside the .idea directory.

Please, take your time to understand what each configuration does.

| Platform | Tips and quirks                                                                                                                                                                                                                                                                                                                                     |
| -------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| zephyr   | it has been tested only with nucleo f446re, but theoretically, the configuration supports any kind of hardware.                                                                                                                                                                                                                                     |
| cubeclt  | the user must install stm32cubeclt, and move the generated .sh script(often in `/etc/profile.d`) in the home directory and rename it to `.cubeclt_setup`, the one found in this repository is just an example of what it is going to look like.                                                                                                     |
| esp-idf  | this is the most tricky one, the bundled GDB does not support the xtensa architecture, so the user should replace the default gdb client with the one relative to the corresponding soc, that file should look like `xtensa-esp32s3-elf-gdb` and it is usually found somewhere in the espressif tools installation(often `$HOME/.espressif/tools`). |

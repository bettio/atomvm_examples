
# AtomVM Elixir Example Programs

Welcome to the AtomVM Elixir Example programs.

The applications in this directory make use of the [AtomVM Mix Plugin](https://github.com/atomvm/ExAtomVM) to compile, assemble, and if applicable, flash the application onto an ESP32 device.

Some example programs can only run on specific platform.  The following table summarizes the platforms on which the Elixir example programs can be run.

| Example Program | esp32 | stm32 | generic_unix |
|-----------------|-------|-------|--------------|
| Blinky          | ✅ | ✅ | ❌ |
| HelloWorld      | ✅ | ✅ | ✅ |

To build and run an example in this directory, change your working directory to the corresponding example program, and execute the generic instructions below.

> WARNING!  The Elixir examples in this repository are currently under construction.  They may not run or even compile.  Stay tuned for updates!

## Generic Instructions

The following generic instructions apply to the Elixir tests in this repository.  Special notes about building and running the example programs that deviate from these instructions are noted in the README file for the particular example program.

### Building

To build and package this application into an AtomVM AVM file, use the `packbeam` target:

    shell$ mix deps.get
    shell$ mix atomvm.packbeam

This target will create the `Blinky.avm` file in the `./_build/default/lib/` directory.

### Running on the ESP32 platform

To run this application on the ESP32 platform, you must flash the application to the device attached to your computer via USB.  You may then optionally monitor the program via a serial console program to view any data output to the console.

#### Flashing onto an ESP32 Device

To flash this application to your ESP32 device, issue the `esp32_flash` target.  Use the `--port` option to specify the port to which your device is connected:

    shell$ mix atomvm.esp32_flash --port /dev/ttyUSB0

#### Monitoring an ESP32 Device

Use a serial console program, such as `minicom`, to attach to the device over USB:

    shell$ minicom -D /dev/ttyUSB0

### Running on the STM32 platform

TODO

### Running on Generic Unix platforms

To run this application on a generic UNIX platform, supply the path to the generated AVM file, together with the AtomVM core library

    shell% /path/to/AtomVM ./_build/default/lib/<example-program>.avm /path/to/atomvmlib.avm

where `<example-program>` is the name of the example program.

> Note.  Currently, you must build the AtomVM virtual machine from source, in order to run AtomVM applications on the generic UNIX platform.

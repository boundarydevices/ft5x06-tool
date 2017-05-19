FT5x06 Tool
===========

Boundary Devices user-space tool used to diagnose and/or update FT5xxx touch controllers.

This code was largely inspired from the [Focaltech GitHub driver](https://github.com/focaltech-systems/drivers-input-touchscreen-FTS_driver).

Requirements
------------

The source code itself isn't depending any external library, so no build dependency.

As for runtime dependency, the kernel must have `i2c-dev` support enabled.

Build instructions
------------------

Very straight-forward:
```
$ cd
$ git clone https://github.com/boundarydevices/ft5x06-tool
$ cd ft5x06-tool/
$ make
```

If you want to cross-compile the tool, simply provide a different `CC`.
```
$ CC=arm-linux-gnueabihf-gcc make
```

Finally, if you want to build it statically so it can run on any C library (like Android), just add the `LDFLAGS`.
```
$ LDFLAGS=-static CC=arm-linux-gnueabihf-gcc make
```

Usage
-----

The tool has an help output which lists all the different parameters.
```
FT5x06 tool usage: ft5x06-tool [OPTIONS]
OPTIONS:
	-a, --address
		I2C address of the FT5x06 controller (hex). Default is 0x38.
	-b, --bus
		I2C bus the FT5x06 controller is on. Default is 2.
	-c, --chipid
		Force chip ID to the value (hex). Default is read from controller.
	-i, --input
		Input firmware file to flash.
	-o, --output
		Output firmware file read from FT5x06.
	-h, --help
		Show this help and exit.
```

Here is an example on how to update the FW on our platforms:
```
# ft5x06-tool -i firmware.bin
```

Limitations
-----------

* This tool only was tested on a FT5426 chip from our [Tianma display](https://boundarydevices.com/product/bd070lic2/).
* Reading the firmware back doesn't work properly.

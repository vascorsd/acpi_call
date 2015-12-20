What is this about? See here - https://wiki.archlinux.org/index.php/Hybrid_graphics#Fully_Power_Down_Discrete_GPU

quick checkout, build and install this new kernel module
```
$ git clone < this repo url >
$ make
$ sudo make install
$ sudo depmod -a
```

load kernel module
```
$ sudo modprobe acpi_call
```

to discover which code works for you run:
```
$ ./examples/turn_off_gpu.sh
```

run when needed to deactive DGPU:
```
echo "\_SB.PCI0.RP05.PXSX._OFF" | sudo tee /proc/acpi/call
```

where the code after the echo is the one you found that works for you.

done :)

Notes: it's a kernel module so each time kernel is updated this module
needs to be built and installed again.

todo:
 - add dkms confs

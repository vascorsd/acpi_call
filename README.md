What is this about? See here - https://wiki.archlinux.org/index.php/Hybrid_graphics#Fully_Power_Down_Discrete_GPU

quick checkout, build and install this new kernel module
```
$ git clone < this repo url >
$ make
$ sudo insmod acpi_call.ko
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

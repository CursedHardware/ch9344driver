ifeq ($(KERNELRELEASE), )
KERNELDIR := /usr/src/linux-headers-$(shell uname -r)
MODULEDIR := /lib/modules/$(shell uname -r)/kernel/drivers/usb/serial
PWD := $(shell pwd)
default:
	$(MAKE) -C $(KERNELDIR) M=$(PWD)  
clean:
	rm -rf *.mk .tmp_versions Module.symvers *.mod.c *.o *.ko .*.cmd Module.markers modules.order
load:
	insmod ch9344.ko
unload:
	rmmod ch9344
install: default
	mkdir -p $(MODULEDIR)
	cp -f ch9344.ko $(MODULEDIR)
	depmod -a
uninstall:
	rm -rf $(MODULEDIR)/ch9344.ko
	depmod -a
else
	obj-m := ch9344.o
endif

# LinuxCNC Ethercat configuration

LinuxCNC EtherCAT config using lcec_deasda component

## set GRUB parameters
```
sudo geany /etc/default/grub

GRUB_CMDLINE_LINUX_DEFAULT="quiet isolcpus=5 intel_idle.max_cstate=0 idle=poll i915.enable_rc6=0 rcu_nocbs=5 cpufreq.default-governor=performance nomodeset"

sudo update-grub
```

## compile VFD modbus component
```
sudo apt install linuxcnc-uspace-dev

sudo apt install libmodbus-dev

sudo halcompile --userspace --install --extra-compile-args="-I/usr/include/modbus" --extra-link-args="-lm -lmodbus -llinuxcncini" vfde_vfd.c
```
## set symlink for USB ports
```
sudo geany /etc/udev/rules.d/01-usb.rules

echo "SUBSYSTEM=="tty", ATTRS{idVendor}=="1a86", ATTRS{idProduct}=="7523", SYMLINK+="ttyUSB_SEIKI"" > sudo tee /etc/udev/rules.d/01-usb.rules

echo "SUBSYSTEM=="tty", ATTRS{idVendor}=="10c4", ATTRS{idProduct}=="ea60", SYMLINK+="ttyUSB_DELTA"" > sudo tee /etc/udev/rules.d/01-usb.rules

sudo udevadm control --reload-rules
```
## edit USB port in arduino connector script
```
sudo geany /usr/bin/arduino-connector

ln -s /home/cnc/linuxcnc/3dworks_ethercat_lcec/arduino-connector /usr/bin/arduino-connector
```

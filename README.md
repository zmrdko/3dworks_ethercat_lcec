# 3dworks_ethercat_lcec
LinuxCNC EtherCAT config using lcec_deasda


sudo nano /etc/default/grub
GRUB_CMDLINE_LINUX_DEFAULT="quiet isolcpus=5 intel_idle.max_cstate=0 idle=poll i915.enable_rc6=0 rcu_nocbs=5 cpufreq.default-governor=performance nomodeset"

sudo update-grub


compile VFD component:
sudo apt install linuxcnc-uspace-dev
sudo apt install libmodbus-dev

sudo halcompile --userspace --install --extra-compile-args="-I/usr/include/modbus" --extra-link-args="-lm -lmodbus -llinuxcncini" vfde_vfd.c


sudo geany /etc/udev/rules.d/01-usb.rules
SUBSYSTEM=="tty", ATTRS{idVendor}=="1a86", ATTRS{idProduct}=="7523", SYMLINK+="ttyUSB_SEIKI"
SUBSYSTEM=="tty", ATTRS{idVendor}=="10c4", ATTRS{idProduct}=="ea60", SYMLINK+="ttyUSB_DELTA"

sudo udevadm control --reload-rules

sudo geany /usr/bin/arduino-connector

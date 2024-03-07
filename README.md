# 3dworks_ethercat_lcec
LinuxCNC EtherCAT config using lcec_deasda


sudo nano /etc/default/grub
GRUB_CMDLINE_LINUX_DEFAULT="quiet isolcpus=2,3 intel_pstate=disable intel_idle.max_cstate=0 idle=poll cpufreq.default_governor=performance"

sudo update-grub


 isolcpus=3 intel_pstate=disable processor.max_cstate=0 idle=poll cpufreq.default_governor=performance i915.enable_dc=0 ahci.mobile_lpm_policy=1 nomodeset quiet



VFD:
sudo apt install linuxcnc-uspace-dev
sudo apt install libmodbus-dev

sudo halcompile --userspace --install --extra-compile-args="-I/usr/include/modbus" --extra-link-args="-lm -lmodbus -llinuxcncini" vfde_vfd.c

# 3dworks_ethercat_lcec
LinuxCNC EtherCAT config using lcec_deasda


sudo nano /etc/default/grub
GRUB_CMDLINE_LINUX_DEFAULT="quiet isolcpus=2,3 intel_pstate=disable intel_idle.max_cstate=0 idle=poll cpufreq.default_governor=performance"

sudo update-grub

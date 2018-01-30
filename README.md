ansible-raspberrypi
===================

Ansible playbook to do a basic config of a raspberry pi with:

 * SSH
 * samba
 * external harddrive
 * transmission
 * unattended-upgrades

Prepare raspberrypi
-------------------

```
sudo dd if=2017-11-29-raspbian-stretch-lite.img bs=1M of=/dev/mmcblk0 
touch /media/t/boot/ssh
```

* Boot raspberrypi
* ssh pi@raspberrypi.local
* sudo raspi-config
 * 7 Advanced Options
  * A1 Expand Filesystem
* sudo reboot

Run ansible
-----------

```
ansible-galaxy install -r roles.yml
ansible-playbook playbook.yml
```

Furthermore, you can adjust `host.yml` to your needs.
Most important, set `ssh_key` to enable password-less SSH and Tor onion service.

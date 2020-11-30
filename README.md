ansible-raspberrypi
===================

Ansible playbook to do a basic config of a Raspberry Pi with:

 * External harddrive
 * SSH
 * Samba
 * [Raspotify](https://github.com/dtcooper/raspotify)
 * [Transmission](https://transmissionbt.com/)
 * unattended-upgrades
 * Enable hardware watchdog

Available, but disabled on default:

 * [HiFiBerry](https://www.hifiberry.com/)
 * Tor Onion Service

Prepare raspberrypi
-------------------

Flash SD card and enable ssh access:

```
wget https://downloads.raspberrypi.org/raspios_lite_armhf/images/raspios_lite_armhf-2020-08-24/2020-08-20-raspios-buster-armhf-lite.zip
unzip 2020-08-20-raspios-buster-armhf-lite.zip
sudo dd if=2020-08-20-raspios-buster-armhf-lite.img bs=1M of=/dev/mmcblk0
mount /dev/mmcblk0p2 /mnt 
touch /mnt/ssh
```

* Boot raspberrypi
* Make sure you can ssh into raspberrypi
  * `ssh pi@raspberrypi.local`

Run ansible
-----------

```
ansible-galaxy install -r roles.yml
ansible-playbook playbook.yml
```

Furthermore, you can adjust `host.yml` to your needs.
Most important, set `ssh_key` to enable password-less SSH and Tor onion service.

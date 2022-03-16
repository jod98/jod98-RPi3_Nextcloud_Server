# Raspberry Pi 3 Nextcloud Server - Your Self Hosted 'Google Drive'

Avoid the Google One subscription and retain your personal data with your own self hosted 'Google Drive' using Nextcloud.

-------------------------------------------------------------------------------------------------------------------------------

1. Download Raspian Pi OS Lite @ https://www.raspberrypi.com/software/operating-systems/
2. Flash the “.zip” file onto your SD card (preferably 8GB or greater) using Etcher @ https://www.balena.io/etcher/
3. Insert SD card into Raspberry Pi and connect it to your router via Ethernet cable.
4. Connect the Pi to your TV/monitor via a HDMI cable and login using:
>Username: “*pi*” <br />
>Password: “*raspberry*” <br />
5. Run “*sudo raspi-config*” to enable SSH so we can login using our remote machine.
6. Go to “Interfacing Options” and then enable SSH.
7. Login into your Pi using your computer by simply typing in the IP address of the Pi. Type “hostname -l” into the Pi to retrieve IP address if unsure.
8. Connect hard drive (HDD)
9. Download Putty @ https://www.putty.org/ and enter in the IP address of the Pi to access it remotely via the SSH protocol.
10. Update and upgrade current packages by entering the following into terminal:
>“*sudo apt update*” <br />
>“*sudo apt full-upgrade*” <br />
>“*sudo reboot*” <br />
11. Access Pi via Putty again (SSH) and create new password for login. Current password is:
>*(current) UNIX Password: openmediavault*
12. Restart Pi to commit new changes
>*sudo reboot*
13. Install OpenMediaVault (OMV) in Putty terminal after reboot:
>“*sudo wget -O - https://github.com/OpenMediaVault-Plugin-Developers/installScript/raw/master/install | sudo bash*” <br />
14. Open a browser and enter the Raspberry Pi's private IP address as the URL i.e. *192.168.178.24*
15. Login with the following credentials:
>Username: “*admin*” <br />
>Password: “*openmediavault*” <br />

![OMV_Login](https://user-images.githubusercontent.com/36043248/131504405-01039aef-51f3-474f-9838-e48a90275bf6.PNG)

Follow the tutorials below to complete the process...

16. OMV Settings Setup: https://youtu.be/M_oxzpvMPTE
17. NGINX Proxy Manager Install: https://www.youtube.com/watch?v=2oi4IQF7VnE or https://nginxproxymanager.com/
18. Nextcloud Install (using Docker and Portainer): https://www.youtube.com/watch?v=HkAqt6WreGQ or https://www.addictedtotech.net/installing-nextcloud-on-raspberry-pi-4/

Refer to this guide for port forwarding, domain, DDNS, proxy and SSL. Steps '14' onwards: https://github.com/jod98/RPi3_Web_Server---Host_for_FREE/blob/master/README.md


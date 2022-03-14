# Raspberry Pi 3 Nextcloud Server - Your Self Hosted 'Google Drive'

Avoid the Google One subscription and retain your personal data with your own self hosted 'Google Drive' using Nextcloud.

-------------------------------------------------------------------------------------------------------------------------------

1. Download Raspian Pi OS Lite (Debian Version 10 - Buster) @ https://www.raspberrypi.com/software/operating-systems/
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
11. Install OpenMediaVault (OMV) in Putty terminal after reboot:
>“*sudo wget -O - https://github.com/OpenMediaVault-Plugin-Developers/installScript/raw/master/install | sudo bash*” <br />
12. Open a browser and enter the Raspberry Pi's private IP address as the URL i.e. *192.168.178.24*
13. Login with the following credentials:
>Username: “*admin*” <br />
>Password: “*openmediavault*” <br />

![OMV_Login](https://user-images.githubusercontent.com/36043248/131504405-01039aef-51f3-474f-9838-e48a90275bf6.PNG)

13. In 'System' :
    - 'General Settings'
        - 'Web Administration' - set 'Auto logout' to' Disabled' -> *Save*
        - 'Web Administration Password' - create a new password to access OMV -> *Save*
    - 'Date & Time' - change timezone to current timezone -> *Save*
    - 'Network' - 'Interfaces' 
        - Click 'Add' -> 'Ethernet'
            - 'General Settings' - 'Name': select device i.e. 'eth0'
            - 'IPv4' - 'Method': select 'DHCP'
            - 'Advanced Settings' - 'DNS Servers': "8.8.8.8" -> *Save*
    - 'Update Management' - click '☐ Package information' and click '+Upgrade'


NOT SURE FROM HERE DOWNWARDS!
    
14. In 'Storage' :
    - 'File Systems'
        - Click '+Create'
            - 'Device' - *your HDD*
            - 'Label' - "Plex Pi HDD" -> *Save*
        - *Once file system created* - click 'Mount' (access HDD content over network)
        
15. In 'Access Rights Management' :
    - 'User'
        - Click '+Add'
            - 'General'
                - 'Name': *your name*
                - 'Email': *your email*
                - 'Password': *your password*
                - 'Confirm Password': *your password*
            - 'Groups'
                - Click '☐ sambashare'
                - Click '☐ ssh'
                - Click '☐ sudo'
                - Click '☐ users' -> *Save*
    - 'Shared Folders'
        - Click '+Add'
            - 'Name': 'Movies'
            - 'Device': *select HDD device*
            - 'Path': 'Movies/'
            - 'Permissions': 'Everyone: read/write' -> *Save*
        - Click '+Add'
            - 'Name': 'TV_Shows'
            - 'Device': *select HDD device*
            - 'Path': 'TV_Shows/'
            - 'Permissions': 'Everyone: read/write' -> *Save*

15. In 'Services' :
    - 'SMB/CIFS'
        - 'Settings'
            - Click 'Enable' -> *Save*
        - 'Shares'
            - Click '+Add'
                - 'Shared Folder': *select recently created shared folder i.e. 'Movies'*
                - 'Public': 'Guests Allowed' 
                - 'Inherit permissions': 'Enable' -> *Save*
            - Click '+Add'
                - 'Shared Folder': *select recently created shared folder i.e. 'TV_Shows'*
                - 'Public': 'Guests Allowed' 
                - 'Inherit permissions': 'Enable' -> *Save*
    - 'SSH'
        - 'Permit root login': 'Enable' -> *Save*

16. Close OMV + Navigate to 'Windows Explorer' -> 'Network'. Verify that the Raspberry Pi is visible and content is accessible on the network

![RaspberryPi_Network](https://user-images.githubusercontent.com/36043248/131515974-a62fe16a-5ca9-4325-9e8e-547f934891c4.png)

17. Access Pi via Putty again (SSH) and create new password for login. Current password is:
>*(current) UNIX Password: openmediavault*
18. Restart Pi to commit new changes
>*sudo reboot*

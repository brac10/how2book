# Adding Conky
sudo apt-get install conky
1. Create conky.sh file
-  sudo nano /usr/bin/conky.sh

#Fill with:
---
#!/bin/sh
(sleep 4s && conky) &
exit 0
---

2. Create Desktop startup command 
-  sudo nano /etc/xdg/autostart/conky.desktop
Fill with:
---
[Desktop Entry]
Name=conky
Type=Application
Exec=sh /usr/bin/conky.sh
Terminal=false
Comment=system monitoring tool.
Categories=Utility;
----

download the conkyrc file to home directory as .conkyrc

wget -O /home/pi/.conkyrc https://raw.githubusercontent.com/brac10/software/master/rpi3_conkyrc

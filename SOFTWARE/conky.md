# Adding Conky
sudo apt-get install conky
1. Create conky.sh file
-  sudo nano /usr/bin/conky.sh
Fill with:
#!/bin/sh
(sleep 4s && conky) &


exit 02. Create Desktop startup command 
-  sudo nano /etc/xdg/autostart/conky.desktop
Fill with:

[Desktop Entry]
Name=conky
Type=Application
Exec=sh /usr/bin/conky.sh
Terminal=false
Comment=system monitoring tool.
Categories=Utility;

 
adding conky to raspberry pi

sudo apt-get install conky

download the conkyrc file to home directory as .conkyrc

wget -O /home/pi/.conkyrc https://raw.githubusercontent.com/novaspirit/rpi_conky/master/rpi3_conkyrc

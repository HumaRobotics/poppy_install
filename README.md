Poppy software installation
===========================

Branch: raspi-light
install on a new raspberry pi 2  with 'pypot light' from humarobotics (without scipy)

What is specific to raspberry pi ?
- no automatic resize
- TODO install x11 ?
- TODO put config.txt in /boot (screen config)
- TODO lightdm to avoid screen sleep mode: 
```bash
    sudo nano /etc/lightdm/lightdm.conf
     ```   
 add in file:
```bash 
    xserver-command=X -s 0 dpms
     ```  
     
 - TODO yeux au démarrage: 
```bash
    sudo apt-get install fbi
     ```  
     
 - TODO text to speech : http://rpihome.blogspot.fr/2015/02/installing-pico-tts.html
 + in raspi-config, advanced, force audio jack output
     
Let's start the installation :

 1. Connecting you to the board over ssh.
    ```bash
      $ ssh pi@raspberrypi.local
      pi@raspberrypi.local password: "raspberry"
      pi@raspberrypi.local:~$
    ```

 1b. Use all the space from SD card
    ```bash
      pi@raspberrypi.local:~$sudo raspi-confi
    ```
    Select the first line and accept the resize. Accept the reboot.

 2. Download and run poppy_setup.sh
    ```bash
      pi@raspberrypi.local:~$ curl -L https://raw.githubusercontent.com/HumaRobotics/poppy_install/raspi-light/poppy_setup.sh | sudo bash
    ```
    Do not forget to set the root password "odroid"

 3. You should lost your ssh connection because of the board reboot. This reboot is needed to proceed to the finalisation of the partition resizing. Now your board should installing all the poppy environement. Please do not unpower the board or shut-it down.  
 You can see the instalation process by reconnecting you to your board with your new poppy acount:
```bash
  $ ssh poppy@poppy.local
  poppy@poppy.local password: "poppy"
  poppy@poppy:~$
```
  A process will automatically take you terminal and print the installation output. You can leave it with `ctrl+c`. You can get back this print by reading the install_log file :
```bash
poppy@poppy:~$ tail -f /home/poppy/install_log
...
```
If the last line is :
```bash
System install complete!
Please share your experiences with the community : https://forum.poppy-project.org/
```
The installation is finish, you can restart your Poppy and start to play!
```bash
poppy@poppy:~$ sudo reboot
```

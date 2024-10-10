# fixing port permission

setting permissions via the following commands, it worked on the Appimage version fine without problems 

![[Pasted image 20231021234759.png]]

```bash
sudo usermod -a -G dialout dino
sudo usermod -a -G tty dino
sudo chmod a+rw /dev/ttyUSB0 # or the desired usb port depending on what the ide Shows
```




### Tags
#arduino 
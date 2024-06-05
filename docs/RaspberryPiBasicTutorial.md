# **Install Raspberry Pi OS System：**

This tutorial covers how to burn the Raspberry Pi system, how to find the IP address of the Raspberry Pi, and how to perform VNC remote desktop.

## **（一）Hardware and Software：**

### **1.Required Hardware：**

(1) Raspberry Pi 4B/5  (2) TFT memory card above 16G  (3) Card reader  (4) Commonly used computer and accessories

### **2.Operation Method：**

##### （1）Raspberry Pi Imager Software（official software）

**Raspberry Pi Imager Software：**

Download link： [Raspberry Pi Imager](https://www.raspberrypi.com/software/)

![](./media/A1.png)

After the download is successful, click Install and open it after installation.

![A2](./media/A2.png)

We use Raspberry Pi 5, so select Raspberry Pi 5 in the "Raspberry Pi Device".

![image-20240424131421972](./media/A22.png)

Select "Raspberry Pi OS (64-bit)" in the column below "Operating System" (64-bit or 32-bit is according to the bit of your Raspberry Pi).

![image-20240424131615662](./media/A23.png)

Select the SD card to which we want to burn the Raspberry Pi image system in the column below "Storage".

![image-20240424132318451](./media/A24.png)

Then click![image-20240424132856746](./media/A25.png) 

Set the Raspberry Pi login name and password, click on `EDITSETTINGS`.

![a46](./media/A46.png)

First, check `Set host name`and `Set username and password`, then fill in `Username` as' pi 'and`Password`as' raspberry' (you can also change it to the name and password you want).

![a47](./media/A47.png)

After setting the login name and password, click on `Services` on the right side, then check`Enable SSH `and`Use password authentication`, and finally click on`SAVE `.

![a48](./media/A48.png)



Click`YES`.

![a49](./media/A49.png)

Click `YES` to start burning, be patient and wait until the burning is completed.

![a44](./media/A44.png)

![a45](./media/A45.png)

####  （2）Install putty（for SSH remote connection）

Download link：[https://www.chiark.greenend.org.uk/~sgtatham/putty/](https://www.chiark.greenend.org.uk/~sgtatham/putty/)

![img](./media/A3.png) 

![img](./media/A4.png)

a. After downloading the putty driver file![img](./media/A5.png), double-click it and then click "Next".

​    ![img](./media/A6.png)

b. Tap “Next”.

  ![img](./media/A7.png)

c. Tap “Install Putty files” and “Install”.

  ![img](./media/A8.png)

d. Tap “Finish”.

 ![img](./media/A9.png)



##### (3) SSH Remote Login Software WinSCP (can view the Raspberry Pi IP address)

Download link：[https://winscp.net/eng/download.php](https://winscp.net/eng/download.php)

a. After downloading the WinSCP software file![img](./media/A12.png), double-click it, then click ![img](./media/A13.png).

​     ![img](./media/A14.png)

b. Click “Accept”，“Next” and “Install”.

​    ![img](./media/A15.png)

​    ![img](./media/A16.png)

​    ![img](./media/A17.png)

   ![img](./media/A18.png)

c. After a few seconds, the installation will be completed, click "Finish".

   ![img](./media/A19.png)

Use WinSCP to log in through the default name, default username, and default password of the Raspberry Pi system,These are set when burning the system and need to be consistent with the burning system. (Only one Raspberry Pi can be connected to the same network).![image-20240424142624855](./media/A27.png)

 ![image-20240424142642564](./media/A28.png)

To view the ip address and mac address, click![](./media/A29.png) to link and open the PuTTY software, then enter `ip a` to see the ip address. Or click![](./media/A30.png) and then enter `ip a` in the command box to see the ip address.![](./media/A31.png)

After clicking to open the terminal, you need to enter the password again: raspberry, and then press Enter on the keyboard.

![](./media/A33.png)

After successful login, open the terminal, enter ***\*ip a\**** and then press Enter on the keyboard to view the ip and mac addresses.

```bash
ip a
```

  ![](./media/A32.png)

As can be seen from the circle in the picture above, the mac address of my Raspberry Pi is: d8:3a:dd:bf:47:73, and the IP address is: 192.168.0.72(It will be used when we use xrdp to remotely log in to the Raspberry Pi system desktop).

The mac address will not change. If you are not sure which ip address it is, you can use the mac address to confirm it.

##### (4)  Use PuTTY software to remotely connect to the Raspberry Pi, and set the Raspberry Pi to open VNC

1. Use the PuTTY software to open the VNC of the Raspberry Pi, log in with the IP found on the WinSCP software

Enter the IP address in the "Host Name (or IP address)" box and click "OPEN".

![](./media/A10.png)

login as：If you don't modify it, the default is "pi".

pi@xxx.xxx.xxx.xxx‘s password：If you don't modify it, the default is “raspberry”.

![](./media/A11.png)

 Then enter `sudo raspi-config` after successful login and press Enter to enter the setting page (if you have opened the PuTTY software through the WinSCP software, there is no need to reopen it).

```bash
sudo raspi-config
```

![](./media/A34.png)

2.Use![img](./media/F36.png) of the keyboard to select "3 Interface Options" and press Enter.

![image-20240424145202144](./media/A35.png)

3.Select "I2 VNC" and press the Enter key, then select "YES" and press the Enter key. After the setting is successful, press the "ESC" key on the keyboard to exit it.

![](./media/A36.png)

![](./media/A37.png)

![](./media/A38.png)

##### （5）VNC viewer（VNC is used to log in to the Raspberry Pi system interface）

Download link：[https://www.realvnc.com/en/connect/download/viewer/](https://www.realvnc.com/en/connect/download/viewer/)

![img](./media/A20.png)

 Then Install it.

![](./media/A21.png)

1.Open the VNC viewer software, then click "File" and "New connection...".

![](./media/A39.png)

2. Enter the Raspberry Pi's IP address in the VNC Server and click "OK".

![](./media/A40.png)

3.Double click on the server named 192.168.0.72.

![](./media/A41.png)

4.Enter pi in the "Username" box, enter raspberry in the password box (note: this is the default if you have not changed the Raspberry Pi login name and password), then check "Remember password" and click OK.

![](./media/A42.png)

5.Login is successful.

![](./media/A43.png)


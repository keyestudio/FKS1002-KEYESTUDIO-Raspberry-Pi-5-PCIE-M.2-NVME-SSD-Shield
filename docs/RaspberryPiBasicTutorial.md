# **Install Raspberry Pi OS System：**

This tutorial covers how to burn the Raspberry Pi system, how to find the IP address of the Raspberry Pi, and how to perform VNC remote desktop.

## **（一）Hardware and Software：**

### **1.Required Hardware：**

(1) Raspberry Pi 4B/5  (2) TFT memory card above 16G  (3) Card reader  (4) Commonly used computer and accessories

### **2.Required Software：**

##### （1）Raspberry Pi Imager Software（official software）

**Raspberry Pi Imager Software：**

Download link： [Raspberry Pi Imager](https://www.raspberrypi.com/software/)

![image-20240424130313356](./media/image-20240424130313356.png)

After the download is successful, click Install and open it after installation.

![image-20240424130808984](./media/image-20240424130808984.png)

 

##### （2）Install putty（for SSH remote connection）

Download link：[https://www.chiark.greenend.org.uk/~sgtatham/putty/](https://www.chiark.greenend.org.uk/~sgtatham/putty/)

![img](./media/wps1.jpg) 

![img](./media/wps2.jpg)

a. After downloading the putty driver file![img](./media/wps3.jpg), double-click it and then click "Next".

​    ![img](./media/wps4.jpg)

b. Tap “Next”.

  ![img](./media/wps5.jpg)

c. Tap “Install Putty files” and “Install”.

  ![img](./media/wps6.jpg)

d. Tap “Finish”.

 ![img](./media/wps7.jpg)

e. Using Method

Enter the IP address in the "Host Name (or IP address)" box and click "OPEN".

![image-20240424115215036](./media/image-20240424115215036.png)

login as：If you don't modify it, the default is "pi".

pi@xxx.xxx.xxx.xxx‘s password：If you don't modify it, the default is “raspberry”.

![image-20240424141145027](./media/image-20240424141145027.png)

##### (3) SSH Remote Login Software WinSCP (can view the Raspberry Pi IP address)

Download link：[https://winscp.net/eng/download.php](https://winscp.net/eng/download.php)

a. After downloading the WinSCP software file![img](./media/wps10-1713939727629-5.jpg), double-click it, then click ![img](./media/wps12-1713939727629-7.jpg).

​     ![img](./media/wps13-1713939727629-8.jpg)

b. Click “Accept”，“Next” and “Install”.

​    ![img](./media/wps14-1713939727629-9.jpg)

​    ![img](./media/wps15-1713939727629-10.jpg)

​    ![img](./media/wps16-1713939727630-11.jpg)

   ![img](./media/wps17-1713939727630-12.jpg)

c. After a few seconds, the installation will be completed, click "Finish".

   ![img](./media/wps18-1713939727630-13.jpg)





##### （4）VNC viewer（VNC is used to log in to the Raspberry Pi system interface）

Download link：[https://www.realvnc.com/en/connect/download/viewer/](https://www.realvnc.com/en/connect/download/viewer/)

![img](./media/wps25-1713940996905-40.jpg)

 Then Install it.

![image-20240424144504982](./media/image-20240424144504982.png)

#### 3.Operation Method

This step can only be performed after installing the software.

##### Step 1: Use the Raspberry Pi Imager software to burn the Raspberry Pi image system to the SD card and create an SSH file in bootfs.

We use Raspberry Pi 5, so select Raspberry Pi 5 in the "Raspberry Pi Device".

![image-20240424131421972](./media/image-20240424131421972.png)

Select "Raspberry Pi OS (64-bit)" in the column below "Operating System" (64-bit or 32-bit is according to the bit of your Raspberry Pi).

![image-20240424131615662](./media/image-20240424131615662.png)

Select the SD card to which we want to burn the Raspberry Pi image system in the column below "Storage".

![image-20240424132318451](./media/image-20240424132318451.png)

Then click![image-20240424132856746](./media/image-20240424132856746.png) to start burning

After the image system is burned, unplug the card reader and plug it in again to see "bootfs". Create a new text file named SSH, delete the .txt, and then copy it to the bootfs directory of the SD card. Then the SSH login function can be enabled, as shown in the figure below:

![img](./media/wps46.jpg)

##### Step 2: Use WinSCP software to find the IP address of the Raspberry Pi

Use WinSCP to log in through the default name, default username, and default password of the Raspberry Pi system. (Only one Raspberry Pi can be connected to the same network).![image-20240424142624855](./media/image-20240424142624855.png)

 ![image-20240424142642564](./media/image-20240424142642564.png)

To view the ip address and mac address, click![image-20240424143853242](./media/image-20240424143853242.png) to link and open the PuTTY software, then enter `ip a` to see the ip address. Or click![image-20240424144005368](./media/image-20240424144005368.png) and then enter `ip a` in the command box to see the ip address.![image-20240424142704026](./media/image-20240424142704026.png)

After clicking to open the terminal, you need to enter the password again: raspberry, and then press Enter on the keyboard.

  ![image-20240424141145027](./media/image-20240424141145027.png)

After successful login, open the terminal, enter ***\*ip a\**** and then press Enter on the keyboard to view the ip and mac addresses.

```bash
ip a
```

  ![image-20240424140843998](./media/image-20240424140843998.png)

As can be seen from the circle in the picture above, the mac address of my Raspberry Pi is: d8:3a:dd:bf:47:73, and the IP address is: 192.168.0.72(It will be used when we use xrdp to remotely log in to the Raspberry Pi system desktop).

The mac address will not change. If you are not sure which ip address it is, you can use the mac address to confirm it.

##### Step 3: Use PuTTY software to remotely connect to the Raspberry Pi, and set the Raspberry Pi to open VNC

1. Use the PuTTY software to open the VNC of the Raspberry Pi, log in with the IP found on the WinSCP software, then enter `sudo raspi-config` after successful login and press Enter to enter the setting page (if you have opened the PuTTY software through the WinSCP software, there is no need to reopen it).

```bash
sudo raspi-config
```

![image-20240424145020125](./media/image-20240424145020125.png)

2.Use![img](./media/d1160924ab18972ba911ffa8feb5fa849e510a2a.jpeg) of the keyboard to select "3 Interface Options" and press Enter.

![image-20240424145202144](./media/image-20240424145202144.png)

3.Select "I2 VNC" and press the Enter key, then select "YES" and press the Enter key. After the setting is successful, press the "ESC" key on the keyboard to exit it.

![image-20240424145352644](./media/image-20240424145352644.png)

![image-20240424145454275](./media/image-20240424145454275.png)

![image-20240424145934799](./media/image-20240424145934799.png)

##### Step 4: Connect to the Raspberry Pi remotely via VNC viewer software

1.Open the VNC viewer software, then click "File" and "New connection...".

![ae1d321b3bb65e0de766d2782d736ab8](./media/ae1d321b3bb65e0de766d2782d736ab8.png)

2. Enter the Raspberry Pi's IP address in the VNC Server and click "OK".

![image-20240424150202645](./media/image-20240424150202645.png)

3.Double click on the server named 192.168.0.72.

![image-20240424150309374](./media/image-20240424150309374.png)

4.Enter pi in the "Username" box, enter raspberry in the password box (note: this is the default if you have not changed the Raspberry Pi login name and password), then check "Remember password" and click OK.

![image-20240424150458058](./media/image-20240424150458058.png)

5.Login is successful.

![image-20240424151047017](./media/image-20240424151047017.png)


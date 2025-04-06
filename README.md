<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
This tutorial outlines the prerequisites and installation of the open-source help desk ticketing system osTicket.<br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)

<h2>Operating Systems Used </h2>

- Windows 10</b> (22H2)

<h2>List of Prerequisites</h2>

- VM in Azure (2 cpus, 8gb RAM minimum) running Windows 10 Pro
- Collect osTicket required Installation Files, upload to cloud storage with public available link (Refer to for required installation files https://docs.osticket.com/en/latest/Getting%20Started/Installation.html)

<h2>Installation Steps</h2>

<p>
1. I've created the VM in Azure (Resource Group: osTicket-Lab, VM: osticket-vm) and connected to it via RDP using the username: labuser.
</p>

<p>
2. On the VM (osticket-vm), open your browser, download and unzip your osTicket installation files to the desktop from your cloud storage link. I collected the required installation files into a folder called osTicket-Installation-Files.zip. The unzipped folder will be named "osTicket-Installation-Files" and contains the files for osTicket and dependencies. You can see both the zip and unzipped folders in the image below
</p>
<img src="https://i.imgur.com/d0A1Dqj.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/3ZHlvEc.png" height="15%" width="15%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>
3. Install/Enable IIS in Windows with CGI. Make sure to enable CGI by following these steps:
Control Panel -> Programs -> Turn Windows features on or off -> World Wide Web Services -> Application Development Features -> Check CGI.
Click OK to install, and once the message "Windows completed the requested changes" appears, close the window.
</p>
<p>
<img src="https://i.imgur.com/Dv7GsH3.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>
4. Open your browser and enter the loopback address 127.0.0.1. You should see an IIS page, which verifies that your VM is now acting as a web server.
</p>
<p>
<img src="https://i.imgur.com/gLAdGMH.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>
5. From the “osTicket-Installation-Files” folder, install PHP Manager for IIS (PHPManagerForIIS_V1.5.0.msi)
</p>
<p>
<img src="https://i.imgur.com/evxj844.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>
6. From the “osTicket-Installation-Files” folder install the Rewrite Module (rewrite_amd64_en-US.msi)
</p>
<p>
<img src="https://i.imgur.com/gY3gvI4.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>
7. Create the directory C:\PHP
</p>
<p>
<img src="https://i.imgur.com/wp8SQ3E.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>
8. From the “osTicket-Installation-Files” folder, unzip PHP 7.3.8 (php-7.3.8-nts-Win32-VC15-x86.zip) into the “C:\PHP” folder. Explore to the C:\PHP and verify that it has been populated the php-7.3.8 files
</p>
<p>
<img src="https://i.imgur.com/guWY0om.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/vX3fu0n.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>
9. From the “osTicket-Installation-Files” folder, install VC_redist.x86.exe.
</p>
<p>
<img src="https://i.imgur.com/vskyhAd.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>
10. Install MySQL 5.5.62 from the "osTicket-Installation-Files" folder (mysql-5.5.62-win32.msi): <br />
Choose Typical Setup during installation <br />
After installation, launch the Configuration Wizard <br />
Select Standard Configuration <br />
Set the following credentials: <br />
- Username: root <br />
- Password: root <br />
</p>
<p>
<img src="https://i.imgur.com/SsPvduN.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>
10. Open IIS as an Admin
</p>
<p>
<img src="https://i.imgur.com/vskyhAd.png](https://i.imgur.com/vS4INNs.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/y2kzh4C.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>
11. Register PHP from within IIS (PHP Manager -> C:\PHP\php-cgi.exe). Then Reload IIS (Open IIS, Stop and Start the server, under Actions on the right you can see the options to stop and start the server.)
</p>
<p>
<img src="https://i.imgur.com/79qCPZ2.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/i5hVQLF.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/ujectw4.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>
12. From the “osTicket-Installation-Files” folder, unzip “osTicket-v1.15.8.zip” and copy the “upload” folder into “c:\inetpub\wwwroot”. Next, within “c:\inetpub\wwwroot”, Rename “upload” to “osTicket”. Then, Reload IIS (Open IIS, Stop and Start the server).
</p>
<p>
<img src="https://i.imgur.com/j5ggpYw.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/Y8wGHck.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/ujectw4.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>
13. Load the website now. Open IIS -> default site -> osTicket folder -> Click Browse 80 (http). Some extensions are not enabled that we need.
</p>
<p>
<img src="https://i.imgur.com/lIyQEvd.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/luZYeGM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/> 
</p>
<br />

<p>
14. Go back to IIS, sites -> Default -> osTicket <br />
-	Double-click PHP Manager <br />
-	Click “Enable or disable an extension” <br />
-	Enable: php_imap.dll <br />
-	Enable: php_intl.dll <br />
-	Enable: php_opcache.dll <br />
-	Refresh the osTicket site in your browser, observe the changes. You will notice only ACPU and Zend OPache extensions are the only disabled extensions now which aren't necessary for the purposes of this lab. 
</p>
<p>
<img src="https://i.imgur.com/60LHuLn.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/iklOHQH.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/u6cHs0h.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/J7Rrcmw.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>
15. Rename: ost-config.php <br />
From: C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php <br />
To: C:\inetpub\wwwroot\osTicket\include\ost-config.php
</p>
<p>
<img src="https://i.imgur.com/je3AmAc.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/pQWwC4c.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>
16. Rename: ost-config.php <br />
-	Disable inheritance -> Remove All inherited permissions from this object <br />
-	New Permissions -> Everyone -> All
</p>

<p>
<img src="https://i.imgur.com/NZZ1dqD.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/xQ7wU3s.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/zjk4rfB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/WedX6ux.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/nboqahp.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>  
17. From the “osTicket-Installation-Files” folder, install HeidiSQL <br />
-	Open Heidi SQL <br />
-	Create a new session, root/root <br />
-	Connect to the session <br />
-	Create a database called “osTicket”
</p>
<p>
<img src="https://i.imgur.com/CV4S9qW.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/sKuLNyG.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/WlziC2w.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/GbNtx03.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/w89LCAG.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>  
<img src="https://i.imgur.com/rVH11y2.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>  
<img src="https://i.imgur.com/Xdy1rys.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>  
</p>
<br />

<p> 
18. Continue Setting up osTicket in the browser. As this is a lab you can just enter fake info and credentials for testing purposes like I have below. <br />
-	MySQL Database: osTicket <br />
-	MySQL Username: root <br />
-	MySQL Password: root <br />
-	Click “Install Now!”
</p>
<p>
<img src="https://i.imgur.com/9Pxm3gQ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>  
</p>
<br />

<p> 
19. Congratulations, hopefully it is installed with no errors! <br />
-	Help desk login page: http://localhost/osTicket/scp/login.php <br />
-	End Users osTicket URL: -	http://localhost/osTicket/  <br />
</p>
<p>
<img src="https://i.imgur.com/EzqJe1q.png" height="80%" width="80%" alt="Disk Sanitization Steps"/> 
</p>
<br />

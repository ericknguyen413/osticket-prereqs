<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
This tutorial outlines the prerequisites and installation of the open-source help desk ticketing system osTicket.<br />


<h2>Video Demonstration</h2>

- ### [YouTube: How To Install osTicket with Prerequisites](https://www.youtube.com)

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)

<h2>Project Walkthrough</h2>

First, let's create a virtual machine:

![image](https://github.com/user-attachments/assets/21ba53af-d727-448f-a6c0-51a83cf87ef9)

The virtual machine has been created:

![image](https://github.com/user-attachments/assets/07355011-8adc-449f-9960-72681f1187ba)

Next, let's log in the virtual machine by using RDP (Remote Desktop Protocol)

![image](https://github.com/user-attachments/assets/bc622b2f-dd49-428b-9ea1-ae244e4948a9)

On the virtual machine, I will now download osTicket files through the Microsoft Edge browser:

Here's the <a href="https://drive.usercontent.google.com/download?id=1b3RBkXTLNGXbibeMuAynkfzdBC1NnqaD&export=download&authuser=0)">link</a> to the download files of osTicket.

![image](https://github.com/user-attachments/assets/81bc6428-695f-43b3-be0b-f7f75bf020ad)

![image](https://github.com/user-attachments/assets/f63bf82b-982a-4e4a-8897-d0a4b2b194c2)

Once I've connected to the VM I will install and enable IIS (Internet Information Servies) by going to Control Panel> Programs> Turn Windows Features On or Off> Internet Information Services and enable it then World Wide Web Services> Application Development Features and enable CGI:

![image](https://github.com/user-attachments/assets/d7b839ad-380f-4e99-b5a0-d28669ef6b77)

I can test that the web server installed correctly by typing in the loopback IP (127.0.0.1) in the internet browser and this page should load:

![image](https://github.com/user-attachments/assets/e96ede41-86af-4d95-b2ef-4a750ab6434b)

Now I need to install PHP manager for IIS Setup:

![image](https://github.com/user-attachments/assets/2a4067ea-20be-481d-84b5-f2d0aa880a31)

Install IIS URL Rewrite Module:

![image](https://github.com/user-attachments/assets/76fff78f-17fd-45de-a028-ce452075c2d9)

Once those have installed I will create a PHP directory on the C drive:

![image](https://github.com/user-attachments/assets/383f4fe6-3636-46a9-8823-58f2d467304f)

Now I'll download PHP and extract the zip file in the PHP directory I just made:

![image](https://github.com/user-attachments/assets/9befcf81-8115-43c9-82ff-b1f1a3ae42b6)

![image](https://github.com/user-attachments/assets/abeabd21-ce23-43f0-96f7-204505f083ef)

Download Microsoft Visual C++:

![image](https://github.com/user-attachments/assets/997e7acb-dd36-4483-a007-6efcf0c01010)

Download MySQL:

![image](https://github.com/user-attachments/assets/5f617264-c988-446d-927b-47e022e24a3f)

Next, I have to setup the login credentials and I'll write them down just so I remember, since this is only a project. Do not write passwords down in real life:
Open IIS as an admin:
Next go to PHP Manager> Register new PHP version and then select the file shown:
Go back to osticketVM Home and hit Restart under Manage Server on the right side:
Next I'll download osTicket and copy the upload file to the wwwroot file in the inetpub directory:
Rename upload file to osTicket:
Reload IIS and restart the server as I did before, then click Browse *80 (http) on the right side:
This page should open:
Notice some extensions are not enabled. I'll enable a few of those in IIS. Go to Sites> Default Web Site> osTicket Click PHP Manager> Enable or disable an extension. Enable php_imap.dll, php_intl.dll, and php_opcache.dll:
Note the changes here:
Next browse in file explorer to C drive> osTicket> include> ost-sampleconfig.php and remove the "sample" from the name:
Right-click on ost-config.php> Properties> Security> Advanced> Disable Inheritance> Remove all inherited permissions from this object:
Click on the add buton to add permissions to the file> Select a principle> type "everyone"> Check> OK> check all permissions> OK> apply> OK:
Hit continue on the osTicket web page in the browser and fill out the set up page:
Before database set up we'll have to connect the database using HeidiSQL. Install HeidiSQL from setup links:
In HeidiSQL click New> Username = root> Password = mySQL password from mySQL setup> Open:
In HeidiSQL right click Unnamed> Create> New Database> Name it osTicket> OK. Then continue to fill out the database portion of osTicket setup. Click Install Now when done.:
Last steps, for clean up go to C drive> inetpub> wwwroot> osTicket and look for the setup file and delete it. Then go to C drive> inetpub> wwwroot> osTicket> include right click on ost-config.php> Properties> Security> Advanced> Select Everyone and click edit> only leave Read & Execute and Read checked, then apply settings:



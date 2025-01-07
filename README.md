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

![image](https://github.com/user-attachments/assets/14615a72-eac2-44f8-9d4b-4ce15b77d4da)

Open IIS as an admin:

![image](https://github.com/user-attachments/assets/330e1d06-283d-43af-bf6f-57d587e1d4fc)

Next go to PHP Manager> Register new PHP version and then select the file shown:
![image](https://github.com/user-attachments/assets/47a9ffed-e060-4100-9a15-48e66a8e2d6d)

Go back to osticketVM Home and hit stop under Manage Server on the right side:

![image](https://github.com/user-attachments/assets/1ed48429-7865-40fa-bc91-f2055c142d28)

Then hit start under Manage Server on the right side:

![image](https://github.com/user-attachments/assets/f4c8b04b-3f50-4350-95d3-ca7c1ca2de49)

Next I'll download osTicket and copy the upload file to the wwwroot file in the inetpub directory:

![image](https://github.com/user-attachments/assets/e4b14bd6-68f3-4095-bb28-fbd09e7cfcee)

Rename upload file to osTicket:

![image](https://github.com/user-attachments/assets/959787f7-5853-4ebd-ae02-2c309cc661af)

Stop IIS and Start the server as I did before, then click Browse *80 (http) on the right side:

![image](https://github.com/user-attachments/assets/45086c12-0f7c-4de8-8f2e-d48c85f96b6f)

![image](https://github.com/user-attachments/assets/7b819bc4-75ed-4d69-ada4-5a87a2f59ce4)

This page should open:

![image](https://github.com/user-attachments/assets/f03bca4f-0985-4593-8740-e798d4a08337)

Notice some extensions are not enabled. I'll enable a few of those in IIS. Go to Sites> Default Web Site> osTicket Click PHP Manager> Enable or disable an extension. Enable php_imap.dll, php_intl.dll, and php_opcache.dll:

![image](https://github.com/user-attachments/assets/ccd2953c-0cd8-4533-8cd6-3ecef8dd7600)

Note the changes here:

![image](https://github.com/user-attachments/assets/3b41aac2-fa96-4880-848c-1268f6e5db56)

Next browse in file explorer to C drive> osTicket> include> ost-sampleconfig.php and remove the "sample" from the name:

![image](https://github.com/user-attachments/assets/be981826-ccc9-4fee-b33a-f212dfa5df26)

Right-click on ost-config.php> Properties> Security> Advanced> Disable Inheritance> Remove all inherited permissions from this object:

![image](https://github.com/user-attachments/assets/fe30a37a-8d9a-4827-8cc5-4deee4dfdb63)

Click on the add buton to add permissions to the file> Select a principle> type "everyone"> Check> OK> check all permissions> OK> apply> OK:

![image](https://github.com/user-attachments/assets/2818d9b2-ae04-498a-ae58-9ed9ef32b9c6)

Hit continue on the osTicket web page in the browser and fill out the set up page:

![image](https://github.com/user-attachments/assets/ea0bb2ab-fc87-495e-8449-deaf0f4bc9b0)

Before database set up we'll have to connect the database using HeidiSQL. Install HeidiSQL from setup links:

![image](https://github.com/user-attachments/assets/5296ca6f-2c9a-4a09-a485-b6f12ee85dd7)

In HeidiSQL click New> Username = root> Password = mySQL password from mySQL setup> Open:

![image](https://github.com/user-attachments/assets/b3aa0e3c-a798-4af0-93a2-eb5367a46069)

In HeidiSQL right click Unnamed> Create> New Database> Name it osTicket> OK. Then continue to fill out the database portion of osTicket setup. Click Install Now when done.:

![image](https://github.com/user-attachments/assets/a6e2e408-5597-4a17-90e4-85018e248644)

![image](https://github.com/user-attachments/assets/e708c363-214f-4918-9768-3a11bf4739e9)

![image](https://github.com/user-attachments/assets/09d54ad7-0768-458f-ab76-90455dc1fd62)

<h2>osTicket Installed!</h2>

<b>osTicket is now installed and ready for use! In the next project I will walk you through how to configure agents, their permissions and access, users, and more!  </b>

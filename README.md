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

Once I've connected to the VM I will install and enable IIS (Internet Information Servies) by going to Control Panel> Programs> Turn Windows Features On or Off> Internet Information Services and enable it then World Wide Web Services> Application Development Features and enable CGI:


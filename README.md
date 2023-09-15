<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Installation</h1>
This tutorial outlines the installation of the open-source help desk ticketing system osTicket.<br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)

<h2>Installation Steps</h2
                   
Install / Enable IIS in Windows WITH
CGI and Common HTTP Features.  Open Control panel and click  turn on windows features on/off <img src="https://imgur.com/OyCd2oz.png"/>
World Wide Web Services -> Application Development Features ->
[X] CGI
[X] Common HTTP Features
AND IIS Management Console
Internet Information Services -> Web Management Tools -> IIS Management Console
	[X] IIS Management Console


Download and install (PHPManagerForIIS_V1.5.0.msi) https://drive.google.com/file/d/1RHsNd4eWIOwaNpj3JW4vzzmzNUH86wY_/view?usp=share_link

Download and install the Rewrite Module (rewrite_amd64_en-US.msi) https://drive.google.com/file/d/1tIK9GZBKj1JyUP87eewxgdNqn9pZmVmY/view?usp=share_link

Create the directory C:\PHP

Download PHP 7.3.8 (php-7.3.8-nts-Win32-VC15-x86.zip)https://drive.google.com/file/d/1snNMtLdCOpMtkCyD4mvl9yOOmvVIp9fP/view?usp=share_link and unzip the contents into C:\PHP
!! ATTENTION !!
If this appears, choose to “Keep” the file: ![image](https://github.com/KendrickChe/osticket-prereqs/assets/144974559/d9396a64-d88f-4aba-a914-7e094058920d) ![image](https://github.com/KendrickChe/osticket-prereqs/assets/144974559/92072e09-f592-4c81-9a5b-57e5c9556f8b)


If you are still having trouble downloading PHP 7.3.8, please try downloading and installing Google Chrome and doing it from within there. 

Download and install VC_redist.x86.exe.https://drive.google.com/file/d/1s1OsGF3-ioO0_9LYizPRiVuIkb3lFJgH/view?usp=share_link

Download and install MySQL 5.5.62 (mysql-5.5.62-win32.msi)https://drive.google.com/file/d/1_OWh9p7VQLcrB0q_V7qT8yHl0xo5gv7z/view?usp=share_link
Typical Setup ->
Launch Configuration Wizard (after install) ->
Standard Configuration ->

Open IIS as an Admin

Register PHP from within IIS

Reload IIS (Open IIS, Stop and Start the server)

Install osTicket v1.15.8
Download osTicket https://drive.google.com/file/d/1_OWh9p7VQLcrB0q_V7qT8yHl0xo5gv7z/view?usp=share_link
Extract and copy “upload” folder to c:\inetpub\wwwroot
Within c:\inetpub\wwwroot, Rename “upload” to “osTicket”

Reload IIS (Open IIS, Stop and Start the server)

Go to sites -> Default -> osTicket
On the right, click “Browse *:80”

Note that some extensions are not enabled
Go back to IIS, sites -> Default -> osTicket
Double-click PHP Manager
Click “Enable or disable an extension”
Enable: php_imap.dll
Enable: php_intl.dll
Enable: php_opcache.dll
Refresh the osTicket site in your browse, observe the changes

Rename: ost-config.php
From: C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php
To: C:\inetpub\wwwroot\osTicket\include\ost-config.php 
![image](https://github.com/KendrickChe/osticket-prereqs/assets/144974559/e7cb31c6-6234-4140-ac78-3cd081229264)


Assign Permissions: ost-config.php
Disable inheritance -> Remove All
New Permissions -> Everyone -> All ![image](https://github.com/KendrickChe/osticket-prereqs/assets/144974559/e33e0344-7169-4cbd-9559-256f5a48c2e2) ![image](https://github.com/KendrickChe/osticket-prereqs/assets/144974559/41705862-066d-40ab-ad3d-945f26176193) ![image](https://github.com/KendrickChe/osticket-prereqs/assets/144974559/84ba9914-c3a1-42b2-9b76-98a3f654128c) 




Continue Setting up osTicket in the browser (click Continue)
Name Helpdesk
Default email (receives email from customers)

Download and install HeidiSQL. https://docs.google.com/document/d/1WovrX2DaS9xkfaSr4LXyB4YnnWpXIgPCMMbbfgHmGVw/edit
Open Heidi SQL
Create a new session, root/Password1 example whatever you put here is used to finish setting up osTicket
Connect to the session
Create a database called “osTicket” ![image](https://github.com/KendrickChe/osticket-prereqs/assets/144974559/39450c3a-1f0f-47f8-b4bd-d7ff2b11b7f7)
Continue Setting up osticket in the browser
MySQL Database: osTicket
MySQL Username: root (example)
MySQL Password: Password1 (example)
Click “Install Now!”

Congratulations,
Browse to your help desk login page: http://localhost/osTicket/scp/login.php
End User http://localhost/osTicket/

Clean up
Delete: C:\inetpub\wwwroot\osTicket\setup
Set Permissions to “Read” only: C:\inetpub\wwwroot\osTicket\include\ost-config.php
![image](https://github.com/KendrickChe/osticket-prereqs/assets/144974559/b1a8408d-20db-4a9b-9c8c-fe09f51f2769) ![image](https://github.com/KendrickChe/osticket-prereqs/assets/144974559/275e497f-d79e-4e8d-ac1e-bc3aeb3511eb)



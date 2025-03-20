<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket: Prerequisites and Installation</h1>
This tutorial provides a step-by-step guide for setting up the prerequisites and installing osTicket, an open-source help desk ticketing system. It details the configuration of a Windows 10 virtual machine in Azure, installation of necessary software like IIS, PHP Manager, and MySQL, and the final setup of osTicket. The guide ensures a comprehensive installation process for users setting up osTicket in a virtualized environment.<br />


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)

<h2>Operating Systems Used </h2>

- Windows 10 or Mac OS</b> 

<h2>List of Prerequisites</h2>

- IIS
- PHP Manager
- Rewrite Module
- VC_redistx86
- MySQL 5.5.62
- Heidi SQL



<h1>Creating Our Resource, Network, & Virtual Machines/ Connecting to Remote Desktop </h1> 

<br>
<br>

<h2>&#9312; Create a Virtual Machine on Azure</h2>


- To begin this step, first search for Virtual Machines and hit create; Make sure to click on Azure Virtual Machine 

- For the resource group, click on "Create New" so that you can make a new resource group. I named it "osTicket" it can be any name you choose -> Click "OK"
  
- For the name of the virtual machine, I have chosen "osTicket-VM"
  
- I have selected my region, "East US 2," and I have retained the options as displayed. Furthermore, I have chosen the image for this virtual machine as "Windows 10 Pro, version 22H2 - x64 Gen2"


<br>

pic 1:40

<br>

- When determining the appropriate size, it is essential to ensure that there are a minimum of 2 virtual CPUs (VCPUs) allocated. Additionally, it is advisable to document your username and password in a secure location for future reference

<br>

pic 2:21

<br>

- In Networking this time, we will allow the Virtual Machine to create its Virtual network

- Please ensure that the licensing agreement presented is checked, and then proceed by selecting "Review + Create," followed by "Create"

- Then the virtual machine will be created

<br>
<h2>&#9313; Find your VM's public IP address</h2>

pic 3:45

<br>

- First, copy the public IP address from the newly created virtual machine

- Then Open Remote Desktop 



<img width="276" alt="Screenshot 2025-01-13 at 1 12 03 PM" src="https://github.com/user-attachments/assets/f63c13d1-7408-4d1c-9568-884061a5557e" /> 

<br>

<h2>&#9314; Connect to your VM using the Microsoft Remote Desktop app</h2>


<img width="287" alt="Screenshot 2024-09-19 at 12 28 36 PM" src="https://github.com/user-attachments/assets/fc0b9142-ae88-4315-9a78-b2649a841455">

<br>

- Go to the App Store on Mac and download this app. We are going to use the Microsoft Remote Desktop app to connect to our Windows Server virtual machine

<br>

<img width="601" alt="Screenshot 2025-01-12 at 8 00 32 PM" src="https://github.com/user-attachments/assets/a82711e7-80c0-4aa3-9bea-3e06a4c41c91" />

- Open Microsoft Remote Desktop --> Click on the Plus icon and click on add Pc --> Name it "osTicket" in "Friendly Name:" ---> paste the public IP address in the PC name ---> press add to connect (if needed put in the username and password u made to connect)


- After that you should be able to connect to your newly created virtual machine 

<br>


<h3>- Resetting Passwords </h3>

pic 4:29

<br>

- If you are confident that you have entered all the information accurately, yet you are still unable to establish a remote desktop connection to the virtual machine, the issue may be related to the password.

- To reset your password, please access the Azure portal. Select your Windows virtual machine, navigate to the "Help" section, and click "Reset password." Enter your new password and then select "Update." This process should effectively resolve the issue.


<h1>Installation Steps</h1>

<br>
<br>

<h2>&#9312; Professional Installation & Configuration of osTicket from Scratch  </h2>

<br>

pic 7:18

<br>

- Download the osTicket installation files here
  <https://drive.google.com/uc?export=download&id=1b3RBkXTLNGXbibeMuAynkfzdBC1NnqaD>

- After the instillation Click Folder -> go to downloads there should be a folder named "osTicket-Installation-Files"             
                                                                                                            
pic 7:52                                                                                                        
<br>                                                                                                          
           

- We are going to unzip them onto the desktop and then into a folder called "osTicket-Installation-Files"
  
- Drag the folder from downloads to the Desktop

<br>

pic 07:58

<br>

- Right Click on the folder -> Click on Extract all

- Make sure that it is going towards the Desktop\osTicket-Installation-Files -> then hit "Extract"

<br>









<h2>&#9313; Enable IIS </h2>

<br>

- IIS, or Internet Information Services, is a web server platform that operates on virtual machines (VMs). It will be utilized to host and serve the osTicket application effectively.

- 

9:55


 <br> 

Enable and expand the following features:</p>
<img width="400" src="https://imgur.com/DdrwoVU.png">

 [X] Internet Information Services
[X] Web Management Tools 
[X] IIS Management Console 
[X] World Wide Web Services  
[X] Application Development Features 
[X] CGI
[X] Common HTTP Features
<br>
Click okay and the features should be enabled.
<br>
 NOTE: To test if the changes were applied succesfully, type "127.0.0.1" on your browser and this page below should appear. </strong></p>
<img width="900" src="https://imgur.com/nqv8e9h.png">
<br> <br>
<h3>&#9317; Download and Install PHP Manager</h3>
<Download and install PHP manager from the <a href="https://drive.google.com/drive/u/2/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6"> installation files </a>(PHPManagerForIIS_V1.5.0.msi) 
 <br>
<img width="386" src="https://imgur.com/DbU0lk6.png">

<br>
<h3>&#9318; Download and Install the Rewrite Module</h3>
<p> Download and install the rewrite module (rewrite_amd64_en-US.msi) from the <a href="https://drive.google.com/drive/u/2/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6"> installation files </a> </p>
<p><img width="386" alt="rewrite module" src="https://imgur.com/dM5GWpc.png"></p>
<h3>&#9319; Create a new directory</h3>
<p>Proceed to File Explorer and create the directory in "C:" naming the new folder "PHP" </p>
<img width="647" alt="PHP" src="https://imgur.com/AP3sxXs.png">
<br>
<br>
<h3>&#9320; Download and install PHP 7.3.8 </h3>
<p> Download and install php-7.3.8-nts-Win32-VC15-x86.zip from the <a href="https://drive.google.com/drive/u/2/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6"> installation files </a> and extract the contents into the newly created PHP folder </p>
<img width="720" alt="PHP zip" src="https://imgur.com/AgERChE.png">
<br>
<h3>&#9321; Download and install VC_redist.x86.exe </h3>
<br>
<h3>&#9322; Download and install MySQL 5.5.62 </h3>
<p> Download and install MySQL 5.5.62 (mysql-5.5.62-win32.msi) from the <a href="https://drive.google.com/drive/u/2/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6"> installation files </a>  and select the following configurations:</p>
<p> Typical Setup -> Launch Configuration Wizard after install -> Standard Configuration
</p>
<br>
<img width="420" alt="mysql" src="https://imgur.com/UXdU64D.png">
<br>
<h3>&#9323; Launch IIS as an administrator</h3>
<p> Search IIS in the Windows search bar, then right click and select "Open as Administrator"</p>
<br>
<h3>&#9324; Register PHP Manager </h3>
<br>
<img width="720" alt="PHP registration 2" src="https://imgur.com/BEmvAuY.png">

<br>
<br>
<p><strong> NOTE: Registration will require you to provide a path to "php-cgie.exe". Lead it to the PHP folder previously created and you will find the file "php-cgi"
</strong></p>
<br>
<img width="700" alt="PHP path " src="https://imgur.com/Pewjk2r.png">

<br>
<p>
</p> 
<h3>&#9325; Restart the IIS server</h3>
<p> The restart button can be found on the right side of the window under Actions -> Manage Server.</p>
<br>
<img width="623" alt="Restart IIS" src="https://imgur.com/KHl2nlC.png">
<br>
<br>
<h3>&#9326; Download and install osTicket</h3>
<p> Download and install osTicket v1.15.8 from the installation files and extract the contents to c:\inetpub\wwwroot </p>
<br>
<img width="547" alt="inetpub" src="https://imgur.com/KqDNCsS.png">
<br>
<br>
<p> Within c:\inetpub\wwwroot, Rename “upload” to “osTicket”</p>
<br>
<h3>&#9327; Restart the IIS Again.</h3>
<img width="623" alt="Restart IIS" src="https://imgur.com/KHl2nlC.png">
<br>
<br>
<h3>&#9328; Launch osTicket </h3>
<p>Under Connections in IIS, VM-osTicket -> Sites -> Default Web Site -> osTicket</p>
<img width="623" alt="osTicket" src="https://imgur.com/bgZrJzV.png">
<p></p>
<p><strong>NOTE: Click on osTicket</strong></p>

<h3>&#9329; Select Browse *80 to launch osTicket</h3>
<p> On the right side of the window, under Actions -> Manage Folder -> Click on Browse *:80 (http) </p>
<img width="623" alt="browse80" src="https://imgur.com/yiQjEcK.png">
<br>
<br>
<p><strong>This should lead to osTicket opening in a separate Windows broswer</strong>.</p>
<br>
<br>
<img width="664" alt="osTicket browser" src="https://imgur.com/yOa0Jy8.png">
<br>
<br>
<h3>&#9330; Enable extensions</h3>
<p>Open IIS -> PHP Manager -> Select "Enable or Disable Extension". </p>
<p>Enable the following extensions:</p>
<p>[X]Enable: php_imap.dll</p>
<p>[X]Enable: php_intl.dll</p>
<p>[X]Enable: php_opcache.dll</p>
<img width="273" alt="php enable 2" src="https://imgur.com/8QO0yIO.png">
<br>
<br>
<h3>&#9331; Refresh osTicket</h3>

<p>After refreshing your web browser on osTicket, notice how more features are now available to use.</p>
<img width="608" alt="OSticket changes" src="https://imgur.com/bdJ05kP.png">
<br>
<br>

<h3>&#12881; Rename ost-config.php</h3>

<p> Under c:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php, rename "ost-sampleconfig.php" to "ost-config.php"</p>
<img width="527" alt="ostconfig rename" src="https://imgur.com/yP1YTT0.png">
<br>
<br>

<h3>&#12882; Change ost-config.php permissions</h3>

<p>Change ost-config.php permissions (right click)</p>
<p>Properties -> Security -> Advance -> Disable Inheritance</p> 
<p>Select "remove all inherited permissions" and add everyone as a principal. Select all boxes to ensure all permissions are granted. </p>
<img width="571" alt="Permissions" src="https://imgur.com/mANNCMT.png">

<h3>&#12883; Continue osTicket installation</h3>

<p> Continue through osTicket filling out only the first half of the page to this point.</p>
<img width="611" alt="osticket signup" src="https://imgur.com/m7WratO.png">
<br>
<br>
<p><strong>NOTE: The database credentials we'll fill out later.</strong> </p>
<br>

<h3>&#12884; Download and install Heidi SQL from the installation files</h3>

<p>Open Heidi SQL and create a new session. Make sure to fill in the username as root and create a password. After filling up your credentials now click open and a new session should show up.
</p>

<h3>&#12885; Create new database </h3>

<p>On the left side of the window, right click on "Unnamed" and create a new database named "osTicket".</p>
<img width="512" alt="SQL" src="https://imgur.com/AbElzBn.png">
<br>
<br>

<h3>&#12886; Finish osTicket Sign-Up</h3>

<p>Revert back to your osTicket browser and fill out the incomplete credentials.</p>
<img width="375" alt="osticket final signup" src="https://imgur.com/B2A1SMM.png">


<h3>&#12887; Finalize osTicket installation</h3>

<p>Click install and osTicket should begin to setup. </p>


<br>
<br>
<h1>Congratulations!! &#127881; you just installed osTicket</h1>



































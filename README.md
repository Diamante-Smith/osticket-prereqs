<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>


<h1>osTicket: Prerequisites and Installation</h1>
This tutorial provides a step-by-step guide for setting up the prerequisites and installing osTicket, an open-source help desk ticketing system. It details the configuration of a Windows 10 virtual machine in Azure, the installation of necessary software like IIS, PHP Manager, and MySQL, and the final setup of osTicket. The guide ensures a comprehensive installation process for users setting up osTicket in a virtualized environment.<br />


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)

<h2>Operating Systems Used </h2>

- Windows 10 or Mac OS 

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

<br>

- To begin this step, first search for Virtual Machines and hit Create; Make sure to click on Azure Virtual Machine 

- For the resource group, click on "Create New" so that you can make a new resource group. I named it "osTicket" It can be any name you choose -> Click "OK"
  
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

<br>

pic 3:45

<br>

- First, copy the public IP address from the newly created virtual machine



- Then Open Remote Desktop 

<br>

<img width="276" alt="Screenshot 2025-01-13 at 1 12 03 PM" src="https://github.com/user-attachments/assets/f63c13d1-7408-4d1c-9568-884061a5557e" /> 

<br>


<h2>&#9314; Connect to your VM using the Microsoft Remote Desktop app</h2>


<br>

<img width="287" alt="Screenshot 2024-09-19 at 12 28 36 PM" src="https://github.com/user-attachments/assets/fc0b9142-ae88-4315-9a78-b2649a841455">

<br>

- Go to the App Store on Mac and download this app. We are going to use the Microsoft Remote Desktop app to connect to our Windows Server virtual machine

<br>

<img width="601" alt="Screenshot 2025-01-12 at 8 00 32 PM" src="https://github.com/user-attachments/assets/a82711e7-80c0-4aa3-9bea-3e06a4c41c91" />

<br>

- Open Microsoft Remote Desktop --> Click on the Plus icon and click on add Pc --> Name it "osTicket" in "Friendly Name:" ---> paste the public IP address in the PC name ---> press add to connect (if needed put in the username and password u made to connect)


- After that, you should be able to connect to your newly created virtual machine 

<br>

<h3>- Resetting Passwords </h3>

<br>

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

- To get all the files needed for osTicket, go to osTicket documentation and collect them all to install them 1 at a time
  
<https://docs.osticket.com/en/latest/Getting%20Started/Installation.html>

- You can instead also download the osTicket installation files here provided by Josh Madakor, our instructor
  
<https://drive.google.com/uc?export=download&id=1b3RBkXTLNGXbibeMuAynkfzdBC1NnqaD>
  

- After the installation, Click Folder -> go to downloads there should be a folder named "osTicket-Installation-Files"             
                                                                                                            
pic 7:52                                                                                                        
<br>                                                                                                                  

- We are going to unzip them onto the desktop and then into a folder called "osTicket-Installation-Files"
  
  
- Drag the folder from downloads to the Desktop

<br>

pic 07:58

<br>

- Right-click on the folder -> Click on Extract all


- Make sure that it is going towards the Desktop\osTicket-Installation-Files -> then hit "Extract"



<br>


<h2>&#9313; Enable IIS </h2>

<br>

- IIS, or Internet Information Services, is a web server platform that operates on virtual machines (VMs), it will be utilized to host and serve the osTicket application effectively.

<br>

pic 9:30

<br>

- Open a new tab and type in 127.0.0.1 in the web browser Nothing will happen; you will receive a page that cannot be reached

- 127.0.0.1 This address refers to the computer itself, If you try to run it and if you have a web server running on the computer, then a default webpage should be loaded

 <br> 

pic 9:55

<br>

- Open Control Panel -> Under programs, click on "Uninstall a program"

<br>

pic 10:21

<br>

- Click on "Turn Windows features on or off" -> Check the box that says "Internet Information Services" and expand that folder

<img width="376" alt="13" src="https://github.com/user-attachments/assets/489920cc-fae1-4930-8713-4ecaf8be4c8e" />
  

- We also have to install CGI as well since osTicket depends on this program as well

<br>

pic 10:40

<br>

- Expand on "World Wide Web Services" -> Expand "Application Development Features" -> Click on "CGI" -> Click on "OK" and wait a few minutes for it all to install

<br>


<img width="793" alt="15" src="https://github.com/user-attachments/assets/09c9262b-093e-42b0-8a5d-faa039ef56ae" />


<br>

- Once it is finished, click on close go back to the webpage and load 127.0.0.1



- Here will be the default webpage for IIS


<br> 



<h2>&#9314; Download and Install PHP Manager</h2>

<br>

- From the osTicket-Installation-Files folder, We will install PHP manager for IIS
  

- PHP is like a web server language where osTicket runs on PHP, so for osTicket to run, you need this installed
  

<br>

pic 13:20 

<br>

- go into the osTicket-Installation-Files folder -> Click on PHP manager

<br>

pic 13:40

<br>

- Click Next

<br>

pic 13:42

<br>

- Click I Agree, then Next

<br>

pic 13:47

<br>

- Say yes to everything and install it -> Click Close

<br>

pic 14:00

<br>

<h2>&#9315; Download and Install the Rewrite Module</h2>

<br>

- In the same folder, we will install the Rewrite module, another requirement for osTicket -> Double-click it and press Install


<h2>&#9316; Create a New Directory</h2>
  

- Next, we are gonna create a directory on the C drive called PHP "C:\PHP"  


<br>

pic 14:47

<br>

- Right-click on the folder on your start menu -> Click on File Explorer, and another folder should be opened to be used as well

<br>

pic 14:59

<br>

- Go to the C:\ Drive We are going to make a folder -> Right-click on Windows (C:) drive -> Hit New -> go to Folder -> name it "PHP"




- From the “osTicket-Installation-Files” folder, unzip this file PHP 7.3.8 (php-7.3.8-nts-Win32-VC15-x86.zip) into the “C:\PHP” folder

<br>

pic 15:37

<br>

- First, Double-click on the PHP file that will be unzipped, Here are the actual language files



- Right-click on this and press Extract all

<br>

pic 15:41

<br>

- Before pressing Extract at the top where it says browse, type in "C:\PHP" -> then hit Extract
  

- After the extraction, you will see in the C:\ Drive the PHP folder that was created plus other things that were extracted inside of it   
  

- Basically, we are putting the PHP files the osTicket is going to use on the C:\ Drive

<br>


<h2>&#9317; Download and install VC_redist.x86.exe </h2>
  

<br>

pic 16:55

<br>

- We are going to install the "VC redistributable file" -> Double-click the file -> make sure to press yes 

<br>


<h2>&#9318; Download and install MySQL 5.5.62 </h2>


<br>

pic 17:06

<br>

- MySQL is a database that osTicket uses to store all the data in, like user accounts, ticketing information, etc

- It's something that's on the backend and needs to be there for us to get to work in this field

- Download and install MySQL Server 5.5.62 (mysql-5.5.62-win32.msi) 
<https://drive.google.com/file/d/1_OWh9p7VQLcrB0q_V7qT8yHl0xo5gv7z/view?usp=share_link>


<br>

pic 17:20


<br>


- When choosing Setup type, click on "Typical" -> Press Install -> Click "Yes"
-> Wait for that to finish installing -> Once complete, check mark where it says
"Launch" so the wizard can be launched -> Click on Finish -> Then click on "Yes"
to allow the app to make changes


<br>

pic 17:52


<br>

- Press "Next" -> Choose "Standard Configuration" -> Press "Next" -> Leave everything as is and press "Next"


<br>

pic 18:06


<br>

- For this part, make sure you DO NOT mess this one up

- For new root password, just type in the word "root" for both to keep everything simple for this project, write this down on a notepad as well for later

- Click Next, then Execute on the 2 check-marked bubbled options that will automatically appear



<br>


<h2>&#9319; Launch IIS as an administrator</h2>

<br>


pic 20:22

<br>

- We are going to open IIS as an Admin


- Search IIS in the Windows search bar, then right-click and select "run as Administrator"

<br> 


<br>

<h2>&#9320; Register PHP Manager </h2>

<br>


pic 20:51

<br>

- We are gonna be registering PHP from within IIS

- So we are making the web server aware of the existence of PHP on the computer and telling it where it is


<br>


pic 21:11
  
<br>


- Open the PHP manager that we installed -> Click on register a new PHP version and browse to it by clicking on the 3 dots on the right side to browse


<br>

pic 21:14
  
<br>

- Once the folder shows up, click on "Windows (C:) A.K.A the C: Drive" -> Click on the PHP folder -> When you see php.cgi that is the only executable binary for PHP -> Double click it, and then click OK




<br>


<h2>&#9321; Stop and Restart the IIS server</h2>


<br>

pic 21:48
  
<br>

- Under "Connections" located on the left side, click on "osticket-vm"

- Then on the right side under "Actions" Click on "Stop"

- You could also right-click on "osticket-vm", then click on "Stop" to get the same results

- Give it a moment to stop, then right-click on "osticket-vm" and click on "Start"

<br>


<h2>&#9322; Download and install osTicket</h2>

<br>

pic 22:49
  
<br>

- Go back to the osTicket installation files folder

- Right-click on the file name osTicket-v1.15.8 -> Click "Extract All" and wait for it to finish, during the process, you will see another folder pop up at the top with the same name

<br>

pic 23:22
  
<br>

- Open that folder up, which will contain 2 other folders as well

- Open another File Explorer window -> Click Windows (c:) -> Click inetpub -> Click wwwroot

- "wwwroot" is the root of the web server

- Copy the Upload folder into the wwwroot folder -> Rename upload to osTicket with no spaces or anything, just exact


<br>
 

<h2>&#9323; Restart the IIS Again</h2>

<br>

pic 25:06
  
<br>

- Type and open up "Internet Information Services (IIS) Manager, remember to run as an administrator
  
- right-click on "osticket-vm", then click on "Stop" -> wait for it to stop, then right-click on it again and press "Start" for it to begin

<br>

<h2>&#9324; Launch osTicket </h2>

<br>

pic 25:44
  
<br>

- To launch osTicket under "Connections" located on the left side, expand "osticket-vm" with the down arrow 

- Expand "sites" -> Expand "Default Web site" -> Click on "osTicket"

- On the right side, click on Browse *80 to launch osTicket

- * If osTicket didn't load for you normally then that would indicate that you did something wrong and would have to delete your Virtual Machine and do the steps over but more precise


<br>

<h2>&#9325; Enable Extensions </h2>

<br>

pic 27:58
  
<br>

- Some of the Extensions are not enabled

<h2>&#9326; Refresh osTicket</h2>

<p>After refreshing your web browser on osTicket, notice how more features are now available to use.</p>
<img width="608" alt="OSticket changes" src="https://imgur.com/bdJ05kP.png">
<br>
<br>

<h2>&#9327; Rename ost-config.php</h2>

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



































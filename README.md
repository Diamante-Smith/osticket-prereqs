<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>


<h1>osTicket: Prerequisites and Installation</h1>
This tutorial provides a step-by-step guide for setting up the prerequisites and installing osTicket, an open-source help desk ticketing system. It details the configuration of a Windows 10 virtual machine in Azure, the installation of necessary software like IIS, PHP Manager, and MySQL, and the final setup of osTicket. The guide ensures a comprehensive installation process for users setting up osTicket in a virtualized environment.<br />


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)
- osTicket

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

- * If osTicket didn't load for you normally, then that would indicate that you did something wrong and would have to delete your Virtual Machine and do the steps over, but more precisely


<br>

<h2>&#9325; Enable Extensions </h2>

<br>

pic 28:44
  
<br>

- Some of the Extensions are not enabled
 
- Re-open IIS -> go to "sites" -> go to "Default Web Site" -> click on "osTicket"

- Double-click "PHP Manager" -> Under PHP Extensions, click on Enable or Disable an extension


<br>

pic 27:58
  
<br>

- Look for and enable these 3 extensions:

- php_impap.dll, This extension enables IMAP, POP3, and NNTP email functions in PHP. It’s used when your app (like osTicket) needs to connect to and read emails from a mailbox, such as fetching tickets from an email inbox.

- php_intl.dll is the PHP extension for Internationalization (Intl). It provides tools for formatting dates, times, numbers, currencies, and handling text in different languages and locales.

- Finally, php_opcache.dll is a tool that speeds up PHP by caching compiled scripts in memory. This reduces server load and makes apps like osTicket run faster.

<br>

pic 30:08
  
<br>


<h2>&#9326; Rename ost-config.php/ Assign Permissions to it</h2>

<br>

- Go to file explorer -> Click Windows (c:) -> Click inetpub -> Click wwwwroot -> Click osTicket

- Click the "include" folder -> Scroll down to "ost-sampleconfig.php" -> Right-click it and press "rename"

- Name it exactly ost-config.php DO NOT mess this step up

- Now you have to assign permissions specifically for OS ticket so you're able to make changes to this file on the backend 

<br>

pic 31:16
  
<br>

- Right-Click on the file "ost-config.php"-> go to "Properties" -> Click on "Security" -> - Click "Advanced" -> Click "Disable Inheritance", this will remove all the current permissions -> Click "Remove all inherited permissions from this object"

- To add new permissions, click on "ADD" -> Click "Select a principal" -> At the bottom, where it says "Enter the object name," type in "everyone" for this project, then hit OK

- Press/ checkmark "Full control" -> Press Apply -> hit OK and press OK again

<br>

<h2>&#9327; Continue osTicket installation </h2>

<br> 

pic 32:31
  
<br>

- Go back to the osTicket website -> Click on "Continue"

- For "Helpdesk Name," name it whatever you like -> The email portion shouldn't matter

- For Admin user, put your name -> The Admin User email address has to be different from the Default Email at the top
  
- Copy down the username and password; I'm gonna go with "adminuser" for the username and "Password 1" for the Password

  

<br> 

pic 34:07
  
<br>

- For this step, we will be creating a database specifically for osTicket and then provide the credentials for it

- Go back to the homescreen -> Right click the files and click on File Explorer -> Click on Desktop

- Open up the "osTicket-Installation-Files"
             

<br>


<h2>&#9328; Download and install HeidiSQL from the installation files</h2>

<br> 

pic 34:32
  
<br>

- "HeidiSQL" is an application that allows us to make a connection to our database and configure and do some stuff in there

- Double click the HeidiSQL file -> Once you open that up -> keep clicking through the file by pressing "Next"

-  Make sure to check mark launch HeidiSQL and finish -> Press skip


- With HeidiSQL, we are going to make a connection to our database and then set up a database for osTicket to use

<br>



<h2>&#9329; Create new database </h2>

<br> 

pic 35:08
  
<br>

- For this step, we are going to make a connection to our database and set up a database for osTicket to use

- Click new -> In user type in "root", the password will also be "root" as well -> Click on Open

- This opened a connection to our database

- Right click on where it says "Unnamed" -> Go to create new -> Then click on "Database"

- Type in the name exactly, osTicket -> Click "ok"

<br>

<h2>&#9330; Finalize osTicket installation</h2>

<br> 

pic 36:25
  
<br>

- Go back to the browser and go to the Database settings, like the osTicket set up

- Under MySQL Database, type in "osTicket"


- Under MySQL Username, type in "root" and for the password type in "root" -> Click "install now" to finalize everything


<br>

<h3>Congratulations!! &#127881; you just installed osTicket</h3>

<br> 



<h1> Post-installation Setup</h1>

<br>
<br>

<h2> &#9312; Acknowledge the Agent vs Admin Panel then Configure Roles </h2>

<br>

pic 01:52
  
<br>

- If you log in, you can see 2 different panels

- The Sysadmin Panel lets you configure a bunch of settings on the backend for osTicket

- The Agent Panel is if you're like a helpdesk worker and working on tickets

- For the lab, we will go back and forth between the 2

<br>

pic 03:26
  
<br>

- Roles are like teams that group permissions together and give specific people access to those permissions.

- Go to the Admin Panel or make sure you are in the Admin panel to verify, look at the top right portion, and if you see Agent Panel, then you are currently in the Admin Panel

- Click on Agents -> Click Roles -> The various roles are assigned distinct levels of access, each tailored to specific responsibilities. This structure ensures clarity regarding who has access to particular resources, thereby minimizing confusion.

<br>

pic 03:43

<br>

- If we click on the "View" Role -> Then click on "permissions" -> You will notice this role doesn't have anything checkmarked

- But go back to "roles" -> Click on the "Expanded Access" role -> Click on

'permissions' only certain things are checked

- Go back to roles -> Click on "All Access" to verify that everything is checked

 
<br>

pic 04:44

<br>

- You can create\ define your own roles

- Click on "Agents" -> Click on "Roles" -> Click "Add New Role" -> you can name it "Supreme Admin"

- Click on "Permissions" and checkmark everything -> Click on "Tasks" and checkmark everything to let be capable of doing everything

- Click on "Knowledgebase" and checkmark "Premade" as well -> after that is over, click on "Add Role"; this will solidify our new role for "Supreme Admin"

<br>

pic 05:55

<br>

- Next will be diving into "Departments," which is for ticket visibility, for instance, you can assign the Networking department a ticket so that only they should be able to look at it

- Make sure you're in the "Admin Panel" -> Click on "Departments" -> Click on "Add New Department"

- Under the settings for Parent, keep it as "Support" -> Name it "SysAdmins" -> For type, make it public

- For the rest of the settings, you can choose to keep them as is, or you can configure them to your liking

- Click on "Create Dept"

<br>

pic 07:30

<br>

- For teams, it's a group of people from different departments

- Make sure you're in the Admin panel -> Click Agent, then Teams

- Press Add New Team

- Name: put online banking and leave the rest settings as default -> Click on "Create Team"

<br>

<h2> &#9313; Allow end users the ability to create tickets on their own</h2>


<br>

pic 08:10

<br>

- With this setting, it allows people to create tickets even though they are not registered in the system yet

- Go to the Admin panel -> Click "Settings" at the top -> Click "Users" -> * For this important step, make sure to uncheck "Registration Required"

<br>

<h2> &#9314; Configure Agents</h2>

<br>

pic 09:03

<br>

- Agents are the actual workers

- In the Admin panel, click on "Agents" -> Click on "Add New Agent"

- Type in "Jane Doe" for first and last name -> Email address type in "Jane@lognpacific.com"

- For Username type in "jane", don't forget to write down the username and password for later

- Click on "Set Password."


<br>

pic 10:21

<br>

- At the top, left click on "Access" to see what lies in there

- Under the primary Department section, click on "Sysadmins" -> Under
- "Role," we will make Jane Doe a Supreme Admin and have access to everything

- Under assigned Teams, put her in Online Banking


<br>

pic 11:03

<br>

- Go back to Agents, we will be creating another person

- Click on "Agents" -> Click "Add New Agent" -> Type in "John Doe"

- For the fake email, type in "john@lognpacific.com" -> Username will be "john"

- His access once you click on "Access" under "Primary Department", click on "Support" -> For Role, click on "View Only" for this lab

- Under "Permissions," leave everything as is -> Finally, click on "Create"

<br>

<h2> &#9315; Set Passwords</h2>

<br>

pic 12:03

<br>

- *Go to Jane to see if you can set their password

- Click on "Set Password" -> Uncheck once where it says "Send the agent a password reset email" -> That should allow you to create your password

- For both Jane and John, I typed in "Password1" as my password for them

- Uncheck where it says "Require password change at next login" and click on update

- Then do the same steps for John

<h2> &#9316; Create a User</h2>

<br>

pic 13:34

<br>

- Go to the "Agent Panel" -> Click on "Users" -> Click "Add User"

- Type in the fake, made-up email "karen@lognpacific.com"

- For Full name type "Karen" -> Click on "Add User" -> don't forget to write down the passwords and users for later to remember


<br>

<h2> &#9316; Configure SLA</h2>

<br>

pic 14:38

<br>
  
- Just to remember, SLA's are service level agreements, it's how much time you have to do some specific task, whether it's to respond to a ticket or completing a ticket, and more

- Go back to the Admin panel -> Click on Manage -> Click on SLA -> Click on "Add New SLA Plan"


- We are going to make 3, Sev A for a really bad problem, Sev B for a slightly less bad problem, and Sev C for even something less bad

<br>

pic 15:23

<br>

- In the new SLA plan, type in "Sev-A" for name, for status, press "Active"

- Grace period, which is the number of hours after a ticket is created that it will be automatically marked as overdue

- We will place a 1 in hours, and for schedule select 24/7, so for example, the ticket needs to be responded to in 1 hour -> after that, click on "Add Plan"

<br>

pic 16:44

<br>

- Click on "Add New SLA Plan" -> Type in "Sev-B" for name -> keep the status as "Active"

- For the grace period, make it 4hrs -> for the schedule, make it 24/7 -> Then press "Add plan"

<br>

pic 17:06

<br>

- Click on "Add New SLA Plan" -> Type in "Sev-C" for name -> keep the status as "Active"

- For the grace period, make it 8hrs -> for the schedule, make it normal business hrs Mon-Fri -> Then press "Add plan"

<h2> &#9316; Configure Help Topics</h2>

<br>

pic 17:57

<br>

- Go to Admin panel -> Manage -> Help Topics -> Click on "Add new help topic"

- For Topic type in "Business Critical Outage" -> Status select Active -> Type press "Public"

- For parent topic select "Report a Problem" -> Click on "Add Topic"

<br>

pic 18:30

<br>

- We are going to make more, so again, click on "Add new help topic"

- Type in for topic "Personal Computer Issues" -> Status press "Active" -> The type will be
"Public"

- For parent topic select "Report a Problem" -> Click on "Add Topic"

<br>

pic 18:51

<br>

- Click on "Add new help topic"

- Type in for topic "Equipment Request" -> Status press "Active" -> The type will be
"Public"

- For parent topic select "General Inquiry" -> Click on "Add Topic"

<br>

pic 19:16

<br>

- Click on "Add new help topic"

- Type in for topic "Password Reset" -> Status press "Active" -> The type will be
"Public"

- For parent topic select "Report a Problem" -> Click on "Add Topic"

<br>

pic 19:38

<br>

- Click on "Add new help topic"

- For this last one, type in for topic "Other" -> Status press "Active" -> The type will be "Public"

- For parent topic select "General Inquiry" -> Click on "Add Topic"

<br>

pic 01:30

<br>

- http://localhost/osTicket/scp/login.php
Copy and paste this URL into the browser on your virtual lab, not your actual browser

- Log in with your Admin User credentials

<br>

pic 02:01

<br>

- For this one, we are gonna go to the Admin panel -> Click on "Agents" at the top -> Click on "Departments"

* - Click on the "Maintenance" Department -> Status click on "Disabled" -> For type you will press Public
 
- For everything else, leave it as is and click on "save changes"

<br>

pic 02:45

<br>

- Go back to agents, then click on Departments -> Click on SYSAdmins

- Make sure "Parent" is set to "Top Level Department," then scroll down to the bottom and click on "Save changes"

<br>

pic 03:12

<br>

- For this step, we will be making a ticket as an end user

- Log out of the current user you are using in osTicket

- Press the browser for a new tab and paste this URL in it http://localhost/osTicket

<br>

pic 03:24

<br>

- Click on "Open a New Ticket", our end user will be Karen

- Type in the email address "karen@lognpacific.com" -> put in whatever random phone number

- For the Help topic, select "Report a problem" -> for the issue summary type in "Entire mobile/online banking system is down

- Under that type in "My employees are reporting that users are no longer able to access the online banking portal, and the ones who can occasionally access it cannot log in

- Click on "Create Ticket"

<br>

pic 05:12

<br>  

- Press the browser for a new tab and paste this URL into it because we are going to log in as John http://localhost/osTicket/scp/login.php

- If you have to change the password if prompted, go ahead and do so, just make sure to write it down

- You will notice your first ticket, we will be observing the stuff that is in this ticket

<br>

pic 08:22

<br>

- Look at the top portion of the ticket, its priority was defaulted to normal 

- The department is now "support" -> The SLA is defaulted to "Default SLA" -> Assigned to is "Unassigned"

- Usually, a new ticket will have lots of default settings on it and not have a user assigned to it unless the end user has the ability to assign it to a help desk admin or something

<br>

pic 10:42

<br>

- We are going to update the SLA plan for this ticket as its a major issue

- Click on "Default SLA" -> Click on "Sev-A" -> Type in "wide impact, customers unable to do online banking" for the description

- Click on "Update"

<br>

pic 11:28

<br>

- Click on "Help topic: report a problem"

- Under Help Topic, under the drop-down, click on "Report a Problem/ Business Critical Outage"

- For the description type in "No Customer is able to access online banking" -> Click on "Update"

- Once you refresh the ticket as you scroll down, you will see the history of the ticket, who worked on it when, and what changed

<br>

pic 12:28

<br>

- Click on "Assigned To", you will see assignees you can designate the ticket to, such as individuals or teams

- Click on "Online Banking" -> In the description type, "the customer is not able to access the online banking portal assigning to online banking team"

- Then Click "Assign"

- Some permissions were made in the beginning so certain people could not see specific tickets just a heads up, if you wanted to have certain users not be able to see certain tickets

<br>

pic 14:51

<br>

- Log out of John's account, then log in as Jane

- Click on the online/ banking ticket that shows up when you log in

- Click on "Online Banking" -> click on Jane Doe under assignee, as we are going to assign it to Jane

- For the description type in "I'll be taking this ticket" -> Click on "Assign" -> now it's specifically assigned to Jane

<br>

pic 15:41

<br>

- Scroll down to the bottom of the ticket

- For the post reply, put in the description, "I suspect the problem might be related to the recent updates. We tested them sufficiently, but I'm going to look into it further and roll them back if I determine that was the cause."

- Click on "Post Reply"

- Whenever you reply to a thread in an email ticket, all the people subscribed to the ticket usually will get emails whenever something is updated or someone makes a comment

- And you can see a trail of replies/ activity that has been taking place to resolve an issue

<br>

pic 17:22

<br>

- We will act like we went to the back end and checked out online banking as Jane and figured that the problem was a recent update that was installed, then we uninstalled the update and rolled back the system, and that fixed the issue

- For the post reply, put in the description, "It was determined that the root cause was the recent update. We rolled it back, notified the vendor, and are waiting for a proper fix. Online banking should now be up and running.
        
- Click "Post reply" -> Go to the top, click on "Open" for the status, set the ticket to "Resolved

- To check previously closed tickets, you would have to sign in as the admin user, go to tickets, then closed, and click on yesterday or any of the previous days

<br>

pic 19:46

<br>

- Go back to the end-user portal to create a new ticket http://localhost/osTicket

- For the email address, since we made 2 end users, this one is for Ken, put in his email address "ken@lognpacific.com"

- Put in whatever random phone number -> For the Help topic, select "General inquiry / other"
  
- Click on "create Ticket" -> For the issue summary, type in "Accounting department needs Adobe upgrade"

- For the description type in "it looks like many people in the account department can't use their Adobe software"

- It's good to inspect before upgrading what the end user wants, because it could be a simple matter where they just don't have access to the software right now

<br>

pic 21:18

<br>

- We will log in as John to look at this new ticket

- Then we see the ticket come through from Ken -> Click on it

- When inspecting further on the customer to better understand what they want, it's best to email them, especially if their contact information is listed on their ticket

<br>

pic 22:51

<br>

- After gaining further information, to take the next course, you can click on the blue link next to SLA Plan

- We changed the SLA to Sev-C -> At the bottom, type in the description "Only 2 people unable to open Adobe Reader, Classifying as Sev-C since the impact isn't so bad

- Click on "Department" as we will be assigning it to the "Support Team"

- And next to "Assign to," click on the blue link on the pop-up up select "John Doe"

- In the "Post reply" description, type in "Customer states that only two people in the accounting department are unable to open and use Adobe Reader. Customer testing restart, will call back after lunch."

- Then click "Post Reply"

<br>

pic 24:46

<br>

- In the scenario, we wait for some hrs for the customer to reach back out to us, then we take lunch as time rolls on, and then Ken calls back, he restarted the computer, and everything is working again with no issues

- For the description reply, we make a note saying "customer states that a restart fixed the issue, closing out ticket."

- Then click "Post Reply"

<br>

pic 25:38

<br>

- Click on the ticket we just did -> And scroll down towards the bottom portion where it says "Post Internal Note"

- These are notes that the customers can't see             

- Always assume these notes will be looked at or can be viewed by a customer

- So please act professionally when writing an Internal note to your coworkers


<br>

pic 27:32

<br>

- Let's now go to status at the top and click on "Resolved"

- For the description, type in restart fixed the issue for both users -> Click on "Close"

<br>

pic 28:49

<br>

- For this last ticket, it will be discussing a problem with our laptop how it is not turning on

- http://localhost/osTicket, go to open a new ticket

- This ticket will be from Karen, Type in the email address "karen@lognpacific.com"

- Put in whatever random phone number

- For the Help topic, select "Report a problem/ personal computer issues" -> for the issue summary type in "CFO states he is unable to use laptop

- Under that type in  "laptop won't power on despite pressing the power button"

- Click on "Create Ticket"

<br>

pic 29:43

<br>

- If you're still logged in as John, then you can see the new ticket and click on it

- Set the priority to Emergency -> Then click on SLA and change that to Sev-B

- Underneath for the description type "May re-classify after getting more info", since the customer never told us basically if it's impacting a business, etc., other than himself

- Click on the link also next to "Assigned To" -> Choose John Doe as the assignee -> no need to make notes, and then click assign

<br>

pic 31:12

<br>

-










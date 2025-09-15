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

<img width="341" height="373" alt="Screenshot 2025-08-19 at 10 59 30 AM" src="https://github.com/user-attachments/assets/440cb77f-e92e-44cf-8902-33c7d6b5c1eb" />
<br>

<img width="613" height="677" alt="Screenshot 2025-08-21 at 4 42 47 PM" src="https://github.com/user-attachments/assets/ba43bbb0-f4e9-4b48-bdbe-96a3f0dcb80b" />


<br>


- To begin this step, first search for Virtual Machines and hit Create; Make sure to click on Azure Virtual Machine 

- For the resource group, click on "Create New" so that you can make a new resource group. I named it "osTicket" It can be any name you choose -> Click "OK"
  
- For the name of the virtual machine, I have chosen "osticket-vm"
  
- I have selected my region, "East US 2," and I have retained the options as displayed. Furthermore, I have chosen the image for this virtual machine as "Windows 10 Pro, version 22H2 - x64 Gen2"


<br>

<img width="301" height="250" alt="Screenshot 2025-08-19 at 11 12 54 AM" src="https://github.com/user-attachments/assets/4d29b907-06e2-414d-8377-29eae70a204c" />


<br>



- When determining the appropriate size, it is essential to ensure that there are a minimum of 2 virtual CPUs (VCPUs) allocated. Additionally, it is advisable to document your username and password in a secure location for future reference

<br>

<img width="587" height="654" alt="Screenshot 2025-08-19 at 11 28 46 AM" src="https://github.com/user-attachments/assets/0ac8ff97-6fb6-48d7-a17a-5bd8832044a6" />

<br>


- Username will be "labuser" and your password could be whatever you can remember

<br>

<img width="612" height="758" alt="Screenshot 2025-08-21 at 4 47 18 PM" src="https://github.com/user-attachments/assets/644d10ab-94e0-4cfd-8b45-093608d43973" />


<br>




- In Networking this time, we will allow the Virtual Machine to create its Virtual network

<br>

<img width="371" height="87" alt="Screenshot 2025-08-19 at 11 28 33 AM" src="https://github.com/user-attachments/assets/0bd471c2-9c5b-48bb-8bd8-6378b36b6287" />

<br>

<img width="568" height="113" alt="Screenshot 2025-08-21 at 4 56 51 PM" src="https://github.com/user-attachments/assets/353f3e53-f610-4435-a458-e18e0a09133d" />

<br>


- Please ensure that the licensing agreement presented is checked, and then proceed by selecting "Review + Create," followed by "Create"

- Then the virtual machine will be created

<br>

<h2>&#9313; Find your VM's public IP address</h2>

<br>

<img width="1135" height="81" alt="Screenshot 2025-08-21 at 5 01 43 PM" src="https://github.com/user-attachments/assets/c04f39b8-f788-4bde-8065-2f7c9063b59d" />


<br>

- First, copy the public IP address from the newly created virtual machine



- Then Open Remote Desktop 



<br>


<h2>&#9314; Connect to your VM using the Microsoft Remote Desktop app</h2>


<br>

<img width="287" alt="Screenshot 2024-09-19 at 12 28 36 PM" src="https://github.com/user-attachments/assets/fc0b9142-ae88-4315-9a78-b2649a841455">

<br>

- Go to the App Store on Mac and download this app. We are going to use the Microsoft Remote Desktop app to connect to our Windows Server virtual machine

<br>

<img width="601" alt="Screenshot 2025-01-12 at 8 00 32 PM" src="https://github.com/user-attachments/assets/a82711e7-80c0-4aa3-9bea-3e06a4c41c91" />

<br>

<img width="469" height="532" alt="Screenshot 2025-08-22 at 1 33 23 PM" src="https://github.com/user-attachments/assets/9294f458-955f-48b4-be16-1b97ece1acca" />

<br>

<img width="283" height="166" alt="Screenshot 2025-08-22 at 1 39 38 PM" src="https://github.com/user-attachments/assets/c90b6117-9491-4a68-a1f0-927fd8be7113" />

<br>



- Open Microsoft Remote Desktop --> Click on the Plus icon and click on add Pc --> Name it "osTicket" in "Friendly Name:" ---> paste the public IP address in the PC name ---> press add to connect (if needed put in the username and password u made to connect)


- After that, you should be able to connect to your newly created virtual machine 

<br>

<h3>- Resetting Passwords </h3>


<br>

- If you are confident that you have entered all the information accurately, yet you are still unable to establish a remote desktop connection to the virtual machine, the issue may be related to the password.

<br>

<img width="233" height="137" alt="Screenshot 2025-08-22 at 1 46 43 PM" src="https://github.com/user-attachments/assets/f5713205-ff29-4987-a3e4-b394ee5f7aa1" />

<br>

<img width="572" height="274" alt="Screenshot 2025-08-22 at 1 47 36 PM" src="https://github.com/user-attachments/assets/ede26243-3342-4f78-b465-498c8887b168" />

<br>

<img width="103" height="53" alt="Screenshot 2025-08-22 at 1 47 44 PM" src="https://github.com/user-attachments/assets/9c368088-8eb2-4172-8c09-5b1afe56b34c" />
<br>


- To reset your password, please access the Azure portal. Select your Windows virtual machine, navigate to the "Help" section, and click "Reset password." Enter your new password and then select "Update." This process should effectively resolve the issue. And it may take a few minutes to update
<br>

<h1>Installation Steps</h1>

<br>
<br>

<h2>&#9312; Professional Installation & Configuration of osTicket from Scratch  </h2>

- WE will be basically installing all the dependencies that are required for osTicket to work and run


- To get all the files needed for osTicket, go to osTicket documentation and collect them all to install them 1 at a time
  
<https://docs.osticket.com/en/latest/Getting%20Started/Installation.html>

- You can instead also download the osTicket installation files here, provided by Josh Madakor, our instructor

<br>

<img width="498" height="146" alt="Screenshot 2025-08-22 at 2 07 14 PM" src="https://github.com/user-attachments/assets/67a499c0-9906-4caa-9878-a6fe75b140d8" />

<br>

  
<https://drive.google.com/uc?export=download&id=1b3RBkXTLNGXbibeMuAynkfzdBC1NnqaD>

https://docs.google.com/document/d/1DyjX8LeVU98LjhXO2t2K2F0aHywI2N9GD57T3taO5qo/edit?tab=t.0

<br>

<img width="748" height="645" alt="Screenshot 2025-08-22 at 2 01 08 PM" src="https://github.com/user-attachments/assets/39e9a263-24a2-449e-a7e1-5c1d7c1cc736" />

<br>


- And don't forget to check the lab checklist, and also place that one in a separate window in Microsoft Edge, the browser in the virtual machine you made

<br>

<img width="1050" height="197" alt="Screenshot 2025-08-24 at 1 48 51 PM" src="https://github.com/user-attachments/assets/c1258eac-ee90-4f83-b70c-5c0f45eb8c63" />

<br>
<img width="775" height="436" alt="Screenshot 2025-08-24 at 1 50 15 PM" src="https://github.com/user-attachments/assets/d081d4ae-7349-4322-aa35-d8dfbfdf3e44" />
<br>
  
- After the installation, Click Folder -> go to downloads, there should be a folder named "osTicket-Installation-Files"             
                                                                                                            
                                                                                                      
<br> 
<img width="102" height="103" alt="Screenshot 2025-08-24 at 1 51 05 PM" src="https://github.com/user-attachments/assets/a6c1b9bf-9c69-4d07-b951-120be63787da" />

<br>
                                                                                                                 

- We are going to unzip them onto the desktop and then into a folder called "osTicket-Installation-Files"
  
  
- Drag the folder from downloads to the Desktop

<br>

<img width="212" height="123" alt="Screenshot 2025-08-24 at 1 51 32 PM" src="https://github.com/user-attachments/assets/dd920b72-3308-4732-974b-5b11f0a87ba6" />


<br>

- Right-click on the folder -> Click on Extract all

<br>
<img width="608" height="442" alt="Screenshot 2025-08-24 at 1 52 00 PM" src="https://github.com/user-attachments/assets/6f28c761-bb80-4907-8c18-5f7a53205b33" />

<br>
<img width="186" height="97" alt="Screenshot 2025-08-24 at 1 53 29 PM" src="https://github.com/user-attachments/assets/91a83cd0-dee1-49bc-8a3e-0bca728983e2" />
<br>


- Make sure that it is going towards the Desktop\osTicket-Installation-Files -> then hit "Extract"
  
- You can put the zipped file in the recycle bin

<br>
<img width="93" height="100" alt="Screenshot 2025-08-24 at 1 53 38 PM" src="https://github.com/user-attachments/assets/b3fa67e0-c4a7-4147-a8af-546ea2ea82ba" />
<br>
<img width="656" height="341" alt="Screenshot 2025-08-24 at 1 54 07 PM" src="https://github.com/user-attachments/assets/42add71e-a179-4a20-aad1-93f2ecff9796" />
<br>

- Everything was extracted into the new folder

<br>


<h2>&#9313; Enable IIS </h2>

<br>

- IIS, or Internet Information Services, is a web server platform that operates on virtual machines (VMs), it will be utilized to host and serve the osTicket application effectively.

<br>

<img width="623" height="669" alt="Screenshot 2025-08-24 at 1 54 50 PM" src="https://github.com/user-attachments/assets/c3d6da6c-8b85-4426-a816-b8f829e65c50" />


<br>

- Open a new tab and type in 127.0.0.1 in the web browser Nothing will happen; you will receive a page that cannot be reached

- 127.0.0.1 This address refers to the computer itself, If you try to run it and if you have a web server running on the computer, then a default webpage should be loaded

 <br> 

<img width="622" height="680" alt="Screenshot 2025-08-24 at 1 55 31 PM" src="https://github.com/user-attachments/assets/d70ec70f-7356-445b-abd7-12484ed23afc" />
<br>
<img width="180" height="66" alt="Screenshot 2025-08-24 at 1 55 57 PM" src="https://github.com/user-attachments/assets/a61631fe-7c91-4b21-9490-2cb6062cf95e" />

<br>

- Open Control Panel -> Under programs, click on "Uninstall a program"

<br>

<img width="190" height="59" alt="Screenshot 2025-08-24 at 1 56 35 PM" src="https://github.com/user-attachments/assets/5305780f-2220-49ec-8098-97dbed6d3b58" />

<br>
<img width="759" height="349" alt="Screenshot 2025-08-24 at 1 57 05 PM" src="https://github.com/user-attachments/assets/e45b2b0d-b53a-4ade-af03-20363073bb5e" />

<br>
<img width="231" height="66" alt="Screenshot 2025-08-24 at 1 57 45 PM" src="https://github.com/user-attachments/assets/3a1eea8a-27b2-45f7-ae48-08970f4cf276" />

<br>
<img width="281" height="214" alt="Screenshot 2025-08-24 at 2 00 37 PM" src="https://github.com/user-attachments/assets/3bf5694e-d829-49e6-add9-749b7488aa27" />
<br>


- Click on "Turn Windows features on or off" -> Check the box that says "Internet Information Services" and expand that folder
<br>

<img width="376" alt="13" src="https://github.com/user-attachments/assets/489920cc-fae1-4930-8713-4ecaf8be4c8e" />

<br>
<img width="649" height="448" alt="Screenshot 2025-08-24 at 2 01 44 PM" src="https://github.com/user-attachments/assets/cd9cc4a5-53a3-4805-8eee-01b427b8067a" />
<br>

  

- We also have to install CGI, as well, since osTicket depends on this program as well for part of the web server


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

<img width="796" height="360" alt="Screenshot 2025-08-24 at 2 05 04 PM" src="https://github.com/user-attachments/assets/690e9507-a6b9-4bd0-89bc-36015af75873" />


<br>

- go into the osTicket-Installation-Files folder -> Click on PHP manager

<br>

<img width="717" height="413" alt="Screenshot 2025-08-24 at 2 10 51 PM" src="https://github.com/user-attachments/assets/713dc22a-de5d-4445-a5e3-8c76142f1373" />


<br>

- Click Next

<br>

<img width="500" height="410" alt="Screenshot 2025-08-24 at 2 11 04 PM" src="https://github.com/user-attachments/assets/4427319b-921d-474e-a676-c138b53e9f8c" />


<br>

- Click I Agree, then Next

<br>

<img width="502" height="410" alt="Screenshot 2025-08-24 at 2 11 24 PM" src="https://github.com/user-attachments/assets/6ac0052d-c1d8-4357-a9d5-e7b31de5ccd1" />


<br>

- Say yes to everything and install it -> Click Close


<br>

<h2>&#9315; Download and Install the Rewrite Module</h2>

<br>
<img width="700" height="396" alt="Screenshot 2025-08-24 at 2 12 42 PM" src="https://github.com/user-attachments/assets/56120dcc-9808-4464-ad4b-9c9611f4b6eb" />
<br>

- In the same folder, we will install the Rewrite module, another requirement for osTicket -> Double-click it and press Install

<br>
<img width="494" height="391" alt="Screenshot 2025-08-24 at 2 13 45 PM" src="https://github.com/user-attachments/assets/8216bf35-cf7d-40b1-95c6-8a76569234b2" />
<br>

- Click on finish, and now that part is complete


<h2>&#9316; Create a New Directory</h2>
  

- Next, we are gonna create a directory on the C drive called PHP "C:\PHP"  


<br>

<img width="294" height="481" alt="Screenshot 2025-08-24 at 2 13 56 PM" src="https://github.com/user-attachments/assets/2631d7c3-a5be-4176-a792-87a5cc325ba3" />


<br>

- Right-click on the folder on your start menu -> Click on File Explorer, and another folder should be opened to be used as well

<br>

<img width="564" height="236" alt="Screenshot 2025-08-24 at 2 15 35 PM" src="https://github.com/user-attachments/assets/f02e56e1-95e0-417e-aa02-a9ff1c27f2d4" />

<br>
<img width="83" height="29" alt="Screenshot 2025-08-24 at 2 15 51 PM" src="https://github.com/user-attachments/assets/9148c1a2-1620-4c4e-8d2a-79154e472a60" />
<br>


- Go to the C:\ Drive We are going to make a folder -> Right-click on Windows (C:) drive -> Hit New -> go to Folder -> name it "PHP"

<br>
<img width="225" height="29" alt="Screenshot 2025-08-24 at 2 17 25 PM" src="https://github.com/user-attachments/assets/8ec94b0b-2f94-47d0-aefc-8fb931fddc2a" />
<br>


- From the “osTicket-Installation-Files” folder, unzip this file PHP 7.3.8 (php-7.3.8-nts-Win32-VC15-x86.zip) into the “C:\PHP” folder

<br>

<img width="423" height="579" alt="Screenshot 2025-08-24 at 2 19 50 PM" src="https://github.com/user-attachments/assets/8aa83d88-4e3d-40ca-bba8-780fa55ec6d9" />


<br>

- First, Double-click on the PHP file that will be unzipped, Here, inside the folder, are the actual language files

<br>

<img width="303" height="87" alt="Screenshot 2025-08-24 at 2 20 19 PM" src="https://github.com/user-attachments/assets/294b062e-f553-44fe-946b-34573d651f63" />
<br>


- Right-click on this and press Extract all

<br>

<img width="547" height="49" alt="Screenshot 2025-08-24 at 2 20 34 PM" src="https://github.com/user-attachments/assets/cfb98740-d001-4861-89ca-214fb5504f8d" />

<br>
<img width="306" height="279" alt="Screenshot 2025-08-24 at 2 21 02 PM" src="https://github.com/user-attachments/assets/236c7c8f-eeba-47b7-80ac-230953ef6d27" />

<br>
<img width="548" height="33" alt="Screenshot 2025-08-24 at 2 21 13 PM" src="https://github.com/user-attachments/assets/a334a24d-66f3-4dc0-9f94-62c0a42fdece" />

<br>




- Before pressing Extract at the top where it says browse, type in "C:\PHP" -> then hit Extract

<br>
<img width="351" height="247" alt="Screenshot 2025-08-24 at 2 22 17 PM" src="https://github.com/user-attachments/assets/2722b08d-b9f4-40cd-9470-0e7b39695dff" />

<br>
  

- After the extraction, you will see in the C:\ Drive the PHP folder that was created, plus other things that were extracted inside of it   
  

- Basically, we are putting the PHP files the osTicket is going to use on the C:\ Drive

<br>


<h2>&#9317; Download and install VC_redist.x86.exe </h2>
  

<br>

<img width="131" height="25" alt="Screenshot 2025-08-24 at 2 26 02 PM" src="https://github.com/user-attachments/assets/2d435276-a02c-4284-899a-e02cae014930" />


<br>
<img width="481" height="299" alt="Screenshot 2025-08-24 at 2 26 15 PM" src="https://github.com/user-attachments/assets/40986031-84d5-4445-8c4c-83902e1ef8fe" />

<br>
<img width="482" height="299" alt="Screenshot 2025-08-24 at 2 26 28 PM" src="https://github.com/user-attachments/assets/b05fb74c-c673-471b-95ee-8edb70197915" />

<br>


- We are going to install the "VC redistributable file" -> Double-click the file -> make sure to press yes 

<br>


<h2>&#9318; Download and install MySQL 5.5.62 </h2>


<br>

<img width="701" height="391" alt="Screenshot 2025-08-24 at 2 28 43 PM" src="https://github.com/user-attachments/assets/eae7e32e-76e7-4473-ba05-70987e04260b" />


<br>

- MySQL is a database that osTicket uses to store all the data in, like user accounts, ticketing information, etc

- It's something that's on the backend and needs to be there for us to get to work in this field

- Download and install MySQL Server 5.5.62 (mysql-5.5.62-win32.msi) 
<https://drive.google.com/file/d/1_OWh9p7VQLcrB0q_V7qT8yHl0xo5gv7z/view?usp=share_link>


<br>

<img width="495" height="386" alt="Screenshot 2025-08-24 at 2 29 01 PM" src="https://github.com/user-attachments/assets/700d053e-0069-4835-a2d2-7a64acd481cc" />


<br>

<img width="499" height="387" alt="Screenshot 2025-08-24 at 2 29 48 PM" src="https://github.com/user-attachments/assets/0efad866-726c-4e87-a121-72f0eb567cf1" />

<br>

<img width="497" height="388" alt="Screenshot 2025-08-24 at 2 30 11 PM" src="https://github.com/user-attachments/assets/67295444-9fb9-4826-993c-d9b80521e3ef" />

<br>

<img width="497" height="387" alt="Screenshot 2025-08-24 at 2 30 25 PM" src="https://github.com/user-attachments/assets/3e3691c6-108c-4cad-a937-c1b9722654c5" />

<br>




- When choosing Setup type, click on "Typical" -> Press Install -> Click "Yes"
-> Wait for that to finish installing -> Once complete, check mark where it says
"Launch" so the wizard can be launched -> Click on Finish -> Then click on "Yes"
to allow the app to make changes


<br>

<img width="501" height="383" alt="Screenshot 2025-08-24 at 2 33 11 PM" src="https://github.com/user-attachments/assets/7c79e556-769d-4f36-90e4-d6fce371fb9e" />

<br>

<img width="501" height="382" alt="Screenshot 2025-08-24 at 2 33 23 PM" src="https://github.com/user-attachments/assets/17f8c339-ebd4-41ae-9fcb-f3002d089e24" />

<br>



- Press "Next" -> Choose "Standard Configuration" -> Press "Next" -> Leave everything as is and press "Next"


<br>

<img width="502" height="384" alt="Screenshot 2025-08-24 at 2 34 22 PM" src="https://github.com/user-attachments/assets/cf11b2e2-4ce4-45a9-8b56-c4edf07e7746" />



<br>

- For this part, make sure you DO NOT mess this one up

- For new root password, just type in the word "root" for both to keep everything simple for this project, write this down on a notepad as well for later

<br>

<img width="500" height="383" alt="Screenshot 2025-08-24 at 2 35 24 PM" src="https://github.com/user-attachments/assets/fcb84673-336d-452a-954c-974557d67200" />

<br>

<img width="502" height="381" alt="Screenshot 2025-08-24 at 2 35 55 PM" src="https://github.com/user-attachments/assets/219e10c9-c022-4bea-b927-64fd0197dc5e" />

<br>





- Click Next, then Execute on the 2 check-marked bubbled options that will automatically appear



<br>


<h2>&#9319; Launch IIS as an administrator</h2>

<br>


<img width="747" height="316" alt="Screenshot 2025-08-24 at 2 36 40 PM" src="https://github.com/user-attachments/assets/f7749684-4e7f-49fe-98a8-597c06d3aa4b" />


<br>

- We are going to open IIS as an Admin


- Search IIS in the Windows search bar, then right-click and select "run as Administrator"

<br>

<img width="899" height="605" alt="Screenshot 2025-08-24 at 2 37 19 PM" src="https://github.com/user-attachments/assets/99e008ba-cf90-4fbb-b840-6856139b783f" />


<br> 



<h2>&#9320; Register PHP Manager </h2>

<br>


<img width="65" height="77" alt="Screenshot 2025-08-25 at 3 43 42 PM" src="https://github.com/user-attachments/assets/5aadaad2-0a51-49cc-9a0a-e919f7b16910" />


<br>

- We are gonna be registering PHP from within IIS

- So we are making the web server aware of the existence of PHP on the computer and telling it where it is


<br>


<img width="905" height="668" alt="Screenshot 2025-08-25 at 3 43 55 PM" src="https://github.com/user-attachments/assets/8c7fdf77-b421-4a45-b2bd-be7cec1a8204" />

  
<br>

<img width="734" height="289" alt="Screenshot 2025-08-25 at 3 44 21 PM" src="https://github.com/user-attachments/assets/380fa6e5-d6f4-4c19-8ddb-741a8c884c26" />

<br>



- Open the PHP manager that we installed -> Click on register a new PHP version and browse to it by clicking on the 3 dots on the right side to browse


<br>

<img width="580" height="207" alt="Screenshot 2025-08-25 at 3 50 32 PM" src="https://github.com/user-attachments/assets/d675276e-d2bd-456c-b620-865cb17726a3" />

  
<br>

<img width="509" height="221" alt="Screenshot 2025-08-25 at 3 50 44 PM" src="https://github.com/user-attachments/assets/8ed48b0b-826b-4df3-925d-e4d64d6a09c4" />

<br>


- Once the folder shows up, click on "Windows (C:) A.K.A the C: Drive" -> Click on the PHP folder -> When you see php.cgi that is the only executable binary for PHP -> Double click it, and then click OK




<br>


<h2>&#9321; Stop and Restart the IIS server</h2>


<br>

<img width="344" height="159" alt="Screenshot 2025-08-25 at 3 53 29 PM" src="https://github.com/user-attachments/assets/acbd1b73-ba19-427b-a01e-9dba83787c85" />

  
<br>

- Under "Connections" located on the left side, click on "osticket-vm"

- Then, on the right side under "Actions" Click on "Stop"

- You could also right-click on "osticket-vm", then click on "Stop" to get the same results

<br>

<img width="368" height="135" alt="Screenshot 2025-08-25 at 3 53 51 PM" src="https://github.com/user-attachments/assets/0ab8b88a-54b4-40bc-9c6a-d60b0b578757" />

<br>


- Give it a moment to stop, then right-click on "osticket-vm" and click on "Start"

<br>


<h2>&#9322; Download and install osTicket</h2>

<br>

<img width="249" height="98" alt="Screenshot 2025-08-25 at 4 13 01 PM" src="https://github.com/user-attachments/assets/002715ee-135b-492d-8cc3-227c27a69d31" />

  
<br>

<img width="583" height="424" alt="Screenshot 2025-08-25 at 4 13 18 PM" src="https://github.com/user-attachments/assets/49319409-8868-495d-98b0-0859cca7878a" />

<br>

<img width="123" height="29" alt="Screenshot 2025-08-25 at 4 15 39 PM" src="https://github.com/user-attachments/assets/096c081b-8fed-4eca-80b0-a7712fd16abb" />

<br>



- Go back to the osTicket installation files folder




- Right-click on the file name osTicket-v1.15.8 -> Click "Extract All" and wait for it to finish -> During the process, you will see another folder pop up at the top with the same name


<br>

<img width="84" height="22" alt="Screenshot 2025-08-25 at 4 18 09 PM" src="https://github.com/user-attachments/assets/ae061ae9-8936-4544-81f3-7e143d087ffd" />
  
<br>

<img width="85" height="28" alt="Screenshot 2025-08-25 at 4 18 19 PM" src="https://github.com/user-attachments/assets/3ee202e0-f749-4c38-9b28-0a4ef32031d9" />

<br>


- Open that folder up, which will contain 2 other folders as well

- Open another File Explorer window -> Click Windows (c:) -> Click inetpub -> Click wwwroot

- "wwwroot" is the root of the web server

- Copy the Upload folder into the wwwroot folder -> Rename upload to osTicket with no spaces or anything, just exact


<br>
 

<h2>&#9323; Restart the IIS Again</h2>

<br>

<img width="747" height="316" alt="Screenshot 2025-08-24 at 2 36 40 PM" src="https://github.com/user-attachments/assets/772eea10-a70b-43c0-a351-ac6145416a5d" />

  
<br>

<img width="344" height="159" alt="Screenshot 2025-08-25 at 3 53 29 PM" src="https://github.com/user-attachments/assets/7fd95253-b070-408e-8f00-20913cf55634" />

<br>

<img width="368" height="135" alt="Screenshot 2025-08-25 at 3 53 51 PM" src="https://github.com/user-attachments/assets/c5d5d01c-da5c-40f9-8df2-5df61044c5c4" />

<br>



- Type and open up "Internet Information Services (IIS) Manager, remember to run as an administrator
  
- right-click on "osticket-vm", then click on "Stop" -> wait for it to stop, then right-click on it again and press "Start" for it to begin

<br>

<h2>&#9324; Launch osTicket </h2>

<br>

<img width="200" height="152" alt="Screenshot 2025-08-25 at 4 21 57 PM" src="https://github.com/user-attachments/assets/8002a8a1-f540-4e40-ada5-b35b552bf7d6" />

  
<br>



- To launch osTicket under "Connections" located on the left side, expand "osticket-vm" with the down arrow 

- Expand "sites" -> Expand "Default Web site" -> Click on "osTicket"

<br>

<img width="200" height="73" alt="Screenshot 2025-08-25 at 4 22 06 PM" src="https://github.com/user-attachments/assets/98fac256-89e4-4614-a0bf-5bbfeb21b471" />

<br>

<img width="822" height="741" alt="Screenshot 2025-08-25 at 4 27 42 PM" src="https://github.com/user-attachments/assets/5d67c9bd-0c46-4962-9b11-532af8720132" />



- On the right side, click on Browse *80 to launch osTicket

- If osTicket didn't load for you normally, then that would indicate that you did something wrong and would have to delete your Virtual Machine and do the steps over, but more precisely


<br>

<h2>&#9325; Enable Extensions </h2>

<br>

<img width="200" height="152" alt="Screenshot 2025-08-25 at 4 21 57 PM" src="https://github.com/user-attachments/assets/590bf781-e3b1-4dad-986a-7940f4b05c17" />


<br>

<img width="278" height="634" alt="Screenshot 2025-08-25 at 4 29 50 PM" src="https://github.com/user-attachments/assets/62440e40-ce7b-43fd-a00d-232d241ebf22" />

  
<br>

- Some of the Extensions are not enabled
 
- Re-open IIS -> go to "sites" -> go to "Default Web Site" -> click on "osTicket"

- Double-click "PHP Manager" -> Under PHP Extensions, click on Enable or Disable an extension


<br>

<img width="237" height="46" alt="Screenshot 2025-08-25 at 4 30 29 PM" src="https://github.com/user-attachments/assets/b5833fa7-3fac-40b8-b002-5c51a70db24c" />

  
<br>

<img width="182" height="59" alt="Screenshot 2025-08-25 at 4 30 50 PM" src="https://github.com/user-attachments/assets/8af134f8-802a-4f2d-a9e8-4b2e6cf52375" />

<br>

<img width="201" height="51" alt="Screenshot 2025-08-25 at 4 31 24 PM" src="https://github.com/user-attachments/assets/0c7ae367-a684-499c-8e9f-b82fb6ad5ee3" />

<br>



- Look for and enable these 3 extensions:

- php_impap.dll, This extension enables IMAP, POP3, and NNTP email functions in PHP. It’s used when your app (like osTicket) needs to connect to and read emails from a mailbox, such as fetching tickets from an email inbox.

- php_intl.dll is the PHP extension for Internationalization (Intl). It provides tools for formatting dates, times, numbers, currencies, and handling text in different languages and locales.

- Finally, php_opcache.dll is a tool that speeds up PHP by caching compiled scripts in memory. This reduces server load and makes apps like osTicket run faster.

<br>

<img width="549" height="448" alt="Screenshot 2025-08-25 at 4 31 50 PM" src="https://github.com/user-attachments/assets/1eaf3590-6bbf-4716-b39e-32bfb63283d0" />

  
<br>

- Hit the "Refresh button" on the browser after enabling all the needed permissions

<br>

<h2>&#9326; Rename ost-config.php/ Assign Permissions to it</h2>

<br>

<img width="83" height="24" alt="Screenshot 2025-08-25 at 4 33 54 PM" src="https://github.com/user-attachments/assets/e262a357-038d-4b70-acd7-28ce760d3590" />

<br>

<img width="149" height="26" alt="Screenshot 2025-08-25 at 4 34 26 PM" src="https://github.com/user-attachments/assets/c5aedc7a-501f-420b-9d69-95c4767ad1d7" />

<br>

<img width="95" height="26" alt="Screenshot 2025-08-25 at 4 34 48 PM" src="https://github.com/user-attachments/assets/a5b333bf-e531-4fb5-a761-97c1fb9f4c8a" />

<br>




- Go to file explorer -> Click Windows (c:) -> Click inetpub -> Click wwwwroot -> Click osTicket

- Click the "include" folder -> Scroll down to "ost-sampleconfig.php" -> Right-click it and press "rename"

<br>

<img width="112" height="25" alt="Screenshot 2025-08-25 at 4 36 41 PM" src="https://github.com/user-attachments/assets/8d02f7f2-af49-4154-9d35-05bfc0bb1656" />

<br>


- Name it exactly ost-config.php DO NOT mess this step up

- Now you have to assign permissions specifically for OS ticket so you're able to make changes to this file on the backend 

<br>

<img width="107" height="33" alt="Screenshot 2025-08-25 at 4 37 03 PM" src="https://github.com/user-attachments/assets/00f2105b-6a23-4c7b-bc96-fa622340d281" />

  
<br>

<img width="354" height="406" alt="Screenshot 2025-08-25 at 4 37 25 PM" src="https://github.com/user-attachments/assets/0b2b448a-b378-4e4b-9da2-36b970723925" />

<br>

<img width="151" height="32" alt="Screenshot 2025-08-25 at 4 37 42 PM" src="https://github.com/user-attachments/assets/916dea29-73db-4f69-b5b7-8718426e3b31" />

<br>

<img width="391" height="44" alt="Screenshot 2025-08-25 at 4 37 53 PM" src="https://github.com/user-attachments/assets/150d33dc-c9fe-43ab-a7a8-f9e155b8d425" />

<br>




- Right-Click on the file "ost-config.php"-> go to "Properties" -> Click on "Security" -> - Click "Advanced" -> Click "Disable Inheritance", this will remove all the current permissions -> Click "Remove all inherited permissions from this object"

<br>

<img width="645" height="224" alt="Screenshot 2025-08-25 at 4 38 20 PM" src="https://github.com/user-attachments/assets/a8f401b2-1e1d-4e32-be38-b611bf471bcc" />

<br>

<img width="65" height="26" alt="Screenshot 2025-08-25 at 4 38 42 PM" src="https://github.com/user-attachments/assets/7a059954-1f35-4577-9b84-539840d68078" />

<br>

<img width="145" height="130" alt="Screenshot 2025-08-25 at 4 39 09 PM" src="https://github.com/user-attachments/assets/84fb5c0c-1567-40d5-8713-54f388f6d6f7" />

<br>

<img width="768" height="521" alt="Screenshot 2025-08-25 at 4 39 59 PM" src="https://github.com/user-attachments/assets/86611b48-466e-4e9d-9c31-d8167a95c91b" />

<br>

<img width="364" height="507" alt="Screenshot 2025-08-25 at 4 40 17 PM" src="https://github.com/user-attachments/assets/9dd13571-b701-4af8-9d41-b8077a0f08f7" />

<br>






- To add new permissions, click on "ADD" -> Click "Select a principal" -> At the bottom, where it says "Enter the object name," type in "everyone" for this project, then hit OK

- Press/ checkmark "Full control" -> Press Apply -> hit OK and press OK again

- osTicket now has full control to the configuration file

<br>

<h2>&#9327; Continue osTicket installation </h2>

<br> 

<img width="434" height="805" alt="Screenshot 2025-08-26 at 5 00 45 PM" src="https://github.com/user-attachments/assets/6642df0f-38b5-488c-80c4-63f2ef7877ab" />

  
<br>

- Go back to the osTicket website -> Click on "Continue"

- For "Helpdesk Name," name it whatever you like -> The email portion shouldn't matter

- For Admin user, put your name -> The Admin User email address has to be different from the Default Email at the top
  
- Copy down the username and password; I'm gonna go with "adminuser" for the username and "Password1" for the Password

  

<br> 

pic 34:07
  
<br>

- For this step, we will be creating a database specifically for osTicket and then provide the credentials for it

- Go back to the homescreen -> Right click the files and click on File Explorer -> Click on Desktop

- Open up the "osTicket-Installation-Files"
             

<br>


<h2>&#9328; Download and install HeidiSQL from the installation files</h2>

<br> 

<img width="193" height="26" alt="Screenshot 2025-08-26 at 5 46 49 PM" src="https://github.com/user-attachments/assets/2877a823-1787-4d82-b3ae-88f03769cb3b" />

  
<br>

- "HeidiSQL" is an application that allows us to make a connection to our database and configure and do some stuff in there

<br>

<img width="601" height="467" alt="Screenshot 2025-08-26 at 5 47 25 PM" src="https://github.com/user-attachments/assets/bb32e3f1-a5de-4291-8e1d-5d2b9d9fe474" />

<br>

<img width="596" height="465" alt="Screenshot 2025-08-26 at 5 47 54 PM" src="https://github.com/user-attachments/assets/ad5425b0-dc27-44e8-83fe-4183c8f1818b" />

<br>



- Double click the HeidiSQL file -> Once you open that up -> keep clicking through the file by pressing "Next"

<br>


<img width="599" height="464" alt="Screenshot 2025-08-26 at 6 36 20 PM" src="https://github.com/user-attachments/assets/e8a114ee-073d-45bb-b8a9-98291ee88616" />

<br>


-  Make sure to check mark launch HeidiSQL and finish -> Press skip


- With HeidiSQL, we are going to make a connection to our database and then set up a database for osTicket to use

<br>



<h2>&#9329; Create new database </h2>

<br> 

<img width="686" height="483" alt="Screenshot 2025-08-26 at 6 46 07 PM" src="https://github.com/user-attachments/assets/1b34a8f0-4ace-4c37-ad48-0b07f0721e42" />
  
<br>

- For this step, we are going to make a connection to our database and set up a database for osTicket to use


- Click new -> In user type in "root", the password will also be "root" as well -> Click on Open

- This opened a connection to our database

<br>

<img width="527" height="226" alt="Screenshot 2025-08-26 at 6 47 10 PM" src="https://github.com/user-attachments/assets/ed535b5b-baae-4b86-aec5-5bd3c223da66" />

<br>


- Right click on where it says "Unnamed" -> Go to create new -> Then click on "Database"

- Type in the name exactly, osTicket -> Click "ok"

<br>

<h2>&#9330; Finalize osTicket installation</h2>

<br> 

<img width="319" height="260" alt="Screenshot 2025-08-26 at 6 47 43 PM" src="https://github.com/user-attachments/assets/27347fdc-1aed-43f5-b689-10f60bdcdaa2" />

  

- Go back to the browser and go to the Database settings, like the osTicket setup

<br>

<img width="107" height="23" alt="Screenshot 2025-08-26 at 6 48 58 PM" src="https://github.com/user-attachments/assets/76bc790b-46be-4184-8b68-1d376a6147bc" />

<br>

- Under MySQL Database, type in "osTicket"

<br>

<img width="589" height="421" alt="Screenshot 2025-08-26 at 7 17 11 PM" src="https://github.com/user-attachments/assets/7fada424-f3e7-4985-aa66-3b5aad6137c2" />

<br>



- Under MySQL Username, type in "root" and for the password type in "root" -> Click "install now" to finalize everything

- All these tables were created within our osTicket database, a bunch of stuff it will use on the backend


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

- Here is the link to log in as the Admin, remember your password and Username to get in http://localhost/osTicket/scp/login.php

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

- You can create and define your own roles

- Click on "Agents" -> Click on "Roles" -> Click "Add New Role" -> you can name it "Supreme Admin"

- Click on "Permissions" and checkmark everything -> Click on "Tasks" and checkmark everything so they can be capable of doing everything

- Click on "Knowledgebase" and checkmark "Premade" as well -> after that is over, click on "Add Role"; this will solidify our new role for "Supreme Admin"

<br>

pic 05:55

<br>

- Next will be diving into "Departments," which is for ticket visibility, for instance, you can assign the Networking department a ticket so that only they should be able to look at it

- Make sure you're in the "Admin Panel" -> Click on "Departments" -> Click on "Add New Department"

- Under the settings for Parent, keep it as "Top Level Department" -> Name it "SysAdmins" -> For type, make it public

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

- At the top, left-click on "Access" to see what lies in there

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

<br>

<h2> &#9316; Create a User</h2>

<br>

pic 13:34

<br>

- Go to the "Agent Panel" -> Click on "Users" -> Click "Add User"

- Type in the fake, made-up email "karen@lognpacific.com"

- For Full name type "Karen" -> Click on "Add User" -> don't forget to write down the passwords and users for later to remember


<br>

<h2> &#9317; Configure SLA</h2>

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

<h2> &#9318; Configure Help Topics</h2>

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

<h1> Creating, Logging In, and Managing Initial Tickets </h1>

<br>
<br>

<h2> &#9312; Logging into the Admin Panel</h2>

<br>

pic 01:30

<br>

- http://localhost/osTicket/scp/login.php
Copy and paste this URL into the browser on your virtual lab, not your actual browser

- Log in with your Admin User credentials

<br>

<h2> &#9313; Modifying the Maintenance Department</h2>

<br>

pic 02:01

<br>

- For this one, if you didn't get to remove the maintenance department, I will show you how to delete it

 - We are gonna go to the Admin panel -> Click on "Agents" at the top -> Click on "Departments"

- Delete the "Maintenance Department" -> the checkmark box next to it -> Click on the "More" dropdown menu and select "Delete"

<br>

<h2> &#9314; Verifying the SYSAdmins Department</h2>

<br>

pic 02:45

<br>

- Go back to agents, then click on Departments -> Click on SYSAdmins

- Make sure "Parent" is set to "Top Level Department," then scroll down to the bottom and click on "Save changes"

<br>

<h2> &#9315; Creating a Ticket as an End User</h2>

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

<h2> &#9316; Logging In as John</h2>

<br>

pic 05:12

<br>  

- Press the browser for a new tab and paste this URL into it because we are going to log in as John http://localhost/osTicket/scp/login.php

- If you have to change the password if prompted, go ahead and do so, just make sure to write it down

- You will notice your first ticket, we will be observing the stuff that is in this ticket

<br>

<h2> &#9317; Reviewing Default Ticket Settings</h2>

<br>

pic 08:22

<br>

- Look at the top portion of the ticket, its priority was defaulted to normal 

- The department is now "support" -> The SLA is defaulted to "Default SLA" -> Assigned to is "Unassigned"

- Usually, a new ticket will have lots of default settings on it and not have a user assigned to it unless the end user has the ability to assign it to a help desk admin or something


<br>

<h2> &#9318; Updating SLA to Sev-A</h2>

<br>

pic 10:42

<br>

- We are going to update the SLA plan for this ticket as it's a major issue

- Click on "Default SLA" -> Click on "Sev-A" -> Type in "wide impact, customers unable to do online banking" for the description

- Click on "Update"

<br>

<h2> &#9319; Updating Help Topic</h2>

<br>

pic 11:28

<br>

- Click on "Help topic: report a problem"

- Under Help Topic, under the drop-down, click on "Report a Problem/ Business Critical Outage"

- For the description type in "No Customer is able to access online banking" -> Click on "Update"

- Once you refresh the ticket as you scroll down, you will see the history of the ticket, who worked on it when, and what changed

<br>

<h2> &#9320; Assigning certain tickets to a Team</h2>

<br>

pic 12:28

<br>

- Click on "Assigned To", you will see assignees you can designate the ticket to, such as individuals or teams

- Click on "Online Banking" -> In the description type, "the customer is not able to access the online banking portal assigning to online banking team"

- Then Click "Assign"

- Some permissions were made in the beginning so certain people could not see specific tickets just a heads up, if you wanted to have certain users not be able to see certain tickets

<br>

<h1> Reassigning, Updating, Following Up, and Closing Support Tickets </h1>
<br>
<br>
<h2> &#9312; Reassigning a ticket to Jane</h2>

<br>

pic 14:51

<br>

- Log out of John's account, then log in as Jane

- Click on the online/ banking ticket that shows up when you log in

- Click on "Online Banking" -> click on Jane Doe under assignee, as we are going to assign it to Jane

- For the description type in "I'll be taking this ticket" -> Click on "Assign" -> now it's specifically assigned to Jane

<br>

<h2> &#9313; Posting a Troubleshooting Reply</h2>

<br>

pic 15:41

<br>

- Scroll down to the bottom of the ticket

- For the post reply, put in the description, "I suspect the problem might be related to the recent updates. We tested them sufficiently, but I'm going to look into it further and roll them back if I determine that was the cause."

- Click on "Post Reply"

- Whenever you reply to a thread in an email ticket, all the people subscribed to the ticket usually will get emails whenever something is updated or someone makes a comment

- And you can see a trail of replies/ activity that has been taking place to resolve an issue

<br>

<h2> &#9314; Resolving the Ticket</h2>

<br>

pic 17:22

<br>

- We will act like we went to the back end and checked out online banking as Jane and figured that the problem was a recent update that was installed, then we uninstalled the update and rolled back the system, and that fixed the issue

- For the post reply, put in the description, "It was determined that the root cause was the recent update. We rolled it back, notified the vendor, and are waiting for a proper fix. Online banking should now be up and running.
        
- Click "Post reply" -> Go to the top, click on "Open" for the status, set the ticket to "Resolved

- To check previously closed tickets, you would have to sign in as the admin user, go to tickets, then closed, and click on yesterday or any of the previous days

<br>
<br>
<br>
<img width="960" height="877" alt="Screenshot 2025-09-03 at 12 45 26 PM" src="https://github.com/user-attachments/assets/72846783-097b-4d2e-af28-78e5eb558e23" />

<br>
<img width="961" height="339" alt="Screenshot 2025-09-03 at 12 45 37 PM" src="https://github.com/user-attachments/assets/45a8179b-4457-41c2-a35b-0892cb975db4" />

<br>

- This is the full conversation throughout the time of the ticket

<br>

<h2> &#9315; Creating a Ticket as Ken</h2>

<br>

pic 19:46

<br>

- Go back to the end-user portal to create a new ticket http://localhost/osTicket

- For the email address, since we made 2 end users, this one is for Ken, put in his email address "ken@lognpacific.com"

- Put in whatever random phone number -> For the Help topic, select "General inquiry / other"
  
- Click on "create Ticket" -> For the issue summary, type in "Accounting department needs Adobe upgrade"

- For the description type in "It looks like many people in the account department can't use their Adobe software"

- It's good to inspect before upgrading what the end user wants, because it could be a simple matter where they just don't have access to the software right now

<br>

<h2>&#9316; Reviewing Ken’s Ticket</h2>

<br>

pic 21:18

<br>

- We will log in as John to look at this new ticket

- Then we see the ticket come through from Ken -> Click on it

- When inspecting further on the customer to better understand what they want, it's best to email them, especially if their contact information is listed on their ticket

<br>

<h2>&#9317; Changing SLA & Assigning</h2>

<br>

pic 22:51

<br>

- After gaining further information, to take the next course of action, you can click on the blue link next to SLA Plan

- We changed the SLA to Sev-C -> At the bottom, type in the description "Only 2 people are unable to open Adobe Reader, Classifying as Sev-C since the impact isn't so bad

- Click on "Department" as we will be assigning it to the "Support Team" if it isn't already selected

- And next to "Assign to," click on the blue link on the pop-up, select "John Doe"

- In the "Post reply" description, type in "Customer states that only two people in the accounting department are unable to open and use Adobe Reader. Customer testing restart, will call back after lunch."

- Then click "Post Reply"

<br>

<h2> &#9318; Marking Ticket as Resolved </h2>

<br>

pic 24:46

<br>

- In the scenario, we wait for some hrs for the customer to reach back out to us, then we take lunch as time rolls on, and then Ken calls back, he restarted the computer, and everything is working again with no issues

- For the description reply, we make a note saying "Customer states that a restart fixed the issue, closing out the ticket."

- Then click "Post Reply"

<br>

<h2> &#9319; Adding Internal Notes </h2>

<br>

pic 25:38

<br>

- Click on the ticket we just did -> And scroll down towards the bottom portion where it says "Post Internal Note"

- Type in the title "Customer is very mad"

- For the description underneath, type in "Try to be empathetic with him."

- These are notes that the customers can't see             

- Always assume these notes will be looked at or can be viewed by a customer

- So please act professionally when writing an Internal note to your coworkers

<br>

<h2> &#9320; Finalizing a Resolution  </h2>

<br>

pic 27:32

<br>

- Let's now go to the status at the top and click on "Resolved"

- For the description, type in "Restart fixed the issue for both users" -> Click on "Close"
  
<br>
<br>
<img width="954" height="856" alt="Screenshot 2025-09-03 at 12 44 42 PM" src="https://github.com/user-attachments/assets/dcb72aed-23a0-4391-b71e-a0d65e5abdf6" />

<br>

- This is the full conversation throughout the time of the ticket

<h2> &#9321; Submitting New Ticket for Laptop Issue </h2>

<br>

pic 28:49

<br>

- For this last ticket, it will be discussing a problem with our laptop how it is not turning on

- http://localhost/osTicket, go to open a new ticket

- This ticket will be from Karen, Type in the email address "karen@lognpacific.com"

- Put in whatever random phone number

- For the Help topic, select "Report a problem/ personal computer issues" -> for the issue summary type in "CFO states he is unable to use laptop"

- Under that type in  "Laptop won't power on despite pressing the power button"

- Click on "Create Ticket"

<br>

<h2> &#9322; Investigating the Laptop Ticket </h2>

<br>

<img width="650" height="253" alt="Screenshot 2025-09-03 at 12 14 25 PM" src="https://github.com/user-attachments/assets/9c316a93-2404-4786-8ded-0e407b3158a8" />

<br>
<img width="647" height="252" alt="Screenshot 2025-09-03 at 12 15 42 PM" src="https://github.com/user-attachments/assets/cc7fc8d0-357e-4ca5-b7c6-118baf564a44" />

<br>
<img width="648" height="252" alt="Screenshot 2025-09-03 at 12 16 07 PM" src="https://github.com/user-attachments/assets/002ff441-d03d-42ab-8924-e6c24b71eafe" />

<br>

- If you're still logged in as John, then you can see the new ticket and click on it

- Set the priority to Emergency -> Then click on SLA and change that to Sev-B

- Underneath for the description type "May re-classify after getting more info", since the customer never told us basically if it's impacting a business, etc., other than himself

- Click on the link also next to "Assigned To" -> Choose John Doe as the assignee -> no need to make notes, and then click assign

<br>

<h2> &#9323; Resolving the Laptop Issue</h2>

<br>

<img width="734" height="85" alt="Screenshot 2025-09-03 at 12 41 30 PM" src="https://github.com/user-attachments/assets/0a4fd350-6e15-461c-a8ae-ae67c2e1548a" />


<br>

- And in this scenario, where you work, you will then take it upon yourself to contact the CFO in some way

- In this scenario, you went to the laptop, and it turned out that his charger was actually broken, and he couldn't charge it, so the battery died

- Go to the post reply and at the bottom for the description type in "CFO's laptop was not charging due to broken charger, brought new charger, now successfully charging."

- Then click "Post Reply"

<br>

<h2> &#9324; Reviewing Ticket Access Permissions</h2>

<br>

<img width="651" height="227" alt="Screenshot 2025-09-03 at 12 42 30 PM" src="https://github.com/user-attachments/assets/5f10b4ac-5386-47e1-a8e5-77c9112c0513" />


<br>

- Set the status to "Resolved"
  
- At the bottom, for the description type in "Charger was broken, because of this, the battery was dead and unable to turn on"

- Click close, and the ticket should be gone

- Log in as an admin and look at the different permissions as you need to give John and other people the ability to see closed tickets, or vice versa, if you don't want them to have the ability

<br>

<h2> &#9325; Real-World Reminder</h2>

<br>

<img width="647" height="396" alt="Screenshot 2025-09-03 at 12 46 40 PM" src="https://github.com/user-attachments/assets/42bfd430-7e06-4577-937f-3a8e04fa9d37" />

<br>
<img width="960" height="848" alt="Screenshot 2025-09-03 at 12 47 05 PM" src="https://github.com/user-attachments/assets/3b7b4231-03dd-4f2f-b59a-0fb99ba8fab3" />
<br>
<br>
<br>

<img width="956" height="688" alt="Screenshot 2025-09-03 at 12 44 08 PM" src="https://github.com/user-attachments/assets/e4b01b82-b57e-46c4-a176-b8bbc3ce579a" />

<br>

- This is the full conversation throughout the time of the ticket


- You never know, you might get a call stating an issue that has just occurred with someone's laptop or cell phone, for example

- Then you will probably get all their contact info and make notes for later to organize your notes and get back to them with an understanding mindset

- You can use ChatGPT to facilitate a person and help them with their ticket, as this builds a mindset for real-world scenarios and issues

- Doing these a couple of times can help you solve issues much faster
  
<br> 

<h3>🎉 Congratulations!! &#127881; You just created your first customer support ticket and provided real assistance!</h3>

You’ve officially taken your first big step into the world of IT support by opening, managing, and responding to customer tickets. 
From understanding the issue to providing updates and resolving the problem, you’ve practiced the exact workflow real help desk teams use every day

Keep building on this skill — every ticket you handle sharpens your problem-solving, communication, and technical abilities. 🚀

<br>

<h2> Final Thoughts </h2>

Working through this osTicket installation and configuration project has been a huge step forward in my IT journey. It gave me a real-world look into what it’s like to support users, set up systems from scratch, and manage an actual ticketing platform like you would in a real help desk environment.

I started by creating a virtual machine in Microsoft Azure, then installed and configured key components like IIS, PHP, MySQL, and osTicket itself. Throughout the process, I learned how each piece connects — from the web server and database to the backend files and front-end support interface. This taught me how to troubleshoot installation issues, manage configurations, and make the system actually work for users.

Beyond just setup, I got hands-on with configuring the system for daily IT use — building out user roles, permissions, departments, SLA plans, and help topics. I also practiced resolving tickets from both the admin and agent sides, which gave me a real sense of how IT teams operate and communicate internally to solve issues for end users.

Most importantly, this project helped me grow more confident with tools and tasks that are common in IT support roles, like remote desktop, server configuration, and permission handling. It also reminded me how important communication, documentation, and structure are in IT environments.

Overall, this was more than just a lab — it was a chance to think like a real IT professional, and it helped me build the practical skills I’ll need to succeed in the field.









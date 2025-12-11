# **Wayang kulit Unreal Engine project.** 

# 

# **Opening the Project on a Windows Computer**

Rodrigo Antonio Vega Cruz. Center of Holistic Integration. Intern working in Unreal engine. Contact email for Rodrigo Antonio Vega Cruz: [rodrigo.vega@mail.citytech.cuny.edu](mailto:rodrigo.vega@mail.citytech.cuny.edu).  
2025-10-15 \- 2025-10-16

TABLE OF CONTENTS

[1\. INTRODUCTION	2](#1.-introduction)

[2\. Prelaunch Considerations	2](#2.-prelaunch-considerations)

[2.1 Required Version Number	2](#2.1-required-version-number)

[2.2 Installing Unreal	2](#2.2-installing-unreal)

[2.3 Using a Laptop with MUX switch	3](#2.3-using-a-laptop-with-mux-switch)

[2.3.1 Using Ultimate mode to connect laptop screen to NVIDIA GPU	3](#2.3.1-using-ultimate-mode-to-connect-laptop-screen-to-nvidia-gpu)

[2.3.2 Using Armoury Crate and NVIDIA Control Panel to connect laptop screen to NVIDIA GPU	4](#2.3.2-using-armoury-crate-and-nvidia-control-panel-to-connect-laptop-screen-to-nvidia-gpu)

[2.4 Configurations after connecting the laptop screen to the NVIDIA GPU	5](#2.4-configurations-after-connecting-the-laptop-screen-to-the-nvidia-gpu)

[2.5 With some laptops with NVIDIA GPU’s it might be a better idea to use the drivers provided by the laptop brand then using the latest ones from NVIDIA themselves. Because I (Rodrigo) had issues with a laptop with NVIDIA GPU after using a driver from the NVIDIA website stuff	5](#2.5-with-some-laptops-with-nvidia-gpu’s-it-might-be-a-better-idea-to-use-the-drivers-provided-by-the-laptop-brand-then-using-the-latest-ones-from-nvidia-themselves.-because-i-\(rodrigo\)-had-issues-with-a-laptop-with-nvidia-gpu-after-using-a-driver-from-the-nvidia-website-stuff)

[2.6 Other Required software that needs to be installed before cloning and opening the project	5](#2.6-other-required-software-that-needs-to-be-installed-before-cloning-and-opening-the-project)

[3\. Windows power settings	6](#3.-windows-power-settings)

[4\. Preparations to opening the project	6](#4.-preparations-to-opening-the-project)

# **1\. INTRODUCTION** {#1.-introduction}

This document provides instructions on how to run the Unreal Engine project on a computer running a modern version of Windows natively. The Unreal Engine project has not been tested on a virtual machine running Windows. Therefore, these instructions may not apply to those wanting to open the Unreal engine project on a Windows virtual machine.

# **2\. Prelaunch Considerations** {#2.-prelaunch-considerations}

This section provides a list of things that need to be checked before opening the Unreal Engine Project.

## **2.1 Required Version Number** {#2.1-required-version-number}

Check that Unreal Engine 5.5.4 or a later version where: the third digit is higher, the first digit is 5, and the second digit is 5\.

This project used the most recent version of Windows 11 (I Rodrigo believe that I mostly used the Home edition of Windows for most of the work) from the time of Jan 2025 \- up to October 16 2025\.

## **2.2 Installing Unreal** {#2.2-installing-unreal}

If Unreal Engine 5 is not installed in the computer running Windows operating system natively. Then follow the following instructions.

1. Download Epic Games Launcher.  
2. Install the Epic Games Launcher. (While installing this software and any other necessities you might have to allow some firewall stuff to use the software and any necessities that the software needs).  
3. After installing the Epic Games Launcher, proceed to opening the Epic Games Launcher. (An Epic Games account may need to be created and then log in to use the Epic Games account to use the launcher. If an Epic games account is ready, then that account could be used to log in to the Epic Games Launcher).  
4. After opening the Epic Games Launcher and being logged in. Go to the Unreal Engine section, then select Library, from there you can add an engine version.  
   1. You might have to select a drop down menu before installing the more appropriate version of Unreal Engine necessary to open the project.  
   2. It is a good idea to install the engine on an internal drive (preferably a solid state drive) instead of an external drive. Although if an external drive and/or a drive connected by an adapter and/or enclosure is going to be used it is recommended to do it with a high speed supported drive connected to a port in the computer that can support high speed data transfers.  
5. After the more appropriate version of Unreal Engine is installed. Open the Engine before opening the software and/or the Unreal Engine Project. This procedure is done to ensure that the Unreal Engine software is working, any requirements are installed, and to make sure that any permission stuff that is necessary is set up.  
6. If there were no previous errors now Unreal Engine 5 should be ready to open the project.  
   

## **2.3 Using a Laptop with MUX switch** {#2.3-using-a-laptop-with-mux-switch}

If you are using a Laptop with a MUX switch that allows you to connect discrete graphics directly to the laptop screen, then please switch the laptop screen to connect to the discrete graphics directly.

### 	**2.3.1 Using Ultimate mode to connect laptop screen to NVIDIA GPU** {#2.3.1-using-ultimate-mode-to-connect-laptop-screen-to-nvidia-gpu}

The following instructions are for modern ASUS ROG laptops using a modern version of Armoury Crate switch to discrete graphics using Ultimate GPU Mode which might require a restart if Ultimate mode has not been set (for other laptop brands, the procedure might be similar and the software used will probably be different):  
	

1. Open the Armoury Crate software (it is recommended that during any time Armoury Crate is loading something not to minimize it. Reason being Rodrigo has had issues of not being able to reopen the Armoury Crate window again).  
2. Go to devices (In some cases you might not see the word Devices. If that is the case select the hamburger menu closer to the upper left corner to be able to see the word devices).  
3. Select the laptop that is going to be used for opening the Unreal Engine Project.  
4. Then go to the GPU Performance tab (You might have to select the 3 dots menu to see GPU Performance and select it while under the laptop configuration stuff).  
5. After getting to the GPU Performance tab, select the Ultimate GPU Mode. ( It may ask you to restart your computer. If that is the case, please restart your computer).  
6. After the GPU Mode has been set to Ultimate. The Unreal Engine project can now be opened.

   ### **2.3.2 Using Armoury Crate and NVIDIA Control Panel to connect laptop screen to NVIDIA GPU** {#2.3.2-using-armoury-crate-and-nvidia-control-panel-to-connect-laptop-screen-to-nvidia-gpu}

   

   If the user desires not to restart their computer another method for them is to use the standard GPU mode in Armoury Crate and switch to NVIDIA GPU only from the NVIDIA Control Panel. Here are the instructions if the user prefers to do so this way (for other laptop brands or ASUS ROG laptops that don’t use Armoury Crate, the procedure might be similar and the software used will probably be different):

   	

1. Make sure that any open widowed and/or fullscreen applications and software is closed to avoid any issues.  
2. Now open the Armoury Crate software (it is recommended that during any time Armoury Crate is loading something not to minimize it. Reason being Rodrigo has had issues of not being able to reopen the Armoury Crate window again).  
3. Go to devices (In some cases you might not see the word Devices. If that is the case select the hamburger menu closer to the upper left corner to be able to see the word devices).  
4. Select the laptop that is going to be used for opening the Unreal Engine Project.  
5. Then go to the GPU Performance tab (You might have to select the 3 dots menu to see GPU Performance and select it while under the laptop configuration stuff).  
6. After getting to the GPU Performance tab, select the standard GPU Mode. ( It may ask you to restart your computer if you are already in Ultimate GPU Mode. If that is the case, you can choose to stay in ultimate mode or go for the other method which will probably still require restarting because you are in Ultimate GPU Mode).  
7. Now after selecting Standard GPU Mode in Armoury Crate. Go feel free to close it. (You can also leave it open if you still want it open. Although because there are about to be changes in the NVIDIA Control Panel. It is probably a good idea to close the Armoury Crate. Because even if the operating system can handle switching GPU without windows opened (aside from the NVIDIA Control Panel), some software might not be able to handle switching GPU and might be issues after switching the GPU).  
8. Now open the NVIDIA Control Panel software.  
9. Under 3D Settings, go to Manage Display mode.  
10. Under Manage Display mode. In Display Mode select the NVIDIA GPU only.  
11. After selecting the NVIDIA GPU only option. Select Apply. If asked to keep the changes, accept it ASAP. (Because that dialog pop up is most likely going to be timed. If you do not accept it in a timely manner it is going to revert the settings. Although the user will probably have a chance to do it again).

    ### **2.4 Configurations after connecting the laptop screen to the NVIDIA GPU** {#2.4-configurations-after-connecting-the-laptop-screen-to-the-nvidia-gpu}

After having selected the more appropriate set up for using the NVIDIA discrete graphics. Make sure that the original or at least the appropriate charger is connected to appropriate electricity. Open the Armoury Crate and set the Operating Mode to Turbo. (On a Desktop computer, you might not have to deal with the switching between discrete graphics and integrated graphics to connect to the screen. Because on many desktop computers you can just connect the display and/or projection device to the graphics card itself. Unless you are using a motherboard that can connect to the GPU somehow and probably pass it through a port on the motherboard that then connects to the display and/or projecting device. I cannot predict for every device that natively runs Windows how things are done).

### **2.5 With some laptops with NVIDIA GPU’s it might be a better idea to use the drivers provided by the laptop brand then using the latest ones from NVIDIA themselves. Because I (Rodrigo) had issues with a laptop with NVIDIA GPU after using a driver from the NVIDIA website stuff** {#2.5-with-some-laptops-with-nvidia-gpu’s-it-might-be-a-better-idea-to-use-the-drivers-provided-by-the-laptop-brand-then-using-the-latest-ones-from-nvidia-themselves.-because-i-(rodrigo)-had-issues-with-a-laptop-with-nvidia-gpu-after-using-a-driver-from-the-nvidia-website-stuff}

### **2.6 Other Required software that needs to be installed before cloning and opening the project** {#2.6-other-required-software-that-needs-to-be-installed-before-cloning-and-opening-the-project}

The following things should be installed to clone and work with the GitHub repository: Git, Git LFS, and GitHub Desktop. Here is a video link about GitHub and Unreal Engine that is about installing the three previously mentioned software: [https://www.youtube.com/watch?v=n3x1fErlmYA](https://www.youtube.com/watch?v=n3x1fErlmYA).

It is recommended to install all the software on an internal drive to avoid having issues. Few of those issues are but not limited to: can’t get certain things to work because the drive with all or part of the required software is not connected, or the drive accidentally disconnects from the computer.

# **3\. Windows power settings** {#3.-windows-power-settings}

In Windows 11 Settings Under System, go to Power & battery, under the Power Mode drop down menu, set both for Plugged in and On battery Best Performance. Now the computer should be ready to open the Unreal Engine Project.

# **4\. Preparations to opening the project** {#4.-preparations-to-opening-the-project}

The following are the instructions to open the Unreal Engine Project and use GitHub desktop on a computer running modern Windows natively.

1. The following things should be installed to clone and work with the GitHub repository: Git, Git LFS, and GitHub Desktop. Use this video to help you if you need help with knowing how to install the three previously mentioned software. After the previous things are installed proceed with the instructions:  
   1. Clone this GitHub repository into your computer (preferably avoid external drives): [https://github.com/CHI-CityTech/Shadow\_puppet\_Unreal](https://github.com/CHI-CityTech/Shadow_puppet_Unreal). (Make sure not to clone this into a cloud storage backed up folder in the computer to avoid issues).  
   2. Go to the main branch.  
   3. Make sure to Pull and Fetch origin to ensure you have the latest updates.  
2. With the more appropriate version of Unreal Engine installed go to the location of where the project is located.  
   1. Open the project folder (it should be named Shadow\_puppet\_test).  
   2. After opening the project folder, double click on the file name Shadow\_puppet\_test.uproject.  
   3. It will probably take a while to open the Unreal Engine project.  
3. After the Unreal Engine project opens, it might ask you to open windows that were opened. Which it is recommended for the user to accept the option to open them.  
4. Now that the project is open:  
   1. With the editor opened and its window being selected. Press CTRL and Space at the same time.  
   2. From the All directory: go to Content, Levels, open the level titled Rigging\_Enclosed\_Puppet\_show. (This step can be avoided if the level is already opened).  
5. Within the project there is a smaller shadow puppet that is there because I (Rodrigo) if remembered correctly was testing something(s) and wanted a better understanding of something(s).  
6. You can hit play when you are in the Level. Walk to the front of the Level using WASD to move the character in a different position and mouse movement to change where the character is pointing and where the character is headed while walking. Stand in front of the yellowish white material and you should see the animation of the shadow puppet.

PLEASE DO NOT PUSH INTO ANY OF RODRIGO ANTONIO VEGA CRUZ'S BRANCHES. YOU MIGHT BE ABLE TO PUSH INTO ANOTHER BRANCH PERHABS. IT IS PROBABLY A GOOD IDEA THAT YOU FIRST COMMUNICATE WITH DAVID B SMITH, IF HE IS NOT AWARE IF ANYBODY IS WORKING ON THE PROJECT.
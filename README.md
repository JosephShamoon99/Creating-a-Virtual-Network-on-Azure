<p align="center"> 
<img width="418" height="120" alt="Azure Logo" src="https://github.com/user-attachments/assets/3b6347a2-5104-4eb2-b4a2-0a7a28524ee0" />
</p>

<h1>Creating Virtual Machines on Azure</h1>
Microsoft Azure is a cloud computing platform that provides services such as virtual machines, virtual networks, storage and much more. It is very important to have  
experience with cloud computing as an IT professional, as many compaines are moving their IT infrastructure to 
the cloud. In this tutorial I will show you how to create virtual machines in Azure.<br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- RDP
- SSH

<h2>Operating Systems Used </h2>

- Windows 11
- Ubuntu Server 20.04

<h2>High-Level Steps</h2>

- Create a Windows virtual machine and a Linux virtual machine
- Place them on a virtual network
- Log in to the Windows VM with RDP
- Log in to the Linux VM with SSH

<h2>Creating Virtual Machines in Azure</h2>

<p>
<img width="1920" height="955" alt="Snapshot#1" src="https://github.com/user-attachments/assets/81da1903-38a4-4b71-8a42-36c771cd739a" />
</p>
<p>
First, go to the Azure Home Screen. Then select the Resource Group tab. Here we will make a resource group to act as a container for everything that we will create in this lab. 
</p>
<br />

<p>
<img width="1920" height="955" alt="Snapshot#2" src="https://github.com/user-attachments/assets/1fc0cdba-d9f4-459d-b106-e0f241a76616" />
</p>
<p>
On the Resource Group page, you can see there is nothing. Select "create" to make a new resource group. 
</p>
<br />

<p>
<img width="1920" height="955" alt="Snapshot#3" src="https://github.com/user-attachments/assets/38a504b2-238f-4b47-b7d1-066096e54cda" />
</p>
<p>
When you create a new resource group, you will be asked to fill out 3 fields. 

The first one is which subscription this resource group will go on for billing. You should only have 1. 

The second field is the name of the resource group. You can name it anything you want. 

The third field is the region. This is the geological location where the services we make on the Azure Cloud will be stored. You can pick any region you want, but it is a good idea to choose a consistent region 
for all of your services.
</p>
<br /> 

<p>
<img width="1920" height="953" alt="Snapshot#4" src="https://github.com/user-attachments/assets/ba379917-5625-4767-b4cf-219f02bf2d62" />
</p>
<p>
After you fill all of that out, you can click "review and create". Review everything and click "create". 
</p>
<br /> 

<p>
<img width="1920" height="955" alt="Snapshot#5" src="https://github.com/user-attachments/assets/252c6aad-7d6f-458d-be77-4a79a34bde42" />
</p>
<p>
You should now see our new resource group in the Resource Groups tab.
</p>
<br /> 

<p>
<img width="1920" height="953" alt="Snapshot#6" src="https://github.com/user-attachments/assets/842fa84f-6984-4df3-a25a-ecacb48dc92d" />
</p>
<p>
Now that we have our resource group created, we can now create our virtual machines. Go back to the Azure home screen and select the Virtual Machines tab.
</p>
<br /> 

<p>
<img width="1920" height="953" alt="Snapshot#7" src="https://github.com/user-attachments/assets/db17d6e6-8a82-49a0-a39d-eb6931f69994" />
</p>
<p>
As you can see again, there is nothing. Click "create" to create a new virtual machine. 
</p>
<br /> 

<p>
<img width="1920" height="953" alt="Snapshot#8" src="https://github.com/user-attachments/assets/74152ae0-282d-4049-84c5-151100caa3b0" />
</p>
<p>
Select the first option, "virtual machine".
</p>
<br /> 

<p>
<img width="861" height="118" alt="Snapshot#9" src="https://github.com/user-attachments/assets/310cfc16-10e4-4e30-93c8-d40e366a7546" />
</p>
<p>
The first thing you will be asked is what subscription and what resource group this VM will belong to. Select your only subscription and the resource group we just made. 
</p>
<br /> 

<p>
<img width="878" height="376" alt="Snapshot#10" src="https://github.com/user-attachments/assets/fcb2f661-cde0-4b1c-ae23-f5fb58041551" />
</p>
<p>
Next, you will name the VM and select which region it will belong too. You can name the VM anything you want. Pick the same region you have been using. 
</p>
<br /> 

<p>
<img width="907" height="300" alt="Snapshot#11" src="https://github.com/user-attachments/assets/d40232a6-9b17-4742-976f-80b645d210fb" />
</p>
<p>
Next, you will pick which image the VM will use. The image is the operating system the VM will use. This will be our Windows machine, so select Windows 11 for the image.

Next, we will pick the size we want the VM to be. The size is how many resources the VM will use. 2vcpus will be enough for our purposes. 
</p>
<br /> 

<p>
<img width="856" height="168" alt="Snapshot#12" src="https://github.com/user-attachments/assets/2d5e6c41-d870-4a76-b4c5-8f99ae2d0928" />
</p>
<p>
After that, we will create a username and password for the admin account of the VM. We will use this to log in to the VM later. 
</p>
<br /> 

<p>
<img width="839" height="284" alt="Snapshot#13" src="https://github.com/user-attachments/assets/25de6c77-319a-4d73-8ef9-e482b9f91535" />
</p>
<p>
Next, We will set the rules for our inbound ports. It is important that we allow traffic to selected ports and make that port 3389 (RDP). This will allow us to log in to the VM from our desktop.
</p>
<br /> 

<p>
<img width="527" height="116" alt="Snapshot#14" src="https://github.com/user-attachments/assets/91a47984-c011-45f3-aec0-40ff1846d5e2" />
</p>
<p>
Select the check box for the licensing agreement. Then hit "next" until you get to the Networking section.
</p>
<br /> 

<p>
<img width="860" height="185" alt="Snapshot#15" src="https://github.com/user-attachments/assets/bf421b54-56ec-4097-a434-d1eb07d02b30" />
</p>
<p>
In the Networking section, we will be asked to select a virtual network to place this VM on. We do not have any virtual networks created yet, so Azure will create one for us. We will also place our next VM on the same virtual network. You can now select “review and create” and select “create” to create the VM. It should take a little while for the VM to be created. 
</p>
<br /> 

<p>
<img width="1920" height="693" alt="Snapshot#16" src="https://github.com/user-attachments/assets/4a6d9664-0b7f-464e-b16b-77fedc2a074d" />
</p>
<p>
Go back to the Virtual Machine tab and you should see your Windows virtual machine. 
</p>
<br /> 

<p>
<img width="1920" height="953" alt="Snapshot#17" src="https://github.com/user-attachments/assets/1a0cc744-620c-495d-bc43-5b25e941edf7" />
</p>
<p>
You can also see the virtual network that we created. Go back to the Homepage and click the Virtual Network tab. 
</p>
<br /> 

<p>
<img width="1920" height="875" alt="Snapshot#18" src="https://github.com/user-attachments/assets/fd609063-b285-40b5-a992-5f12df11eadc" />
</p>
<p>
You should see it there.
</p>
<br /> 

<p>
<img width="790" height="55" alt="Snapshot#19" src="https://github.com/user-attachments/assets/103757e7-1e06-4c0b-9906-d9c9649b63d0" /> 
<img width="828" height="257" alt="Snapshot#20" src="https://github.com/user-attachments/assets/79b8b897-a978-493d-94a6-fa49bffdac22" />
</p>
<p>
Now we will create the Linux virtual machine. Everything should be the same as creating the Windows machine, with the same resource group and region. However, this time you should choose Ubuntu for the image and select port 22 (SSH) for inbound ports.  
</p>
<br /> 

<p>
<img width="785" height="175" alt="Snapshot#21" src="https://github.com/user-attachments/assets/8ecd13fa-8794-42bf-b4b3-5732714e6613" />
</p>
<p>
Make sure to use the same virtual network we created.  
</p>
<br /> 

<p>
<img width="1903" height="708" alt="Snapshot#22" src="https://github.com/user-attachments/assets/83f54413-ff74-4787-8937-5e298e3f162f" />
</p>
<p>
Create the virtual machine, and you should see it in the Virtual Machine tab, along with the Windows VM.  

Now that we have our VM’s created, we can log in to them remotely. For our Windows VM, we can use RDP.  
</p>
<br /> 

<p>
<img width="358" height="157" alt="Snapshot#23" src="https://github.com/user-attachments/assets/4dc24dae-431e-4d32-8a48-3b91fcae45a0" />
</p>
<p>
Go to your Start Menu and type "RDP" and select it. 
</p>
<br /> 

<p>
<img width="416" height="267" alt="Snapshot#24" src="https://github.com/user-attachments/assets/b15b84f1-2745-47bd-9a76-48f5334ef006" />
</p>
<p>
You will be asked for the IP of the VM we are trying to log in to. 
</p>
<br /> 

<p>
<img width="1920" height="701" alt="Snapshot#25" src="https://github.com/user-attachments/assets/6626a8f3-6175-43b2-8c0e-1f72778890bf" />
</p>
<p>
Go to the Virtual Machine tab and find the public IP of the Windows machine. 
</p>
<br /> 

<p>
<img width="421" height="263" alt="Snapshot#26" src="https://github.com/user-attachments/assets/aa5e253f-14c6-4cce-8922-751e1426444e" />
<img width="467" height="495" alt="Snapshot#27" src="https://github.com/user-attachments/assets/26e7a53b-56cb-4961-83b2-571b4862aff2" />
<img width="403" height="416" alt="Snapshot#28" src="https://github.com/user-attachments/assets/c7b1b66d-2331-41f1-ad13-0e71dba86057" />
</p>
<p>
Enter in the Windows VM public IP address. You will be asked for the username and password of the admin account on the VM. type that in. You will be given a warning about connecting to 
The VM, just hit yes since we know it is our VM. 
</p>
<br /> 

<p>
<img width="1919" height="1079" alt="Snapshot#29" src="https://github.com/user-attachments/assets/747a258a-0e66-4696-b118-3802462bf03e" />
</p>
<p>
We are now in the Windows VM via RDP. 

We can not use RDP to log in to the Linux machine, so we will have to use SSH.
</p>
<br /> 

<p>
<img width="1920" height="658" alt="Snapshot#30" src="https://github.com/user-attachments/assets/9e12a117-3bb5-47c7-b73c-7bfe5f47ba46" />
</p>
<p>
First, you will have to get the public IP address of the Linux machine
</p>
<br /> 

<p>
<img width="1117" height="634" alt="Snapshot#31" src="https://github.com/user-attachments/assets/05b35b7c-bb0e-4740-9389-fbf60c95ef85" />
<img width="1130" height="642" alt="Snapshot#32" src="https://github.com/user-attachments/assets/5e5986fd-0b00-4597-a236-f2ac235cd55d" />
<img width="592" height="21" alt="Snapshot#33" src="https://github.com/user-attachments/assets/66596e54-0568-4205-b196-d4613895f711" />
<img width="1118" height="635" alt="Snapshot#34" src="https://github.com/user-attachments/assets/6a4217af-e08f-4f62-931f-dd3d4fd3e3b4" />
</p>
<p>
On the Windows VM, go to Power Shell and use the SSH command followed by the Linux virtual machine's public IP address. You will be given a warning about logging in, just type yes like last time. You will be asked for the password to the Linux VM. When you type, it will be invisible. After that you will be log in into the Linux virtual machine, inside the Linux Command Line. 
</p>
<br />  


<p>
Awesome! You now know how to create virtual machines on Azure how to log in to them using remote protocols! Azure offers many more services, so go do some researching to see everything you can do with this powerful cloud computing platform. If you want to learn some common networking commands using our Windows VM, check out this tutorial: 

[Mircosoft Azure: Common Networking Commands](https://github.com/JosephShamoon99/Common-Networking-Commands)
</p>
<br /> 



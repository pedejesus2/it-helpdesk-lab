# it-helpdesk-lab
Repository was created to document each step of VM Labs. Using Oracle VirtualBox

Overview:

This is a setup of a Windows 11 virtual machine using Oracle VirtualBox, any error would also be documented along the installation. Including Screenshots.

Environment:

Host OS: Windows 11 (tiny11 23H2 x64)

Hypervisor: Oracle VirtualBox

Guest OS: Windows 11

Launched Oracle VirtualBox and created a Windows 11 virtual machine, configured memory and storage use. 

4GB of memory

20GB of storage

Then, Windows Setup screen is presented, chose default English (United States) Language option and Time & currency format

Clicked > Next to continue setup.

<img width="1121" height="851" alt="image" src="https://github.com/user-attachments/assets/40bcc0c6-a78e-4912-a7c9-5dbc63a93715" />

No errors while setting up the virtual machine, finished setup and virtual machine restarted. 

After setting up Language again, some telemetry options asked by Windows. It is downloading updates.

<img width="1176" height="846" alt="image" src="https://github.com/user-attachments/assets/f83b4748-20c6-4f29-a014-9f9f780dc9e5" />

Couldnt complete updates but was able to continue to Desktop. User profile is being created. Suspected the updates couldnt be completed because of storage.

<img width="1087" height="839" alt="image" src="https://github.com/user-attachments/assets/b49c515c-403a-47a0-90bb-efaa2f146c61" />

DIAGNOSIS:
Yes, as confirmed. Storgage is running low. Since this is a Windows 11 VM, still reduced in some features. It does uses 13GB of the 20GB assigned. 

<img width="1118" height="862" alt="image" src="https://github.com/user-attachments/assets/767e2d2f-a390-4f10-a345-7e94a35c3db1" />


Fix Aplied: I am going to be reseting the VM, actually shutting it down. Go to the VM settings and set up a much higher value of storage, considering how much I have to share with this VM.

We close down the VM, choose media in the top menu. Hard Disks and while the hard disk selected. We select properties and move the slider or write down how much storage you want to add up.

<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/8e10ebc0-b6f1-487e-a18c-549480c7e972" />

Added up to 55GB but it will not be visible until I manage it inside the VM.

Fixed this by putting this commands into CMD using admin rights:

diskpart

list disk

select disk 0

list partition

Partition 1 → System Reserved (100 MB)

Partition 2 → C: (19 GB)

Partition 3 → Recovery (773 MB) ← THIS ONE

select partition 3

delete partition override

select partition 2

extend

exit

After all of this, I verified the settings storage screen and storage is now recogized by Windows. Also on Disk Management you are able to see the same information.

<img width="1137" height="853" alt="image" src="https://github.com/user-attachments/assets/88d7f411-4754-40b5-8ef1-c44a0a53a086" />

Then, went to the updates section, selected install all option to download and install important Windows Updates

<img width="1129" height="829" alt="image" src="https://github.com/user-attachments/assets/b5159d82-eda3-4041-b37d-6423fe7a0844" />


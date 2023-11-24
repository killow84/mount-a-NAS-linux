# mount-a-NAS-linux
To automatically mount a NAS (Network Attached Storage) drive in Linux,
To automatically mount a NAS (Network Attached Storage) drive in Linux, you can use the /etc/fstab file. The /etc/fstab file contains information about disk drives and partitions and specifies how they should be mounted. Here are the general steps to auto-mount a NAS drive:

Identify NAS Drive Information:
Determine the IP address or hostname of your NAS device.
Identify the share name or the specific directory you want to mount.
Install Required Packages (if not already installed):
Ensure that the necessary packages are installed. Common packages include cifs-utils for mounting CIFS/SMB shares or nfs-utils for mounting NFS shares.
bash
Copy code
# For CIFS/SMB
```
sudo apt-get install cifs-utils
```
# For NFS
```
sudo apt-get install nfs-common
```
Create a Mount Point:
Choose or create a directory where you want to mount the NAS drive. For example, you can create a directory in the /mnt directory.
bash
Copy code
```
sudo mkdir /mnt/nas
```
Edit /etc/fstab:
Open the /etc/fstab file in a text editor with root privileges. For example:
bash
Copy code
```
sudo nano /etc/fstab
```
Add a line at the end of the file to specify the mount details. The format depends on whether you are mounting a CIFS/SMB share or an NFS share.
For CIFS/SMB:
plaintext
Copy code
```
//NAS_IP_OR_HOSTNAME/Share_Name /mnt/nas cifs username=Your_Username,password=Your_Password,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
```
For NFS:
plaintext
Copy code
```
NAS_IP_OR_HOSTNAME:/exported/directory /mnt/nas nfs defaults 0 0
```
Replace NAS_IP_OR_HOSTNAME, Share_Name, Your_Username, Your_Password, and /exported/directory with your actual NAS details.
Save and Exit:
Save the changes to the /etc/fstab file and exit the text editor.
Test the Configuration:
To test the configuration without rebooting, you can use the following command:
bash
Copy code
```
sudo mount -a
```
### This command will attempt to mount all entries in /etc/fstab. If there are any errors, they will be displayed.
Reboot (Optional):
If the test is successful, you can either reboot your system, and the NAS drive should be automatically mounted.
After these steps, your NAS drive should be automatically mounted every time you boot your Linux system. Make sure to replace the placeholders with your actual NAS details and customize the mount options according to your requirements.

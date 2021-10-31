When trying to upgrade the Synology DS218+, it shows "There is insufficient system capacity for updates". Here is the steps I tried to fix this issue:

1. Login to DS218+ web page, and turn on ssh access by "Control Panel" >> "Terminal"

   1. In case can't login the web page, following this link to enable admin user: https://kb.synology.com/th-th/DSM/tutorial/How_do_I_log_in_if_I_forgot_the_admin_password

2. login to DS218+ by ssh

3. Run command "df -h" over ssh connection to check the filesystem status.

   $ df -h

   ​	Filesystem     Size Used Avail Use% Mounted on                                                                 

   ​	/dev/md0      2.3G 2.3G    0  100% /  

4. Run command "ls -lh /" to list all the file/folder.

5. Run command "du -sh < folder name >" to find out which folder is significent larger than usual. In my case, I have a script to back up the file to USB Hard Drive, but that Hard Drive has been removed few days ago. The script tried to back up all the file to /volumeUSB2 and used all available space under /. After stop the script and delete /volumeUSB2, the issue is gone.
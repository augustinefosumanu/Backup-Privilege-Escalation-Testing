# Backup Privilege Escalation Testing

<h2> Lab </h2>

In this lab, I acted as a penetration tester tasked with identifying vulnerabilities in a target system's backup procedures. Key activities included:<br/>

-  <b>Privilege Escalation Testing</b>: Used the wildpwn.py tool to verify whether the system was vulnerable to privilege escalation attacks within its backup configuration.<br/>
-  <b>Vulnerability Assessment</b>: Analyzed the system’s current configuration to identify potential weaknesses that could be exploited for unauthorized access or control.<br/>
-  <b>Url</b>: https://raw.githubusercontent.com/localh0t/wildpwn/master/wildpwn.py<br/>

<h2> Step 1: Login as User Jane and verifying Sudo Rights for User jane </h2>
I first logged in as Jane using the <b>su 'User'</b> command, then verified that I had successfully switched users with the <b>whoami</b> command. Additionally, using the <b>sudo -l</b> command, I confirmed that Jane had no sudo privileges, which was essential for testing the exploitation process.
   <br />
   <br />
<p align="center">
<img src="https://i.imgur.com/eJ87uFK.png" height="80%" width="90%" alt=""/>
  <br />
  <br />
  
<h2> Step 2: Searching for tar file  </h2>
To search for tar files within the current user's directories, I used the <b>cd</b> command to navigate into the Documents directory. After that, I ran the <b>ls</b> command to list the contents, which revealed the presence of the tar file. <br />
<br />
<p align="center">
<img src="https://i.imgur.com/2Ci7lsF.png" height="80%" width="90%" alt=""/>
  <br />
  <br />
  
<h2> Step 3: Verifying Ownership of the Tar File  </h2>
To test the wildcard attack, I first checked the ownership of the tar file in the Documents directory to confirm it didn't belong to Jane. This was important because the file seemed to automatically regenerate to back up files and directories within the directory. To verify this, I used the <b>rm</b> command to delete the tar file. After a short period, the tar file reappeared, confirming its vulnerability to a wildcard attack.<br />
<br />
<p align="center">
<img src="https://i.imgur.com/x9qEli5.png" height="80%" width="90%" alt=""/>
<br />
<br />
<h2> Step 4: Downloading Wildcard Attack File </h2>
Before downloading the <b>wildpwn.py</b> file, I navigated to the <b>ExploitTar</b> directory, which was designated to contain the payload file. I confirmed the contents of the directory using the <b>ls</b> command. After confirming the directory structure, I proceeded to download the file using the <b>wget</b> command. Once the download was complete, I listed the directory contents again to ensure the file had been successfully downloaded.. <br />
 <br />
<p align="center">
<img src="https://i.imgur.com/HJF9Kbs.png" height="80%" width="90%" alt=""/>
   <br />
      <br />
<img src="https://i.imgur.com/w4VM29Z.png" height="80%" width="90%" alt=""/>
   <br />
      <br />
<img src="https://i.imgur.com/e9K4NCv.png" height="80%" width="90%" alt=""/>
   <br />
      <br />
  
<h2> Step 5: Running the Wildcard Attack File Using 'tar' </h2>
After downloading the file, I executed the <b>wildpwn.py</b> script to extract its contents into the <b>ExploitTar</b> directory. To verify the script ran successfully, I used the <b>ls -lat</b> command to list all files, including hidden ones, and confirm the presence of any new files or directories created by the script. <br />
<br />
<p align="center">
<img src="https://i.imgur.com/0I2Ypo4.png" height="80%" width="90%" alt=""/>
     <br />
     <br />
<img src="https://i.imgur.com/j2NckGp.png" height="80%" width="90%" alt=""/>
   <br />
      <br />
  
<h2> Step 6: Executing Payload File </h2>
With the payload file successfully extracted, I navigated into the <b>.cache</b> directory to locate the <b>.cachefile</b> script. Once inside the directory, I executed the script to escalate privileges, granting the user root access. <br />
<br />
<p align="center">
<img src="https://i.imgur.com/KsmXzLT.png" height="80%" width="90%" alt=""/>
<br />
<br />
  
<h2> Step 7: Escalating Privileges </h2>
After obtaining root privileges, I escalated my user permissions by editing the <b>sudoers</b> file, allowing myself root access without requiring a password for sudo commands. To confirm the changes, I verified my sudo privileges by executing <b>sudo -l</b>. <br />
<br />
<p align="center">
<img src="https://i.imgur.com/SO2t8YO.png" height="80%" width="90%" alt=""/>
   <br />
      <br />
<img src="https://i.imgur.com/LxxQBa8.png" height="80%" width="90%" alt=""/>
   <br />
      <br />
<img src="https://i.imgur.com/x71KrsQ.png" height="80%" width="90%" alt=""/>
   <br />
      <br />
<img src="https://i.imgur.com/EatcSwi.png" height="80%" width="90%" alt=""/>
   <br />
      <br />
  
<h2> Step 8: Successful Exploitation of 'tar' </h2>
To finalize my verification of the privilege escalation, I accessed the <b>/etc/shadow</b> file using a <b>sudo cat</b> command. The system did not prompt me for a password, confirming that the escalation was successful.    <br />
<br />
<p align="center">
<img src="https://i.imgur.com/xbmB9Ee.png" height="80%" width="90%" alt=""/>
   <br />
      <br />
  
<h2> Step 9: Deleting Evidence </h2>
To cover my tracks, I deleted the ExploitTar directory using the sudo rm -r command. This ensured that all associated files, including hidden directories and files, were completely removed from the system, leaving no trace of the exploit.
<br />
<br />
<p align="center">
<img src="https://i.imgur.com/JInSAyE.png" height="80%" width="90%" alt=""/>
   <br />
      <br />
  

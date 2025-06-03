<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
This tutorial outlines the prerequisites and installation of the open-source help desk ticketing system osTicket.<br />



<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop (now Windows App)
- Internet Information Services (IIS)
- MySQL
- osTicket

<h2>Operating Systems Used </h2>

- macOS Sequoia

<h2>List of Prerequisites</h2>

- [Creating Virtual Machines in the Cloud](https://github.com/jadenhinds-hub/creatingvirtualmachinesinthecloud)
- [osTicket Installation Files](https://drive.google.com/drive/u/0/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6)(For reference purposes. Link to download zip file is below.)

<h2>Installation Steps</h2>

<p>
**Create a Windows 10 virtual machine in Azure with 4 vCPUs**
</p>
<p>
<p>
<br>
  
</p>
  <img width="1440" alt="Screenshot 2025-06-03 at 3 38 55 PM" src="https://github.com/user-attachments/assets/0a59380a-ba2d-4a2e-9827-99dfcbb4805c" />
  
</p>
<p>

  </p>
<p>
  <br>
Login to the VM with Remote Desktop
<p></p>
<br>
:Copy the public IP address and use it in Remote Desktop to access the VM. Also, keep note of the username and password you set in the VM as we will access this to login. 
<br>
<img width="1440" alt="Screenshot 2025-06-03 at 3 41 43 PM" src="https://github.com/user-attachments/assets/4c36f5f8-6eb7-43a9-a670-06de24b06849" />

</p>
<p>
</p>
<p>
  <br>
Log into the osTicket VM, then copy the osTicket installation files link provided above and paste it into the web browser. This will direct you to a ZIP file containing all the necessary files to install osTicket on the VM. Unzip it to the desktop
  
<img width="1440" alt="Screenshot 2025-06-03 at 2 40 40 PM" src="https://github.com/user-attachments/assets/8d5c8b61-cf57-49e6-a45b-72f529cc424d" />

</p>
<br />
</p>
<p>
<p>- Now, we'll enable IIS (Internet Information Services) in Windows and make sure CGI is installed.</p>
<p>- Open the Start Menu, go to Control Panel, and click on Uninstall a program.</p>
<p>- Then, click Turn Windows features on or off. </p>
<br/>


<table>
  <tr>
    <td>
      <img width="1126" alt="Screenshot 2025-06-03 at 3 48 51 PM" src="https://github.com/user-attachments/assets/1578d5d8-b17d-4d19-8dfe-095dc1969ba9" />

    </td>
    <td>
      <img width="1440" alt="Screenshot 2025-06-03 at 3 50 20 PM" src="https://github.com/user-attachments/assets/c9f60b4b-2eaa-41af-907d-ef717b4abf60" />

    </td>
  </tr>
</table>
---


---


---

 **Install PHP Manager for IIS**

* Download: PHPManagerForIIS_V1.5.0.msi 
(From the “osTicket-Installation-Files” folder)
</p>
<p>
  <br>
 **Install Rewrite Module**
 Download: rewrite_amd64_en-US.msi
 (From the “osTicket-Installation-Files” folder)
</p>
<img width="1440" alt="Screenshot 2025-06-03 at 2 48 27 PM" src="https://github.com/user-attachments/assets/0b0d46bd-ac8a-44ca-a513-966baece0f18" />

<p>
  <br>
 **PHP**
-Create the directory C:\PHP
-From “osTicket-Installation-Files” folder, unzip PHP 7.3.8 (php-7.3.8-nts-Win32-VC15-x86.zip) into the “C:\PHP” folder

</p>
<p>
  <br>
 **MySQL**
 (Both from “osTicket-Installation-Files” folder)
Install VC_redist.x86.exe
Install MySQL 5.5.62 (Typical Setup → Standard Configuration)
<p>
  
</p>
<img width="1440" alt="Screenshot 2025-06-03 at 2 52 34 PM" src="https://github.com/user-attachments/assets/f612a9b1-0252-4fd9-b38a-1a7375aca943" />

<p>
  </p>
<p>
  <br>
  Follow these steps to properly setup MySQL:
  </p>
<p>
- Typical Setup ->
- Launch Configuration Wizard (after install) ->
- Standard Configuration ->
- Username: root
- Password: root

</p>


<h3>4. Configure IIS and PHP</h3>
<p>
<img width="1440" alt="Screenshot 2025-06-03 at 2 56 29 PM" src="https://github.com/user-attachments/assets/e1a9c986-1f23-49a4-a70c-bd3323848280" />
</p>
<p>
Register PHP in IIS
<code>C:\PHP\php-cgi.exe</code><br/>
Restart IIS (stop and start the server).
</p>
<br />

<h3>5. Install osTicket</h3>
<p>
<img width="1440" alt="Screenshot 2025-06-03 at 3 02 20 PM" src="https://github.com/user-attachments/assets/4367d788-bf4a-4b68-a6d3-9c6cbdaa5db9" />

  <img width="1440" alt="Screenshot 2025-06-03 at 3 04 39 PM" src="https://github.com/user-attachments/assets/42a076e6-2589-4553-b1b7-aa036f5f49b5" />


</p>
<p>
Unzip <code>osTicket-v1.15.8.zip</code> from the installation files and:
<ol>
  <li>Copy the <code>upload</code> folder into <code>C:\inetpub\wwwroot</code></li>
  <li>Rename <code>upload</code> to <code>"osTicket"</code></li>
  <li>Restart IIS</li>
  <li>Browse to: <code>http://localhost/osTicket</code></li>
</ol>
</p>
<br />

<h3>6. Enable PHP Extensions</h3>
<p>
<img width="1440" alt="Screenshot 2025-06-03 at 3 07 00 PM" src="https://github.com/user-attachments/assets/d1e2832f-9ca7-4e53-a0c4-861ecb66d478" />

</p>
<p>
In IIS:
<ol>
  <li>Go to Sites → then Default → then osTicket → then PHP Manager</li>
  <li>Enable these extensions:
    <ul>
      <li>php_imap.dll</li>
      <li>php_intl.dll</li>
      <li>php_opcache.dll</li>
    </ul>
  </li>
</ol>
Refresh the osTicket page to verify the extensions are enabled.
</p>
<br />

<h3>7. Configure osTicket</h3>
<p>
<img width="1440" alt="Screenshot 2025-06-03 at 3 08 56 PM" src="https://github.com/user-attachments/assets/ec59749f-f63e-49ac-a915-ce0259241623" />

</p>
<p>
<ol>
  <li>Rename: <code>ost-sampleconfig.php</code> → <code>ost-config.php</code></li>
  <li>Location: <code>C:\inetpub\wwwroot\osTicket\include\</code></li>
  <li>Set permissions: Disable inheritance → Remove all → Grant Everyone Full Control</li>
</ol>
</p>
<br />

<h3>8. Create MySQL Database</h3>
<p>

<img width="1440" alt="Screenshot 2025-06-03 at 3 13 38 PM" src="https://github.com/user-attachments/assets/bec2af07-63d9-4e84-880b-0cec59fd14e0" />

<img width="1440" alt="Screenshot 2025-06-03 at 3 15 41 PM" src="https://github.com/user-attachments/assets/a91e93d5-9fa8-4f2d-a28b-0629e9eb4128" />

<p>
Install HeidiSQL and:
<ol>
  <li>Create new session using root/root</li>
  <li>Create a new database named <code>osTicket</code></li>
</ol>
</p>
<br />

<h3>9. Finalize Installation</h3>
<p>
<img width="1440" alt="Screenshot 2025-06-03 at 3 22 35 PM" src="https://github.com/user-attachments/assets/c1df4fcb-0ebb-4b42-b4b7-86bf520c8a7c" />

  <img width="1440" alt="Screenshot 2025-06-03 at 3 18 09 PM" src="https://github.com/user-attachments/assets/0417e4a6-7372-465a-904b-21e775aacc6f" />

>
</p>
<p>
Return to the browser setup page:
<ol>
  <li>Database: <code>osTicket</code></li>
  <li>Username: <code>root</code></li>
  <li>Password: <code>root</code></li>
  <li>Click <b>Install Now!</b></li>
</ol>
You should see a success message and be redirected to the login page:
<code>http://localhost/osTicket/scp/login.php</code>

<img width="1440" alt="Screenshot 2025-06-03 at 3 16 06 PM" src="https://github.com/user-attachments/assets/9ccfa4e4-c699-487f-875e-afd37e97ab30" />

</p>
<br />

<h3>10. Post-Installation Cleanup</h3>
<p>
<ol>
  <li>Delete: <code>C:\inetpub\wwwroot\osTicket\setup</code></li>
  <li>Set <code>ost-config.php</code> permissions to <b>Read-only</b></li>
</ol>
</p>
<h2>Conclusion</h2>
<p>
Congrats! We have now finished the osTicket setup. We have now worked with IIS, MySQL,and PHP. We have now done the framework to install osTicket. </p>
<p>
  Now that osTicket is running, we are ready to manage support tickets and explore more advanced features.
</p>

<br />

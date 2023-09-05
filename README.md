# DNS-Intuition

<p align="center">
<img src="https://i.imgur.com/CtGfsq8.png" alt="osTicket logo"/>
</p>

<h1>Building Intuition for DNS</h1>
In this lab, we will be experimenting with DNS. This lab will help us have a better understanding of DNS.<br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- DNS

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)

<h2>List of Prerequisites</h2>

- Active Directory Virtual Machine
- Client Machine joined to your domain

<h2>Lab Steps</h2>
<p>
</p>
<p>
  
We will initially examine the server's DNS A-Records. Hostname to IP address mappings are stored in a record. On DC-1, an A record for "mainframe" will be set up, pointing to DC-1's private IP address. Without creating the DNS record, pinging the mainframe will not be successful. Pinging "mainframe" causes Client-1 to examine the DNS cache, its local host file, and the DNS server. Go to AD->Tools->DNS->DC-1->Forward lookup zones->mydomain.com and right-click to create a new A record with the name mainframe as its value. Hostname to IP address mapping is known as an A record. We will receive a response if we return to the client machine and ping the mainframe. 
</p>
<br />

<p>
<img src="https://i.gyazo.com/57306d4210343fc80e71adb88eaa86e2.png" height="80%" width="80%" alt="Step 1"/>
</p>
<img src="https://i.gyazo.com/46c61778508d2a92e26a49d08e4b3387.png" height="80%" width="80%" alt="Step 2"/>
<p>
When we return to the client machine after changing the record address of "mainframe" to 8.8.8.8, the previous address will still be pingable. This is due to the need to perform the command ipconfig /flushdns to flush the DNS. When we try to ping the mainframe again, the address of the new record will appear because that will empty the DNS cache. 
</p>
<br />
<img src="https://i.gyazo.com/422d35cab4fc89d7e472bb53818d636f.png" height="80%" width="80%" alt="Step 3"/>
</p>
<img src="https://i.gyazo.com/e061c096d480859b12cf41b109560838.png" height="80%" width="80%" alt="Step 4"/>
</p>
<p>
Finally, we will set up a CNAME record to direct the host "search" to "www.google.com". Ping won't be able to locate the host if we use the "search" option. We need to create the CNAME record "search" in the DNS tool on DC-1 once more. When we ping "search" after creating the CNAME record, it resolves to www.google.com.
</p>
<br />
<p>
<img src="https://i.gyazo.com/d4296d6f7239624f09e96288721d51af.png" height="80%" width="80%" alt="Step 5"/>
</p>
<img src="https://i.gyazo.com/2208b3436cfc4f1cf5d3673dc2a08456.png" height="80%" width="80%" alt="Step 6"/>
<p>

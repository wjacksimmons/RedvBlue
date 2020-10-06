Red vs Blue


Overview
In Red vs Blue, a Kibana stacked web server was attacked using various penetration testing methods. Upon gaining access to the server, a flag was discovered. After this, a Kibana stack was used to find baselines and traces for the attack. 

Attack Summary
* Run nmap scan on the network to find host and open ports.
* Use dirbuster or enumeration to find hidden folder.
* Enumerate a login ID from the server.
* Brute force login using Hydra.
* Crack sysadmin password hash.
* Load reverse shell payload to the server using sysadmin.
* Secure shell into sysadmin account to attain root privileges.

Prevention:
* Set an alert to trigger any time the secret_folder is accessed, or remove this from the server altogether.
* Set an alert for 401 errors with a reasonable threshold (15 per hour).
* Set an alert if user_agent.original includes “Hydra”.
* Set a maximum login attempt number per IP per hour. Auto drop traffic from any requests from a login that exceeds that number.
* Since the webdav folder should only be accessed from one machine, ensure that it only accepts traffic from that one machine. 
* Connections to the shared folder should not be accessible via web browser.
* Set an alert for any .php file shared over the server. 
* Remove ability to upload files over web browser.

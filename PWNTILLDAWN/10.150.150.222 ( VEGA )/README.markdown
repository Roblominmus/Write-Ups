# 10.150.150.222 (VEGA) - PWNTILLDAN WRITEUP
Found some open ports with `rustscan`

![rustscan](images/rustscan.png)

---

Served it to `nmap`

![alt text](images/nmap_brief.png)
-
![alt text](images/nmap_full.png)

---

I went to the webiste hosted on port 80 but found nothing particularly interesting.  
After some fuzzing i found a readable `.bash_history` file on the web service and found a FLAG along side some ssh login details.

![alt text](images/bash_history.png)

---

Shell.  
Found the next flag.  

![alt text](images/ssh.png)

---

All that is left now is PrivEsc.  
Ran `sudo -l` and saw i could run all commands. Proceeded to run `sudo su` ad get the flag.  

![alt text](<images/last flag.png>)

---
Done.


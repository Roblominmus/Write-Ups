# 10.150.150.57 ( MORTY ) - PWNTILLDAWN WRITEUP 

Initial scanning with `rustscan`

![alt text](images/rustscan.png)

---

Served to `Nmap` 

![alt text](images/nmap.png)

---

The site had only the `note.html` in it. The notes seemed to mention a webisite being hosted on the machine. This seems to be a hint to update the hosts file.

![alt text](images/site.png)
![alt text](images/note.png)

---
Updated the `/etc/hosts` file and navigate to the site.

![alt text](images/msite.png)

This is obviously a password. 

---
Furthermore, we have an image so `steganography` is suspected.  
We download the image and use `steghide` to extract whatever infromation we can.  

![alt text](images/steg.png)

We were prompted for a passphrase and thankfully the password in the html page worked.  

---

The information extracted seems to be login credentials, and from our initial scanning it's somewhat obvious that it should be used for the ssh.

![alt text](<images/ssh fail.png>)  

No dice. 

--- 

Used `dig` to look around and found something interesting.

![alt text](images/dig.png)

---

From the previous results, I think a `zone transfer` is in order.

![zone](images/zone.png)

Simply Lovely, we found another site. This is quite typical in `CTFs`.

---

Next, we update the `/etc/hosts` file and navigate to the site.  
The site took us to a `phpmyadmin` page. And as per usual we were met with a login page and a beautiful flag.  

![phpadmin](images/login.png)  

---
Next up we input the login details gotten previously and hope for the best.  

![alt text](images/dashboard.png)  

It worked, and we got another flag for our troubles.  

---
There is an old version of `phpmyadmin` in use which has a known `RCE` exploit available.  
[CVE-2018-12613](https://www.exploit-db.com/exploits/50457)  
![alt text](images/exploitdb.png)  

---
We downloaded it, configured what needed configuring and ran it as specified in the `usage` section of the script.  
![alt text](images/rce.png)

It worked.  

---
Next step is to run a `reverse shell` ( gotten from [here](https://www.revshells.com/))and get a shell in the system itself.  

![alt text](images/rshell.png)  

---

Now, we just find and cat out the flag.  
![alt text](images/flag.png)

---

Done.
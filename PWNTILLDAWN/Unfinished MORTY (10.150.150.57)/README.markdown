# 10.150.150.57 ( MORTY ) - PWNTILLDAWN WRITEUP 

Initial scanning with rustscan

![alt text](images/rustscan.png)

---

Served to Nmap 

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
Furthermore, we have an image so steganography is suspected.  
We download the image and use steghide to extract whatever infromation we can.  

![alt text](images/steg.png)

We were prompted for a passphrase and thankfully the password in the html page worked.  

---

The information extracted seems to be login credentials, and from our initial scanning it's somewhat obvious that it should be used for the ssh.

![alt text](<images/ssh fail.png>)  

No dice. 

--- 

Used `dig` to look around and found something interesting.

![alt text](images/dig.png)

This points at possible `zone transfer`.
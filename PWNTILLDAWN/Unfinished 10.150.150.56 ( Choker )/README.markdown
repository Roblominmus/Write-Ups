# 10.150.150.56 ( CHOKER ) - PWNTILLDAWN WRITEUP

Results gotten from a `rustscan`.  
![alt text](images/rustscan.png)  

--- 
Served to `nmap`.  
![alt text](images/nmap.png)  

---
The http site was nothing particularly special.  
![alt text](images/page.png)  

Did some fuzzing and found nothing.  

---
Ran `smtp_version` and `smtp_enum` modules on metaploit and got a few usernames.  

![alt text](images/smtp_enum.png)  

---
Added all the usrenames to a wordlist and used `hydra` to bruteforce `pop3` and `imap`.  
Used a few wordlists but nothing really worked.  
Decided to run the list of users against itself and it worked.  

![alt text](images/hydra.png)

---

After logging in and looking around the messages a password was found.  

![alt text](images/pop3.png)

---
Proceeded to ssh into the account using the discovered pasword and it worked.  

![alt text](images/ssh.png)

---
Got the first flag, all that remains is Privilege Escalation.  

![alt text](<images/flag 1.png>)  

---

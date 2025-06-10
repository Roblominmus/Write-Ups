# 10.150.150.18 ( SNARE ) - PWNTILLDAWN WRITEUP

Results from `rustscan` 

![alt text](images/rustscan.png)

---
Served to `nmap`

![alt text](images/nmap.png)

---
Visited the site and found out there was `SSRF` possible.

![alt text](images/page.png)

---
Configured a `webshel`l, hosted it, started a `netcat` listener and navigated to the hosted webshell.

![alt text](images/webshell.png)

---
Shell Acquired

![alt text](images/shell.png)

---
Looked around and found a flag

![alt text](images/flag.png)

---
All that is left is `PrivEsc`

Ran `linpeas` and discovered a writable `/etc/shadow/` file

![alt text](images/linpeas.png)

---
Used AI to find a way to remove the password for root then switched to root.

![alt text](images/root.png)

---

Found the final flag.

![alt text](images/final.png)

---
DONE.
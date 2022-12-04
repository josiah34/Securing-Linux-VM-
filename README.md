# Securing-Linux-VM-
##### Table of Contents  
* [Objective](#objective)
* [Steps](#steps)
* [References](#references)   

<a name="objective"/>

## Objective 
![download](https://user-images.githubusercontent.com/25124463/205220194-b9abc6db-8555-4dfa-acce-f2d98d162b32.png)

I will be creating an Ubuntu VM on Linode in order to practice securing and hardening a linux server. 

<a name="steps"/>

## Steps
1. Creating my Linode Ubuntu VM


![creating-vm](https://user-images.githubusercontent.com/25124463/205230535-ae0565d2-a472-41c1-9e84-ef7b979811a2.jpg)

2. On boot I'm able to login as root and with password authentication. A big security risk I will be changing. 

3. The first thing I will be doing is doing updates on the vm.
``sudo apt get-update`` ``sudo apt get-upgrade``

![updates](https://user-images.githubusercontent.com/25124463/205233071-b5356315-5037-4fbb-bae1-4279967967f2.jpg)

4. Next I'll create a sudoer account so that I can login without using root. <br>
 ``adduser admin`` **Creating the new user**<br>
 ``usermod -a -G admin`` **Adding new user to the sudo**
 ![new user](https://user-images.githubusercontent.com/25124463/205456533-dde3ba45-eed9-4256-b054-c8d1775c5234.jpg)
 
 
![sudoer-user](https://user-images.githubusercontent.com/25124463/205456562-6f906bb2-e915-40a6-97f5-8bdfcbbd00b8.jpg)

5. After this I will upload my ssh key from my local machine to the Ubuntu VM using the ``ssh-copy-id admin@virtualmachineip``

6. Next I'll open the ssh config file located at ``/etc/ssh/sshd_config`` and disabling the following:
* Disabling Password Authentication
* Disabling root login
* Only allowing ssh access to ipv4 ips as I will not be connecting using ipv6 ips. 

7. Restarting ssh service 

```
sudo service sshd restart

```


8. Next I'll install and setup unattended upgrades so that my Ubuntu VM will automatically install important security updates. 


9. For the last step I will install a firewall called ufw which blocks all incoming connections. To ensure I still have access to my VM I will allow ssh to pass through its filters. 

```
sudo apt install ufw
sudo ufw allow ssh

```

After that is done I will install another application called Fail2Ban which will block ips that exhibit suspicous behaviour like multiple failed authentication attempts.



 
 
<a name="references"/>

## References

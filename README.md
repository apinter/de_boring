# De-Boring
## Digging tunnels making local services publically available.

## Requirements
### Step 1
Install ```autossh```   
   
``` 
apt-get install autossh
zypper in autossh
yum install autossh
dnf install autossh   
```   

### Step 2
Modify the ```ssh-tunnel``` file accordingly your setup (username and ip address, you can also change the ssh port if needed)   
Copy the modfied ```ssh-tunnel``` file to /usr/bin

### Step 3
If you want to automate the whole process generate ssh key pair on your client where the tunnel starts: ```ssh-keygen -t rsa -b 4096``` and copy it over the server so you don't need to sign in all the time: ```ssh-copy-id user@ip```.

### Step 4 
Copy the ```ssh-out.service``` unit to /etc/systemd/system or wherever you store your custom unit files and enable it: ```systemctl enable --now ssh-out.service```.

### Step 5 
Start a Digital Ocean server and install nginx

### Step 6
Modify the ```de-boring.conf``` example reverse-proxy config for nginx accordingly to your needs (domain name, port(s) etc.)  and copy it to a folder where nginx can read it from. (I usually have a conf.d folder and include it under the nginx.conf file)

### Step 7
Check if the config is correct with ```nginx -t``` and start and enable nginx ```systemctly enable --now nginx```

### Step 8 
Profit ;)

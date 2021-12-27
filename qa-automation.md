## Setting up newman via npm (nodejs.14) on RHEL 7 with forward proxy enabled.

1. In order to gain internet access you must add environment variables **"https_proxy, http_proxy, proxy**
```export <env name>=<proxy url>```
2. You must enable rhcl repo in order to install node.js
``` enable rhcl in /etc/yum.repos.d/redhat.repo```
3. After enabling **redhat.repo** search for available nodejs packages 
```sudo yum search nodejs```
4. Install latest version available ie.
```sudo yum install rh-nodejs14```
5. Now node and npm is installed but not accessible via command line.
In order to test if node & npm is installed use this on terminal (bash)
```run scl enable rh-nodejs14 bash```
6. Now run node --version & npm --version. Node should be accessible but it is still accessible only in the current session, if you rejoin the ssh session it would not work to make it persistent for the current user add the command in **".bashrc** file.
``` vi ~/.bashrc and add source scl_source enable rh-nodejs14```
7. To make npm & node accessible for all users create a symlink for the installed package to /usr/local/bin
Path for installed package ```/opt/rh/rh-nodejs14/root/bin```
Create symlink ```ln /opt/rh/rh-nodejs14/root/bin/node /usr/local/bin/node
ln /opt/rh/rh-nodejs14/root/bin/npm /usr/local/bin/node```
Run to verify ```readlink /opt/rh/rh-nodejs14/root/bin/node```
8. Now node and npm would be accessibly by **TFS Agent**

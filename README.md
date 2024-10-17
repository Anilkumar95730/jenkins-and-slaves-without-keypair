# Establish the connection b/w Jenkins master and Slave servers without key pair: 

Create the two ec2 instance one for Jenkins master with key pair and another for slave server without key pair(take t2.medium). 
    



Install the java and Jenkins on master server and install the only java(java 17)on slave server. 

Go to .ssh folder and generate the public and private key by using ssh-keygen command. 

Enter ll command and it shows public and private keys. 

Open the public key by using cat publickey name command and copy this public key and paste it on slave sever at authorized keys file in the  root user. 

Log into Jenkins dashboard and go to manage Jenkins > Nodes. 

Create the node and while configuration  of the node we can add the user name as root and paste the private key (we can generate in the master server). 

Create the job like freestyle or pipeline and we can select and give node label name at Restrict where this project can be run option. 

Click on add buils step option and click on execute shell and write the shell script.Click on apply and save option.Click on Build now option.









# Backup the Jenkins by using thinbackup plugin:

Inside the .jenkins folder (which is available on /var/lib) all the information about Jenkins like jobs,nodes,plugins,config file,secrets etc.is available.
 
 We need to backup the .jenkins to the other folder(create new folder) or external service like store the data on ebs volumes by using thinbackup plugin.

Create the one directory(backupfolder) in opt directory for backup the data on master server.

Change the ownership and group name by using chown username:groupname foldername command.
                   Ex: chown Jenkins:Jenkins backupfolder 
              
	
 Change the file permissions by using chmod 777 foldername command.

Go to Jenkins dashboard and go to managed Jenkins > plugins install thinbackup plugin if it is not available.

Thinbackup plugin is available under Tools and Actions section.

After installation configure the this plugin on system configuration section.

We need to give the directory name(/opt/directoryname in this case) where we want to store the backup data while configuration of thinbackup plugin.
 
Go to tools and actions section click on thinbackup plugin and click on backup now option.

Data will be store at that directory which we have mentioned  while configuration in the system configuration section.


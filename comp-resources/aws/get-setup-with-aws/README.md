# Obtaining access
As mentioned in the general info, most users use AWS for two main services: EC2 and S3.  EC2 is what provides users with computing 'instances', which can be viewed as nodes with a requested number of CPUs, RAM, and disk space.  S3 is for storing data.

## Accessing EC2 instances (e.g. Alm lab node)
These instances can be viewed as regular Linux-operated computers which can be accessed with an IP and an SSH key.  You can obtain both from the systems administrators (currently Thomas and Xiaofang).  Note that both of these pieces of information are private and, for security reasons, should not be shared with anyone without explicit permission.  The SSH key should never be sent by email, and should reside somewhere safe on your computer.  Below we review the access procedures for accessing EC2 resources from Linux and Windows machines.

### Access from Linux/MacOS
This is the easiest way.  To log on to an instance with IP 9.9.9.9 and associated SSH key _login_key.pem_, open a terminal and type the following (replacing /path/login_key.pem with the full path to your SSH key):

```
ssh -i /path/login_key.pem ubuntu@9.9.9.9
```

Similarly, you can copy files to and from the instance using scp:

```
scp -i /path/login_key.pem myfile.txt ubuntu@9.9.9.9:/home/ubuntu/myfile.txt
```	
 
Note: if you have previously logged onto an instance with that IP and the IP has now been associated with a different instance, your SSH manager will complain.  If you get an error, check your ~/.ssh/known_hosts and remove the line with that IP, then try again.

Note: Your SSH manager may also complain if your key has the wrong permissions. If you get an error about permissions, you can change them using chmod:

```
chmod 400 /path/login_key.pem
```

### Access from a Windows machine
In this case, you will need an SSH client.  We recommend PuTTY.  You will also have to convert the SSH key from PEM to PPK format using the PuTTYgen program, since PEM keys cannot be loaded into PuTTY.  Both PuTTY and PuTTYgen are available for free online.  Once you have done this, log in to the node by using username 'ubuntu', setting your IP, and loading the PPK key.

To copy files to and from the instance from Windows, you will need an SCP client.  We recommend WinSCP.  This will operate in the same manner as PuTTY.  Simply set the username to 'ubuntu', the IP, and load the PPK key.


## Accessing storage space on S3
S3 can be accessed in two manners, command line and GUI.

### Access via command line
To upload/download files from S3 using a terminal, you will need to install the 'AWS CLI' (CLI: command line interface).  Once you have this installed, type

```
aws configure
```
and you will be asked for an access key, a secret access key, the default region, and the default output format (the latter should be left blank, just press Enter).  On common lab resources (e.g. Alm lab nodes on EC2), these should be pre-configured and you don't need to install or configure the CLI.  On your home computer or laptop, you will need to obtain these keys from the systems administrators.  Once you have the CLI configured, you can use variants of the usual unix commands 'cp', 'ls', 'rm', as well as 'sync' (equivalent to 'rm -r', for folders) in the generic format 'aws s3 COMMAND FROM TO', e.g.

```
aws s3 ls s3://almlab.bucket/
aws s3 cp myfile.txt s3://almlab.bucket/username/myfile.txt
aws s3 cp s3://almlab.bucket/myfolder/username/myfile.txt myfile.txt
aws s3 sync /home/myfolder s3://almlab.bucket/username/myfolder
```

Note: please be careful when using the CLI.  The Alm lab have several public buckets where lab members store their data, so please _THINK_ before you use commands like 'aws s3 rm'!

### Access via GUI
You can also access S3 buckets via a GUI on the AWS console.  To log on to the AWS console, you need a username and password.  These can also be set by the systems administrators.

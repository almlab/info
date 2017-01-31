# AWS Common Use Standards

## Computing in the Alm lab

Lots of people in the Alm lab do compuational work. We have multiple resources at
our disposal, the biggest of which are coyote and AWS.

coyote is adminstrated by \[greg\] (alm-admin[at]techsquare[dot]com). We pay to share this
resource with a few other MIT labs. coyote has a different set of standards and use
which are not covered in this document.

AWS is administrated by Thomas Gurry (thomasgurry[at]gmail[dot]com) and Xiaofang Jiang (xiaofang[at]mit[dot]edu).
The Alm lab pays for everything related to our AWS usage, and Thomas and Xiaofang
are basically volunteering their time to administer this common resource.

We have a Moira email list for computational-related things, alm-comp[at]mit[dot]edu.
You can add or remove yourself from this and other Moira lists at: groups.mit.edu/webmoira/ .


# Introduction to AWS

## What is AWS?
AWS is Amazon's cloud computing platform. "Cloud" means: de-localized data, pay-per-use
service model, and options to have extra layers of tools for high performance computing.

AWS is pretty bare bones: it's really just a bunch of datacenters containing CPUs+RAM (EC2)
and hard drives (EBS and S3) connected by ethernet cables.  The added value is in the software,
administrative tools, database management systems and general flexibility that using AWS provides.

The major benefit to using AWS is that you can essentially trade time for money. Which brings us to
the next point:

## AWS costs money!

Everything we use AWS for costs money. The almlab node is used enough that we'll leave it running
at all times, but if you're using an EC2 instance for something else that's specific to your work,
please make sure to turn it off when you're not using it!

## Pros and cons

Using AWS has some sweet pros and very real cons.

Pros:
- We all have sudo access, and don't need to wait on an admin to install new things.
- AWS is super flexible, so if you need a customized instance for a specific project
or task, that's really easy to do.
- We generally have low enough usage that there's no need to set up a queue for jobs

Cons:
- We all have sudo access, and therefore can all accidentally screw things up 
- The tragedy of the commons

# Data storage
AWS users are asked to keep their data storage on active instances (e.g. the almlab node) to a minimum.
If you are not actively using data, please move it to the almlab bucket on S3. From the almlab node, you
can type the following command:

```aws s3 cp file_to_copy.txt s3://almlab.bucket/your_user_name/destination_file_name.txt```

If you're not sure how much space you're taking up on the node, you can check data usage with the
following command, from the ```~/users``` directory:

```du -h --max-depth=1```

# Installing things
If you need to install new software that will be generally useful to the lab, you can put it in
```/home/ubuntu/bin``` (if it is a binary) or ```/home/ubuntu/tools``` (if it is an executable).
If you aren't sure, just put it in ```/home/ubuntu/tools``` or your own user directory.

If you need to install new Python packages, use ```conda install``` first. Note that ```conda install```
will automatically install the Python 2 version of your package. If you need to install a Python 3
version, you should type ```conda3 install```. If ```conda``` can't find what you need, you can
also try ```pip install``` or ```easy_install``` or your other favorite installer.


# Safeguarding your work

In agreeing to use this shared resource, you accept that sometimes mistakes
will happen that may affect your work. With this in mind, it's important that
you safeguard your work so that nothing that someone else (or you, lol) accidentally
does spells disaster for your research.

In a similar vein, you also recognize that we are a community of actively learning
researchers, and agree to act in a way that reflects this shared ethos. This means
asking questions when you aren't sure about something, communicating about problems
and improvements with your peers, and generally assuming that everyone is acting in
good faith as well as you yourself also acting in good faith when using this common
resource.

## Virtual environments
We highly encourage all users to use [virtual environments](https://github.com/almlab/info/tree/master/comp-resources/computing/virtual-environments)
when doing coding work. Virtual environments will prevent dependency conflicts that unexplicably
break your code (i.e. if someone updates a package that your code needs an older version of).
Using virtual environments is also a great way to keep track of your work and the dependencies that
it requires to run, which means that if everything gets messed up it shouldn't take you too long
to get back up and running!

## Back up your work, you fool!
Speaking of getting back up and running after everything is messed up, make sure you're backing up
your work! You can use [```git```](https://github.com/almlab/info/tree/master/comp-resources/computing/github)
to version control and back up your code.

As mentioned above, you should be storing most of your data on S3. You can also consider having
another back up of your data somewhere else. As MIT affiliates, we get free access to
[Dropbox Business](https://ist.mit.edu/dropbox) AKA we get unlimited Dropbox storage for free.
It's really easy to set up, and you should probably use it for any non-github stuff you have.

## Terminal multiplexers

Using a terminal multiplexer to hide your running processes from the masses is a good way
to prevent anyone from accidentally interrupting your running code. (Note that it's not
always foolproof, and sometimes people accidentally stop jobs they think is theirs but isn't).

If you're using something like ```screen``` or ```tmux```, make sure to name your sessions
or forever hold your peace (if someone else changes/deletes them).

# Other resources

[This repository](https://github.com/almlab/info) will hopefully serve as the central hub
for all Alm lab-related resources. If something is missing, please add it!

If you have a specific question and don't want to spam the whole almlab email list
list, you can email alm-comp[at]mit[dot]edu.

Finally, please try to label your data and work in a way that other humans can
understand. This will help current and future Almstars who may need to look at
what you've done to understand something important about their or your #science.

# Commitment

By reading and signing this document, you agree to:

1. Do your part to minimize potential tragedies of the commons related to shared Alm lab AWS usage.
2. Minimize your data storage on running instances, and respond to clean-up requests when they are sent.
3. Minimize any monopolozing of computational resources on the almlab node, for example by booting
a new node for your most computationally demanding tasks.
4. Expect the best while preparing for the worst (AKA assume that things will be fine and also
back up your work just in case it isn't).

# Obtaining access

As mentioned above, most users use AWS for two main services: EC2 and S3. EC2 is what provides users with computing 'instances', which can be viewed as nodes with a requested number of CPUs, RAM, and disk space. S3 is for storing data.

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
and you will be asked for an access key, a secret access key, the default region, and the default output format (the latter should be left blank, just press Enter).  On common lab resources (e.g. Alm lab nodes on EC2), these should be pre-configured and you don't need to install or configure the CLI.  On your home computer or laptop, you will need to obtain these keys from the systems administrators.  Once you have the CLI configured, you can use variants of the usual unix commands 'cp', 'ls', 'rm', as well as 'sync' (more info [here](http://docs.aws.amazon.com/cli/latest/reference/s3/sync.html)) in the generic format 'aws s3 COMMAND FROM TO', e.g.

```
aws s3 ls s3://almlab.bucket/
aws s3 cp myfile.txt s3://almlab.bucket/username/myfile.txt
aws s3 cp s3://almlab.bucket/myfolder/username/myfile.txt myfile.txt
aws s3 sync /home/myfolder s3://almlab.bucket/username/myfolder
```

Note: please be careful when using the CLI.  The Alm lab have several public buckets where lab members store their data, so please _THINK_ before you use commands like 'aws s3 rm'!

### Access via GUI
You can also access S3 buckets via a GUI on the AWS console.  To log on to the AWS console, you need a username and password.  These can also be set by the systems administrators.

You can sign in at [aws.amazon.com](https://aws.amazon.com) or, if that doesn't work, using the following alias:
[https://cmit.signin.aws.amazon.com/console](https://cmit.signin.aws.amazon.com/console).
# AWS Common Use Standards

## Computing in the Alm lab

Lots of people in the Alm lab do compuational work. We have multiple resources at
our disposal, the biggest of which are coyote and AWS.

coyote is adminstrated by \[greg\] (alm-admin@techsquare.com). We pay to share this
resource with a few other MIT labs. coyote has a different set of standards and use
which are not covered in this document.

AWS is administrated by Thomas Gurry (thomasgurry@gmail.com) and Xiaofang Jiang (xiaofang@mit.edu).
The Alm lab pays for everything related to our AWS usage, and Thomas and Xiaofang
are basically volunteering their time to administer this common resource.

We have a Moira email list for computational-related things, alm-comp@mit.edu.
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

## How to get setup or obtain access

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

If you have a specific question and don't want to spam the whole almlab@mit.edu
list, you can email alm-comp@mit.edu.

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

# Files
- README.md - this document, which contains the AWS Common Standards that all AWS users must
read and sign before being given access to these computational resources.
- AWS_workshop_slides.pdf - slides from Thomas's workshop in March 2016 going over basic AWS
info, why we use AWS in the Alm lab, connecting to AWS, and basic troubleshooting.

# Contributors
- Claire Duallet, 11/14/2016
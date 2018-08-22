# Setting up an rstudio server node on AWS
author: @nathanieldchu
date: August 22, 2018

[RStudio](https://www.rstudio.com) is a pretty sweet interface to the R suite of tools, but sometimes you don't want to run things on your personal computer.

In comes [RStudio Server](https://www.rstudio.com/products/rstudio/download-server/), which allows you to run RStudio on a remote server but still access and manipulate your R session using the same RStudio interface in a web browser. It's pretty slick.

To do this with AWS, the laziest and best way to do it is to use once of the community AMIs hosted on AWS. While Amazon itself maintains a family of standard AMIs with which to initiate an EC2 instance, there are a ton of other AMIs which are maintained by randos out in the ether.

I used the most current rstudio server AMI [maintained here](http://www.louisaslett.com/RStudio_AMI/). You can also simply search for "rstudio" in the AWS interface and see what options there are. They ought to state the version of R being used and other global characteristics.

Steps:

1. Login to the AWS interface and launch a new instance.
2. Choose appropriate parameters for your needs (likely not much if you are using RStudio) and choose an AMI that is specific to RStudio.
3. Once the instance in launched, in the case of the AMIs [referenced here](http://www.louisaslett.com/RStudio_AMI/). You'll then need to change your rstudio server login password. ssh into the new instance using your AWS key and type the following code : `sudo passwd rstudio`. This will then prompt you to enter a new password.

To access your rstudio interface, you can then copy the [Public DNS (IPv4)](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/using-instance-addressing.html) from the AWS console and enter this value into any web-browser. You should be prompted to enter a username and password, which in this case is username: 'rstudio' and the password is whatever you set it to.

Once logged in, you now have a standard RStudio interface and access to all files attached to the AWS instance. to load in your files, I suggest [making a new volume](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ebs-creating-volume.html), transferring files to it, and then [attaching it](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ebs-attaching-volume.html) to your rstudio instance.
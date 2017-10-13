## If you just want to access jupyter, run:
> jupyter notebook

Then on your laptop, got to https://ip-address:8888
(replace ip-address with our AWS IP address, host is currently 8888, that could change)

If you want the notebook to continue running after you log off, remember to run 
> nohup jupyter notebook

<br><br>
### If you need to fix something, I followed this tutorial to get setup.
To fix things, you might need to look at this directory (I did): */home/ubuntu/.local/share/jupyter*

Another file that might need editing to fix things: */home/ubuntu/.jupyter/jupyter_notebook_config.py*

Taken from tutorial here: 
https://medium.com/@GalarnykMichael/aws-ec2-part-4-starting-a-jupyter-ipython-notebook-server-on-aws-549d87a55ba9

1.) Log into aws

2.) get SHA key from ipython

> ipython

> from IPython.lib import passwd

> passwd()
Enter password: #Type here
Verity password: #Type here
out[2]: 'sha1:blahblahlbblahthisisyourkey'

2.1.) Copy that SHA key

3.) Generate jupyter config file, make certificate in home folder (or elsewhere)

> jupyter notebook --generate-config

> mkdir certs

> cd certs

> sudo openssl req -x509 -nodes -days 365 -newkey rsa:1024 -keyout mycert.pem -out mycert.pem

> cd ~/.jupyter/

4.) Open the file jupyter_notebook_config.py and type:
> c = get_config()

> c.IPKernelApp.pylab = 'inline'

> c.NotebookApp.certfile = u'/home/ubuntu/certs/mycert.pem'

> c.NotebookApp.ip = '*'

> c.NotebookApp.open_browser = False

# Your password below will be whatever you copied earlier
> c.NotebookApp.password = u'sha1:thatthingyoucopiedearlier'

> c.NotebookApp.port = 8888

5.) Run 
> nohup jupyter notebook

6.) https://ip-address:port/ to access jupyter

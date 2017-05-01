Virtual environments are in your self-interest.
They track which packages your code
depends on and creates an environment
of your own.

No more worrying that Jimmy Switchblade
upgraded AWS to Python v17.3, when all your 
stuff runs on v1.3!

# Overview of virtual environments

There's a hierarchy of virtualization possible
for your code, virtual environments solves some
problems associated with making code shareable 
and portable.

## Basic hierarchy of containerization:

Hardware level > Operating System > Program Level

Examples:
Memory and HDD > Windows v. Unix > Python v3 or v2

Technical names (google them if you want to know more):
Virtual machine > Docker Container > Virtual Environments

So virtual environments solve some problems. They'll let 
you run the right python code and packages, but won't help
you port that code from a unix environment to windows. There 
are other systems level issues you could run into that a 
virtual environment can't solve, too. Maybe AWS has a 
different C compiler than your laptop, and that screws things up.




# File list
- virtualenv_workshop.pdf (Isaac's workshop - a quick description and exercise using conda)
- virtualenv_cheatsheet.pdf (a commandlist you can reference)

# Contributors
- Isaac 

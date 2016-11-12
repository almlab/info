Github is great to share code, keep code and text files under version control, and
back up your files.

# The basics

```git``` is a software that is used for version control. GitHub is a web-based repository
hosting service that uses ```git``` to enable users to organize and track their code.

Repositories are basically git-aware directories: they store files as well as the history of
changes made to those files. Usually, different projects are in different repositories.

The staging area is the place in-between your local working directory and the repository.
When you make changes to files on your computer, you ```add``` those changes to the
staging area. The staging area is like a holding cell for changes that you've made, before
you've committed them to the repository. Once you've added all the files you want to the staging area,
you wrap them up together with ```commit```. Now you're committed to those changes, and
you finalize them by ```push```ing them to the repository.

In life and in git, the opposite of ```push``` is ```pull```. When you ```pull```, you're basically
updating the files in your current working directory to match the state of files in the repository (i.e.
"pulling" all the changes from there to here).
If you're just one user always working from the same place, you shouldn't ever really need to ```pull``` - 
there's no reason that anything in your repository (over there) would have changed between your last ```push```
and now. However, if you're working on multiple computers or you're working in a repository that others are also
contributing to, you should always ```pull``` before you start your work, just to make sure that the current
state of the files you're working on match what's in the repository. If you forget to do this, git will
complain when you try to ```push``` your changes. 

There are a lot of more complicated things you can do with git, but these are mostly used
when you're actively collaborating with others on code. If you're just using it to keep
track of your own code or to make infrequent changes to a shared repository (like this one!),
you should be fine.

The most important thing to remember in these cases is to always ```pull``` before you start working.

The learning curve for using ```git``` can be quite steep, but it is totally worth it and
will make you a more productive member of the computational community.

## What can you use git for?

You can technically use git for everything, but it is specifically designed for text files.
The way git tracks changes is essentially by ```diff```ing all of your files, and finding
the lines that are different between the last time you committed changes and now. This works really well
for text files, and not at all for non-text files (i.e. binary files like .doc, .ppt, and .xls).
Not to worry though, you can still have these files in your repositories! It's just that every
time you make a change, git just re-writes the whole file (rather than just changing the couple
lines you changed).

Note that there is a [file size limit](https://help.github.com/articles/what-is-my-disk-quota/)
to what you can include in your repository. git complains
when you try to ```push``` files that are larger than 50 MB. It does not let you ```push```
files larger than 100 MB. 

# Github.com and Github Enterprise

As MIT affiliates, we have access to both normal github.com
as well as github Enterprise (github.mit.edu).

From what I understand, the main differences between github.com and Github Enterprise
have to do with security and hosting-related features, which likely don't affect you
as a normal user. The most practical difference is that Github Enterprise offers
unlimited private repositories, whereas github.com does not. Github Enterprise also
uses MIT's security credentials, which means that you sign on using your certificates
(rather than by typing in a password).

[This](https://enterprise.github.com/downloads/en/comvsenterprise-082415.pdf) file provides
a pretty good overview of the differences, and Github's [FAQ](https://enterprise.github.com/faq)
is also sort of useful to understand the differences.

## Pros and cons

For the most part, the two types of github are pretty equivalent. Both types of accounts can
contribute to public repos. Both your mit.edu and other email addressed can be associated with
either type of account.

The only difference is if you're trying to add a collaborator to a private Enterprise repo. In this case,
the person needs an Enterprise account in order to be added as a collaborator. 

### github.com

Pros:
- easy to collaborate with anyone

Cons:
- limited number of private repos (unless you sign up with your .mit.edu email address? Not sure.)

### github.mit.edu

Pros:
- unlimited free repos
- uses MIT's security stuff

Cons:
- can't add non-Enterprise members as collaborators on private repos

Gotchas:
- sign in is done with certificates, so if you're ever asked for a password to sign in, you'll
need to set up a security key instead (I think, please update if you encounter this issue and figure it out)


# Contributors
- Claire Duvallet, 11/12/16
# computing

##### Table of Contents  
[Github](#github)  
[NCBI Entrez Queries](#ncbi-entrez-queries)   
[Virtual Environments](#virtual-environments)   
[Downloading from SRA](#downloading-from-sra)   

# Github

Github is great to share code, keep code and text files under version control, and
back up your files.

## The basics

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

### What can you use git for?

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

## Github.com and Github Enterprise

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

### Pros and cons

For the most part, the two types of github are pretty equivalent. Both types of accounts can
contribute to public repos. Both your mit.edu and other email addressed can be associated with
either type of account.

The only difference is if you're trying to add a collaborator to a private Enterprise repo. In this case,
the person needs an Enterprise account in order to be added as a collaborator.

#### github.com

Pros:
- easy to collaborate with anyone

Cons:
- limited number of private repos (unless you sign up with your .mit.edu email address? Not sure.)

#### github.mit.edu

Pros:
- unlimited free repos
- uses MIT's security stuff

Cons:
- can't add non-Enterprise members as collaborators on private repos

Gotchas:
- sign in is done with certificates, so if you're ever asked for a password to sign in, you'll
need to set up a security key instead (I think, please update if you encounter this issue and figure it out)

# NCBI Entrez queries

NCBI is a treasure trove of information.   

There are a lot of ways to interface with the various NCBI
databases. One way is to use the Entrez Direct command line tools.   

From their [documentation](https://www.ncbi.nlm.nih.gov/books/NBK179288/):

> Entrez Direct (EDirect) provides access to the NCBI's suite of interconnected databases
> (publication, sequence, structure, gene, variation, expression, etc.) from a UNIX
> terminal window. Functions take search terms from command-line arguments. Individual
> operations are combined to build multi-step queries. Record retrieval and formatting
> normally complete the process.

For example, to get the NCBI Taxonomy IDs for a given `genus`, you could do:

```esearch -db taxonomy -query "${genus}" | efetch -mode xml | xtract -pattern Taxon -element TaxId ScientificName Division```

# Virtual environments

Virtual environments are in your self-interest.
They track which packages your code
depends on and creates an environment
of your own.

No more worrying that Jimmy Switchblade
upgraded AWS to Python v17.3, when all your
stuff runs on v1.3!

## Overview of virtual environments

There's a hierarchy of virtualization possible
for your code, virtual environments solves some
problems associated with making code shareable
and portable.

### Basic hierarchy of containerization:

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

## Files
- virtualenv_workshop.pdf (Isaac's workshop - a quick description and exercise using conda)
- virtualenv_cheatsheet.pdf (a commandlist you can reference)

# Downloading from SRA

When you download data from the SRA, you need to know all of the files that you
want. This can take some clicking around, but once you land on a page that
looks like [this](https://www.ncbi.nlm.nih.gov/Traces/study/?acc=SRP040146),
then you should be good to go.

Note that if fastq-dump isn't working and it's been a while since you've used it, you might need to reconfigure your SRA toolkit:
https://trace.ncbi.nlm.nih.gov/Traces/sra/sra.cgi?view=toolkit_doc&f=std

## Using fastq-dump

`fastq-dump` in the sratoolkit will grab the file from the SRA and write
it to your system in fastq format. This is usually what you'll want.

1. Install sratoolkit on your machine and configure it.
   - http://ncbi.github.io/sra-tools/install_config.html

2. Use fastq-dump to download the SRA files and automatically convert them to fastq.
Be aware whether the data is paired end or not. If it's paired ends, you'll need to
split the spots.
    - This website has a good explanation of the flags: https://edwards.sdsu.edu/research/fastq-dump/
    - For each file in your AccessionList.txt (downloaded from the SRA website): `fastq-dump --accession SRR#######`

You'll want to download the list of accessions from the SRA (click the `Accession List`
button under `Download` on the page with the Run Table).

Then, you can just use a bash loop to download:

```
while read f
do
fastq-dump --accession $f <other flags if you want them>
done < SRA_Run_table.txt
```

## Using wget/ftp/rsync

If you have large files that are taking too long with the sratoolkit and/or breaking, you can also use `rsync`, `wget`, or something like that to get the `sra` files directly.

From http://www.ncbi.nlm.nih.gov/books/NBK158899/ :

```
{wget/FTP/rsync} {rsync | ftp}://ftp-trace.ncbi.nih.gov/sra/sra-instant/reads/ByRun/sra/{SRR|ERR|DRR}/<first 6 characters of accession>/<accession>/<accession>.sra
```
Where {SRR|ERR|DRR} should be either ‘SRR’, ‘ERR’, or ‘DRR’ and should match the prefix of the target .sra file

And then you use `fastq-dump` to convert the sra file to a fastq:

```
path/to/sratoolkit/bin/fastq-dump SRR#####.sra
```

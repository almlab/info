There are some super useful datasets out there. This repo
isn't a place to store the actual data, but rather a place to keep
the things we've learned about using and processing these data.
Hurray for not re-inventing the wheel!

# HMP

The raw data for HMP can be accessed on SRA via the run browser
([here](https://www.ncbi.nlm.nih.gov/Traces/study/?acc=SRP002395)).
Using sratoolkit's fastq-dump, it's easy to get fastq's from this.
However, it seems that some of the runs are deconvoluted whereas others
still have multiple samples in each SRR file. The "SFF and Library
Metadata File Generation" [documentation](http://hmpdacc.org/doc/SFF_LibraryMetadataFiles_SOP.pdf)
on the [HMR16S page](http://hmpdacc.org/HMR16S/) explains this.

From the "16S rRNA Processing" [documentation](http://hmpdacc.org/doc/16S_SOP.pdf)
on the [HM16STR page](http://hmpdacc.org/HM16STR/)
(trimmed data), it looks like de-convoluting these files was not trivial.

tl;dr - it's probably best to just use the trimmed, deconvoluted fasta
files in HM16STR. Thankfully Chris and Scott already did the hard work
of downloading all those files! Files and associated documentation are
on coyote: /net/radiodurans/alm/lab/data/hmp/trim/

# Case control meta-analysis datasets

As part of my (Claire's) [meta-analysis](http://biorxiv.org/content/early/2017/05/08/134031), 
I've collected and re-processed many case-control datasets from the raw data.

## Datasets

The datasets which are currently processed are:

dataset | controls | cases | N ctrls | N cases | year | paper
---------|---------|---------|---------|---------|---------|---------
asd_kang | H | ASD | 20 | 19 | 2013 | [link](http://dx.doi.org/10.1371/journal.pone.0068322)
asd_son | H | ASD | 44 | 59 | 2015 | [link](http://dx.doi.org/10.1371/journal.pone.0137725)
cdi_schubert | H, nonCDI | CDI | 243 | 93 | 2014 | [link](http://dx.doi.org/10.1128/mBio.01021-14)
cdi_vincent | H | CDI | 25 | 25 | 2013 | [link](http://dx.doi.org/10.1186/2049-2618-1-18)
cdi_youngster | H | CDI | 4 | 19 | 2014 | [link](http://dx.doi.org/10.1093/cid/ciu135)
crc_baxter | H | CRC | 172 | 120 | 2016 | [link](http://dx.doi.org/10.1186/s13073-016-0290-3)
crc_chen | H | CRC | 22 | 21 | 2012 | [link](http://dx.doi.org/10.1371/journal.pone.0039743)
crc_wang | H | CRC | 54 | 44 | 2012 | [link](http://dx.doi.org/10.1038/ismej.2011.109})
crc_zackular | H | CRC | 30 | 30 | 2014 | [link](http://dx.doi.org/10.1158/1940-6207.CAPR-14-0129)
crc_zeller | H | CRC | 75 | 41 | 2014 | [link](http://dx.doi.org/10.15252/msb.20145645)
edd_singh | H | EDD | 82 | 201 | 2015 | [link](http://dx.doi.org/10.1186/s40168-015-0109-2)
hiv_dinh | H | HIV | 15 | 21 | 2015 | [link](http://dx.doi.org/10.1093/infdis/jiu409)
hiv_lozupone | H | HIV | 13 | 23 | 2013 | [link](http://dx.doi.org/10.1016/j.chom.2013.08.006)
hiv_noguerajulian | H | HIV | 34 | 205 | 2016 | [link](https://doi.org/10.1016%2Fj.ebiom.2016.01.032)
ibd_gevers | nonIBD | CD | 16 | 146 | 2014 | [link](http://dx.doi.org/10.1016/j.chom.2014.02.005)
ibd_morgan | H | UC, CD | 18 | 108 | 2012 | [link](http://dx.doi.org/10.1186/gb-2012-13-9-r79)
ibd_papa | nonIBD | UC, CD | 24 | 66 | 2012 | [link](http://dx.doi.org/10.1371/journal.pone.0039242)
ibd_willing | H | UC, CD | 35 | 45 | 2009 | [link](http://dx.doi.org/10.1053/j.gastro.2010.08.049)
mhe_zhang | H | CIRR, MHE | 25 | 46 | 2013 | [link](http://dx.doi.org/10.1038/ajg.2013.221)
nash_wong | H | NASH | 22 | 16 | 2013 | [link](http://dx.doi.org/10.1371/journal.pone.0062885)
nash_zhu | H | NASH | 16 | 22 | 2013 | [link](http://dx.doi.org/10.1002/hep.26093)
ob_goodrich | H | OB | 428 | 185 | 2014 | [link](http://dx.doi.org/10.1016/j.cell.2014.09.053)
ob_ross | H | OB | 26 | 37 | 2015 | [link](http://dx.doi.org/10.1186/s40168-015-0072-y)
ob_turnbaugh | H | OB | 61 | 195 | 2009 | [link](http://dx.doi.org/10.1038/nature07540)
ob_zhu | H | OB | 16 | 25 | 2013 | [link](http://dx.doi.org/10.1002/hep.26093)
ob_zupancic | H | OB | 167 | 117 | 2012 | [link](http://dx.doi.org/10.1371/journal.pone.0043052)
par_scheperjans | H | PAR | 74 | 74 | 2015 | [link](http://dx.doi.org/10.1002/mds.26069)
ra_scher | H | PSA, RA | 28 | 86 | 2013 | [link](http://dx.doi.org/10.7554/eLife.01202)
t1d_alkanani | H | T1D | 55 | 57 | 2015 | [link](http://dx.doi.org/10.2337/db14-1847)
t1d_mejialeon | H | T1D | 8 | 21 | 2014 | [link](http://dx.doi.org/10.1038/srep03814)

More information about each dataset can be found on my github in the `results_folders.yaml`
[file](https://github.com/cduvallet/microbiomeHD/tree/master/data/user_input) and the
tables [directory](https://github.com/cduvallet/microbiomeHD/tree/master/final/tables).

## Raw data

The raw data is in the `mbit.storage.bucket1` S3 bucket. Datasets are labeled
with the disease state first, and then either the first or last author, and the
year of publication. Each folder should have a README explaining how I got the
data and what processing I decided was necessary.

## OTU tables

Processed OTU tables are on Zenodo: 
[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.569601.svg)](https://doi.org/10.5281/zenodo.569601)

## 16S High-Res Time Series

The processed OTU tables and metadata for the gut samples in [David et al., 2014](https://genomebiology.biomedcentral.com/articles/10.1186/gb-2014-15-7-r89) and [Caporaso et al., 2011](https://genomebiology.biomedcentral.com/articles/10.1186/gb-2011-12-5-r50) can be accessed [here](https://ndownloader.figshare.com/files/5665881).

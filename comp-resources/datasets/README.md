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

As part of my (Claire's) meta-analysis project, I've collected and re-processed
many case-control datasets from the raw data.

Once my paper is published, I'll definitely make all the OTU tables and metadata
files publicly available. For now, if you'd like to use one of these datasets,
just email me.

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

And some more technical information about each dataset:

dataset | min reads/sample | max reads | median reads | sequencer | region | data location | metadata
---------|---------|---------|---------|---------|---------|---------|---------
asd_kang | 179 | 3350 | 1345 | 454 | V2-V3 | SRA study SRP017161 | SRA
asd_son | 1985 | 9250 | 4777 | Miseq | V1-V2 | SRA study SRP057700 | SRA
cdi_schubert | 536 | 15651 | 4670 | 454 | V3-V5 | [link](mothur.org/CDI_MicrobiomeModeling) | [link](mothur.org/CDI_MicrobiomeModeling)
cdi_vincent | 904 | 19473 | 2526 | 454 | V3-V5 | email authors | email authors
cdi_youngster | 4110 | 32672 | 14696 | Miseq | V4 | SRA study SRP040146 | email authors
crc_baxter | 703 | 232464 | 9476 | Miseq | V4 | SRA study SRP062005 | SRA
crc_chen | 575 | 3364 | 1152 | 454 | V1-V3 | SRA study SRP009633 | SRA sample description
crc_wang | 101 | 515 | 161 | 454 | V3 | SRA study SRP005150 | SRA study description
crc_zackular | 16379 | 234554 | 54269 | MiSeq | V4 | [link](mothur.org/MicrobiomeBiomarkerCRC) | [link](mothur.org/MicrobiomeBiomarkerCRC)
crc_zeller | 28042 | 388997 | 120612 | MiSeq | V4 | ENA study PRJEB6070 | Table S1 and S2
edd_singh | 389 | 10538 | 2585 | 454 | V3-V5 | [link](http://dx.doi.org/10.6084/m9.figshare.1447256) | Additional File 4
hiv_dinh | 1675 | 11497 | 3248 | 454 | V3-V5 | SRA study SRP039076 | SRA
hiv_lozupone | 816 | 27634 | 3262 | MiSeq | V4 | ENA study PRJEB4335 | Qiita study 1700
hiv_noguerajulian | 225 | 231275 | 16506 | MiSeq | V3-V4 | SRA study SRP068240 | SRA
ibd_gevers | 745 | 57387 | 9773 | Miseq | V4 | SRA study SRP040765 | Table S2
ibd_morgan | 249 | 1617 | 1020 | 454 | V3-V5 | SRA study SRP015953 | [link](http://huttenhower.sph.harvard.edu/ibd2012)
ibd_papa | 277 | 6494 | 1303 | 454 | V3-V5 | email authors | email authors
ibd_willing | 162 | 2316 | 1118 | 454 | V5-V6 | email authors | email authors
mhe_zhang | 102 | 2674 | 487 | 454 | V1-V2 | SRA study SRP015698 | SRA
nash_wong | 708 | 2923 | 1980 | 454 | V1-V2 | SRA study SRP011160 | SRA
nash_zhu | 2196 | 16552 | 9904 | 454 | V4 | MG-RAST, study mgp1195 | MG-RAST
ob_goodrich | 3433 | 95825 | 27026 | Miseq | V4 | ENA studies PRJEB6702 and PRJEB6705 | ENA
ob_ross | 994 | 15266 | 4562 | 454 | V1-V3 | SRA study SRP053023 | SRA
ob_turnbaugh | 188 | 21102 | 1569 | 454 | V2 | [link](https://gordonlab.wustl.edu/NatureTwins_2008/TurnbaughNature_11_30_08.html) | Table S1
ob_zhu | 2196 | 16552 | 9904 | 454 | V4 | same study as `nash_zhu` | MG-RAST
ob_zupancic | 102 | 22478 | 1392 | 454 | V1-V3 | SRA study SRP002465 | SRA
par_scheperjans | 916 | 4535 | 2351 | 454 | V1-V3 | ENA study PRJEB4927 | sample names
ra_scher | 226 | 14779 | 2194 | 454 | V1-V2 | SRA study SRP023463 | SRA
t1d_alkanani | 403 | 96428 | 9117 | MiSeq | V4 | email authors | email authors
t1d_mejialeon | 1938 | 10154 | 4702 | 454 | V4 | email authors | email authors


## Raw data

The data is in the mbit.storage.bucket1 S3 bucket. Datasets are labeled
with the disease state first, and then either the first or last author, and the
year of publication. Each folder should have a README explaining how I got the
data and what processing I decided was necessary.

## OTU tables

You can either re-process them yourselves using the pipeline (the respective
S3 bucket should have the latest summary_file that I used to process the data).
You can also email me (duvallet at mit dot edu)!

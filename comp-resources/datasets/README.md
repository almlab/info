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

dataset | N_ctrl | controls | N_dis | cases | min_reads | max_reads | med_reads | sequencer | region | year | data | metadata | paper
---------|---------|---------|---------|---------|---------|---------|---------|---------|---------|---------|---------|---------|---------
asd_kang | 20 | H | 19 | ASD | 179 | 3350 | 1345.0 | 454 | V2-V3 | 2013 | SRA study SRP017161 | SRA | [link](http://dx.doi.org/10.1371/journal.pone.0068322)
asd_son | 44 | H | 59 | ASD | 1985 | 9250 | 4777.0 | Miseq | V1-V2 | 2015 | SRA study SRP057700 | SRA | [link](http://dx.doi.org/10.1371/journal.pone.0137725)
cdi_schubert | 243 | H, nonCDI | 93 | CDI | 536 | 15651 | 4670.5 | 454 | V3-V5 | 2014 | [link](mothur.org/CDI_MicrobiomeModeling) | [link](mothur.org/CDI_MicrobiomeModeling) | [link](http://dx.doi.org/10.1128/mBio.01021-14)
cdi_vincent | 25 | H | 25 | CDI | 904 | 19473 | 2526.5 | 454 | V3-V5 | 2013 | emailed authors | emailed authors | [link](http://dx.doi.org/10.1186/2049-2618-1-18)
cdi_youngster | 4 | H | 19 | CDI | 4110 | 32672 | 14696.0 | Miseq | V4 | 2014 | SRA study SRP040146 | emailed authors | [link](http://dx.doi.org/10.1093/cid/ciu135)
crc_baxter | 172 | H | 120 | CRC | 703 | 232464 | 9476.0 | Miseq | V4 | 2016 | SRA study SRP062005 | SRA | [link](http://dx.doi.org/10.1186/s13073-016-0290-3)
crc_chen | 22 | H | 21 | CRC | 575 | 3364 | 1152.0 | 454 | V1-V3 | 2012 | SRA study SRP009633 | SRA sample description | [link](http://dx.doi.org/10.1371/journal.pone.0039743)
crc_wang | 54 | H | 44 | CRC | 101 | 515 | 161.0 | 454 | V3 | 2012 | SRA study SRP005150 | SRA study description | [link](http://dx.doi.org/10.1038/ismej.2011.109})
crc_zackular | 30 | H | 30 | CRC | 16379 | 234554 | 54269.5 | MiSeq | V4 | 2014 | [link](mothur.org/MicrobiomeBiomarkerCRC) | [link](mothur.org/MicrobiomeBiomarkerCRC) | [link](http://dx.doi.org/10.1158/1940-6207.CAPR-14-0129)
crc_zeller | 75 | H | 41 | CRC | 28042 | 388997 | 120612.0 | MiSeq | V4 | 2014 | ENA study PRJEB6070 | Table S1 and S2 | [link](http://dx.doi.org/10.15252/msb.20145645)
edd_singh | 82 | H | 201 | EDD | 389 | 10538 | 2585.0 | 454 | V3-V5 | 2015 | [link](http://dx.doi.org/10.6084/m9.figshare.1447256) | Additional File 4 | [link](http://dx.doi.org/10.1186/s40168-015-0109-2)
hiv_dinh | 15 | H | 21 | HIV | 1675 | 11497 | 3248.5 | 454 | V3-V5 | 2015 | SRA study SRP039076 | SRA | [link](http://dx.doi.org/10.1093/infdis/jiu409)
hiv_lozupone | 13 | H | 23 | HIV | 816 | 27634 | 3262.0 | MiSeq | V4 | 2013 | ENA study PRJEB4335 | Qiita study 1700 | [link](http://dx.doi.org/10.1016/j.chom.2013.08.006)
hiv_noguerajulian | 34 | H | 205 | HIV | 225 | 231275 | 16506.0 | MiSeq | V3-V4 | 2016 | SRA study SRP068240 | SRA | [link](https://doi.org/10.1016%2Fj.ebiom.2016.01.032)
ibd_gevers | 16 | nonIBD | 146 | CD | 745 | 57387 | 9773.5 | Miseq | V4 | 2014 | SRA study SRP040765 | Table S2 | [link](http://dx.doi.org/10.1016/j.chom.2014.02.005)
ibd_morgan | 18 | H | 108 | UC, CD | 249 | 1617 | 1020.0 | 454 | V3-V5 | 2012 | SRA study SRP015953 | [link](http://huttenhower.sph.harvard.edu/ibd2012) | [link](http://dx.doi.org/10.1186/gb-2012-13-9-r79)
ibd_papa | 24 | nonIBD | 66 | UC, CD | 277 | 6494 | 1303.0 | 454 | V3-V5 | 2012 | emailed authors | emailed authors | [link](http://dx.doi.org/10.1371/journal.pone.0039242)
ibd_willing | 35 | H | 45 | UC, CD | 162 | 2316 | 1118.5 | 454 | V5-V6 | 2009 | emailed authors | emailed authors | [link](http://dx.doi.org/10.1053/j.gastro.2010.08.049)
mhe_zhang | 25 | H | 46 | CIRR, MHE | 102 | 2674 | 487.0 | 454 | V1-V2 | 2013 | SRA study SRP015698 | SRA | [link](http://dx.doi.org/10.1038/ajg.2013.221)
nash_wong | 22 | H | 16 | NASH | 708 | 2923 | 1980.0 | 454 | V1-V2 | 2013 | SRA study SRP011160 | SRA | [link](http://dx.doi.org/10.1371/journal.pone.0062885)
nash_zhu | 16 | H | 22 | NASH | 2196 | 16552 | 9904.0 | 454 | V4 | 2013 | MG-RAST, study mgp1195 | MG-RAST | [link](http://dx.doi.org/10.1002/hep.26093)
ob_goodrich | 428 | H | 185 | OB | 3433 | 95825 | 27026.0 | Miseq | V4 | 2014 | ENA studies PRJEB6702 and PRJEB6705 | ENA | [link](http://dx.doi.org/10.1016/j.cell.2014.09.053)
ob_ross | 26 | H | 37 | OB | 994 | 15266 | 4562.0 | 454 | V1-V3 | 2015 | SRA study SRP053023 | SRA | [link](http://dx.doi.org/10.1186/s40168-015-0072-y)
ob_turnbaugh | 61 | H | 195 | OB | 188 | 21102 | 1569.0 | 454 | V2 | 2009 | [link](https://gordonlab.wustl.edu/NatureTwins_2008/TurnbaughNature_11_30_08.html) | Table S1 | [link](http://dx.doi.org/10.1038/nature07540)
ob_zhu | 16 | H | 25 | OB | 2196 | 16552 | 9904.0 | 454 | V4 | 2013 | same as `nash_zhu` | MG-RAST | [link](http://dx.doi.org/10.1002/hep.26093)
ob_zupancic | 167 | H | 117 | OB | 102 | 22478 | 1392.0 | 454 | V1-V3 | 2012 | SRA study SRP002465 | SRA | [link](http://dx.doi.org/10.1371/journal.pone.0043052)
par_scheperjans | 74 | H | 74 | PAR | 916 | 4535 | 2351.5 | 454 | V1-V3 | 2015 | ENA study PRJEB4927 | sample names | [link](http://dx.doi.org/10.1002/mds.26069)
ra_scher | 28 | H | 86 | PSA, RA | 226 | 14779 | 2194.0 | 454 | V1-V2 | 2013 | SRA study SRP023463 | SRA | [link](http://dx.doi.org/10.7554/eLife.01202)
t1d_alkanani | 55 | H | 57 | T1D | 403 | 96428 | 9117.0 | MiSeq | V4 | 2015 | emailed authors | emailed authors | [link](http://dx.doi.org/10.2337/db14-1847)
t1d_mejialeon | 8 | H | 21 | T1D | 1938 | 10154 | 4702.0 | 454 | V4 | 2014 | emailed authors | emailed authors | [link](http://dx.doi.org/10.1038/srep03814)


## Raw data

The data is in the mbit.storage.bucket1 S3 bucket. Datasets are labeled
with the disease state first, and then either the first or last author, and the
year of publication. Each folder should have a README explaining how I got the
data and what processing I decided was necessary.

## OTU tables

You can either re-process them yourselves using the pipeline (the respective
S3 bucket should have the latest summary_file that I used to process the data).
You can also email me (duvallet at mit dot edu)!

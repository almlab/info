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

## Datasets

The datasets which are currently processed are:


Dataset ID |  Year  | Disease(s) | N control |  N case  | Med. reads/smpl | Sequencer  |   16S Region
-----------|--------|------------|-----------|----------|-----------------|------------| -------------
asd_kb | 2013 | ASD | 20 | 19 | 1345 | 454 | V2-V3
asd_son | 2015 | ASD | 44 | 59 | 4777 | Miseq | V1-V2
cdi_schu | 2014 | CDI | 243 | 93 | 3557 | 454 | V3-V5
cdi_vincent | 2013 | CDI | 18 | 17 | 5518 | 454 | V1-V3
cdi_young | 2014 | CDI | 18 | 27 | 16516 | Miseq | V4
crc_baxter | 2016 | CRC | 122 | 120 | 9476 | Miseq | V4
crc_xiang | 2012 | CRC | 22 | 21 | 1152 | 454 | V1-V3
crc_zackular | 2014 | CRC | 58 | 30 | 54269 | MiSeq | V4
crc_zeller | 2014 | CRC | 75 | 41 | 120612 | MiSeq | V4
crc_zhao | 2012 | CRC | 54 | 44 | 161 | 454 | V3
crc_zhu | 2013 | CRC | 18 | 12 | 1835 | 454 | V3
edd_singh | 2015 | EDD | 82 | 222 | 2573 | 454 | V3-V5
hiv_dinh | 2015 | HIV | 15 | 21 | 3248 | 454 | V3-V5
ibd_alm | 2012 | UC, CD | 24 | 66 | 1303 | 454 | V3-V5
ibd_eng | 2009 | UC, CD | 32 | 32 | 2658 | 454 | V5-V6
ibd_gevers | 2014 | CD | 16 | 146 | 9773 | Miseq | V4
ibd_hut | 2012 | UC, CD | 27 | 186 | 995 | 454 | V3-V5
mhe_zhang | 2013 | CIRR, MHE | 25 | 46 | 487 | 454 | V1-V2
nash_baker | 2013 | NASH, OB | 16 | 47 | 9904 | 454
nash_chan | 2013 | NASH | 22 | 32 | 1743 | 454 | V1-V2
ob_escobar | 2014 | OW, OB | 10 | 20 | 1126 | 454 | V1-V3
ob_goodrich | 2014 | OW, OB | 451 | 528 | 27364 | Miseq | V4
ob_gord | 2009 | OW, OB | 61 | 219 | 1569 | 454 | V2
ob_ross | 2015 | OB | 26 | 37 | 1583 | 454 | V1-V3
ob_zup | 2012 | OB | 167 | 117 | 1392 | 454 | V1-V3
par_schep | 2015 | PAR | 74 | 74 | 2351 | 454 | V1-V3
t1d_alkanani | 2015 | T1D | 23 | 89 | 9117 | MiSeq | V4
t1d_mejia | 2014 | T1D | 8 | 21 | 4702 | 454 | V3-V5

## Raw data

The data is in the mbit.storage.bucket1 S3 bucket. Datasets are labeled
with the disease state first, and then either the first or last author, and the
year of publication. Each folder should have a README explaining how I got the
data and what processing I decided was necessary.

## OTU tables

You can either re-process them yourselves using the pipeline (the respective
S3 bucket should have the latest summary_file that I used to process the data).
You can also email me (duvallet at mit dot edu)!
# Software
Cool stuff made by Almstars that's probably useful.
For the most part, published packages should be updated on the
Alm lab [website](http://almlab.mit.edu/software.html)

### amplicon sequencing pipeline

A collection of scripts that many Alm lab members use to process 16S data.
More info in the [16S folder](https://github.com/almlab/info/tree/master/comp-resources/16S).

### dbOTU (distribution-based clustering)

Distribution-based clustering. Originally developed by Sarah Preheim,
re-written by Scott Olesen. More info [here](http://almlab.mit.edu/dbotu3.html),
github [here](https://github.com/swo/dbotu3).

### TEXMEx

Package to interpret microbial community dynamics in paired experiments.
More info [here](http://almlab.mit.edu/texmex.html).

Olesen SW, Vora S, Techtmann SM, Fortney JL, Bastidas-Oyanedel JR, Rodrguez J, et al. (2016) A Novel Analysis Method for Paired-Sample Microbial Ecology Experiments. PLoS ONE 11(5): e0154804. doi:10.1371/journal.pone.0154804

### slime

Basically a wrapper to run a bunch of random forests on your OTU tables and metadata.
Github [here](https://github.com/cssmillie/slime). Original paper was this one (I think):

Papa, Eliseo, et al. "Non-invasive mapping of the gastrointestinal microbiota identifies children with inflammatory bowel disease." PloS one 7.6 (2012): e39242.```

### StrainFinder

Finds strains in metagenomics data. Github [here](https://github.com/cssmillie/StrainFinder).

### SparCC

Estimates correlation values from compositional data.  Available [here](https://bitbucket.org/yonatanf/sparcc).

Paper:

Friedman, Jonathan, and Eric J. Alm. "Inferring correlation networks from genomic survey data." PLoS Comput Biol 8.9 (2012): e1002687.

### caravan

An OTU-calling pipeline, github [here](https://github.com/swo/caravan). While you can
use it to process raw data into OTU tables, you need to call each function separately
(i.e. there is no integrated "press start, go make cookies, come back to an OTU table" function)

The ```tools/``` directory has a lot of nifty helper functions to help you work
with sequencing data.

### SmileTrain

Also an OTU-calling pipeline, mostly used by the ENIGMA project members.
Github [here](https://github.com/almlab/SmileTrain)

### symsim

Symsim is a simple simulation of sympatric speciation in recombining microbial populations.

More info [here](http://almlab.mit.edu/symsim.html).

### STARRINIGHTS

STARRInIGHTS is a computational pipeline for inferring homologous recombination breakpoints inpopulations of closely related bacterial genomes.

More info [here](http://almlab.mit.edu/starrinights.html)

### AnGST

AnGST is a software package for the inference of prokaryotic gene family evolutionary histories.

More info [here](http://almlab.mit.edu/angst.html).

### SHE-RA

SHE-RA is a tool that aligns the overlapping pair-end reads and generates composite long reads. The algorithm is applicable to any short read sequencing technology, and is open source.

More info [here](http://almlab.mit.edu/shera.html).

### AdaptML

AdaptML is a software package that will automatically partition groups of gene sequences...

More info [here](http://almlab.mit.edu/adaptml.html)
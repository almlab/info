# Software
Cool stuff made by Almstars that's probably useful.
For the most part, published packages should be updated on the
Alm lab [website](http://almlab.mit.edu/software.html)

### dbOTU (the OTU caller formerly known as DBC)

Distribution-based clustering. Originally developed by Sarah Preheim,
re-written by Scott Olesen. More info [here](http://almlab.mit.edu/dbotu3.html),
github [here](https://github.com/swo/dbotu3).

### caravan

An OTU-calling pipeline, github [here](https://github.com/swo/caravan). While you can
use it to process raw data into OTU tables, you need to call each function separately
(i.e. there is no integrated "press start, go make cookies, come back to an OTU table" function)

The ```tools/``` directory has a lot of nifty helper functions to help you work
with sequencing data.

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

# Contributors
- Claire Duvallet, 11/10/16
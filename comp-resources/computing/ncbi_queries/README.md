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
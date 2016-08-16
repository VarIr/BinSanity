# BinSanity v0.1.1

Program implements Affinity Propagation to cluster contigs into putative genomes. BinSanity uses contig coverage as an input, while BinSanity-refine incorporates tetranucleotide frequencies, GC content, and an optional input of coverage. All relevant scripts to produce inputs for BinSanity are provided here.

## BinSanity ##
###Dependencies###
>Versions used at time of last update to script are provided in parenthesis.

* [Numpy](http://www.numpy.org/) (v1.11.1)
* [SciKit](http://scikit-learn.org/stable/install.html) (v0.17.1)
* [Biopython](http://biopython.org/wiki/Download) (v1.66)
* [BedTools](http://bedtools.readthedocs.io/en/latest/content/installation.html) (v2.17.0)

Programs used to prepare input files for BinSanity and associated utility scripts include:

* [Bowtie2] (https://sourceforge.net/projects/bowtie-bio/) (v2.2.5)
* [Samtools] (http://www.htslib.org/) (v1.2)

###Input Files###
* Fasta file
* Combined Coverage Profile
```
contig  coverage-1 coverage-2 coverage-3
con-1   121        89         95
con-2   14         29         21
.......
```

###Script Usage's###
To generate input files for BinSanity the scripts `contig-coverage-bam.py` and `cov-combine.py` are provided:
* 'contig-coverage-bam' generates a `.coverage` file that produces a tab delimited file containing average contig coverage from a `.BAM` file. In our tests we used Bowtie2 to produce a `.SAM` file.  
```
contig-coverage-bam -f [fasta-file] -b [Bam-file] -o [out.coverage] 
.............
 ---------------------------------------------------------
            Finding Length information for each Contig
 ---------------------------------------------------------
 Number of sequences processed for length: 2343
 
  ---------------------------------------------------------
    Extracting Coverage Information from provided BAM file
  ---------------------------------------------------------
  
  Number of records processed for coverage: 2343
  
  ---------------------------------------------------------
                    Building Coverage File
  ---------------------------------------------------------
  Final Contigs processed: 2343

```
Output is typically in the format `sample-1.coverage`
```
BinSanity -f [directory-with-fasta-file] -l [fna,fa,fasta] -c [combined-cov]
```



##Issues##

If an issue arises in the process of utilizing BinSanity please provide please create an issue and we will address is as soon as possible. To expedite a response please provide any associated error messages. 

##Citation##
In Prep:
Elaina Graham, John Heidelberg, & Benjamin Tully. 2016. BinSanity: Unsupervised Clustering of Environmental Microbial Assemblies Using Coverage and Affinity Propagation. 

# VariantDB_Challenge

This repo is designed to serve as a testing framework for different database schemas, architectures, and query formulations within the context of mining genomics data.  For some reason, we in the genomics community (with a few outliers) are stuck in a file-based *modus operandi*.  Most people store variants in either a [VCF](http://samtools.github.io/hts-specs/VCFv4.2.pdf) or [gVCF](http://gatkforums.broadinstitute.org/firecloud/discussion/4017/what-is-a-gvcf-and-how-is-it-different-from-a-regular-vcf).  However there are numerous reasons why this is a bad long-term solution.

1. __VCF files need to be filtered in many different ways depending on the study question__
  - For example, if I wanted to exclude variants that change the protein sequence, I would write a filter program on the command-line and then write the subsetted VCF into yet another file.  This is a huge burden on data storage, as well as tracking data provenance.
2. __It's just not a scalable strategy__
  - I have a hard enough time keeping track of where all my files are from this year, let alone last year.  Instead many of us have to keep separate files that track where all of our files are.
3. __VCF files do not store metadata__
  - VCF files are OK for storing genetic variants, but the lack information about the samples they represent.  For example, simple metadata such as which samples are cases or controls, how old was the patient, etc. is not available in the current specification.
 
It's pretty clear, we need to move to a database if we want to stay on top of the problem of [data growth](http://journals.plos.org/plosbiology/article?id=10.1371/journal.pbio.1002195) that is to be expected.  However, given the scale and nature of genomics data, this isn't a simple solution.  Those that aren't in this field may ask, 

> Why not just throw all your data into a MySQL database?  Won't that work?

Technically, yes but pragmatically no. The key limitation is that the RDBMS approach scales up rather than scaling out for this particular use case.  Genomics is somewhat heterogeneous, constantly evolving and growing, and we need to leverage distributed computing and storage.  But if not MySQL, then what? *This is what this project is all about!*

The future of genomics depends on our ability to leverage distributed storage and computing, so what database architecture is best?  Let's find out by addressing the following challenges:

- Challenge #1.  The multiple source integration problem.

- Challenge #2.  The cost projection problem.

- Challenge #3.  The forward looking technology problem.

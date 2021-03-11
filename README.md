Credit to https://github.com/bulik for the python 2 implementation (full credits below).

# LDSC (LD SCore) `v0.1`

`ldsc` is a command line tool for estimating heritability and genetic correlation from GWAS summary statistics. `ldsc` also computes LD Scores.


## Getting Started
This guide is explicity designed for use with google colab.
Create a new google colab workbook here: https://colab.research.google.com/ (you will need a google account).
Add the following code to the first cell and execute (click the play button):

```python
!git clone https://github.com/PhilAlton/LDScoreRegressionP3.git

!pip install bitarray
!pip install nose
!pip install pybedtools

import sys
sys.path.append('/content/LDScoreRegressionP3')
sys.path.append('/content/LDScoreRegressionP3/ldscore')
```
The following commands (in a new cell) should now work:
```python
!python "/content/LDScoreRegressionP3/ldsc.py" -h
```
and
```python
!python "/content/LDScoreRegressionP3/munge_sumstats.py" -h
```
This should generate a command list / function help for each of these commands. 

## Where Can I Get LD Scores?

You can download [European](https://data.broadinstitute.org/alkesgroup/LDSCORE/eur_w_ld_chr.tar.bz2) and [East Asian LD Scores](https://data.broadinstitute.org/alkesgroup/LDSCORE/eas_ldscores.tar.bz2) from 1000 Genomes [here](https://data.broadinstitute.org/alkesgroup/LDSCORE/). These LD Scores are suitable for basic LD Score analyses (the LD Score regression intercept, heritability, genetic correlation, cross-sex genetic correlation). You can download partitioned LD Scores for partitioned heritability estimation [here](http://data.broadinstitute.org/alkesgroup/LDSCORE/).


## Support

Currently not built for wider support. See the original python 2 implemntation (https://github.com/bulik/ldsc) for a better supported version.

## Changes from bulik Python 2 version.
The following changes were made to the source code to upgrade to Python 3:
- Print functions: changed from previous syntax
```python
Old: print >>sys.stderr, "fatal error"
New: print("fatal error", file=sys.stderr)
```
- dictionary/list comprehension
```python
Old: list + dict.values()
New: List + list(dict.values())
```
```python
Old: dict.values().count()
New: list(dict.values()).count()
```
```python
# not sure exactly what happened here, but this produced a TypeError
# Limit (part of the traceback.format_exc(limit=None, chain=True) function sytax) should be an int or None
# I think it was assuming the value of the exception (a String).
# I suspect the Python2 function unpacked format_exc differently; 
# The current function is expecting only the optional parameters of limit and chain, 
# Not the exception string which is automatically pulled from *sys.exc_info(). 
Old: log.log(traceback.format_exc(ex))
New: log.log(''.join(traceback.format_exception(ex_type, ex)), tb, limit=None, chain=True)))
```
- Functions management
```python
Old: from irwls import IRWLS 
New: from ldscore.irwls import IRWLS
```
- Old functions:
```python
Old: reduce(x,y)
New: 
  import functools
  ...
  functools.reduce(x,y)
```
```python
Old: xrange(x)
New: range(x)
```
```python
Old: DataFrame.ix[...]
New: DataFrame.iloc[...]
```
```python
Old: DataFrame.as_matrix(columns=someDataFrameIndex)
New: DataFrame[someDataFrameIndex.values].values
```
- This is on-going, so please do reach out with issues if you find any errors, especially if these worked previously.


## Citation

If you use the software or the LD Score regression intercept, please cite

[Bulik-Sullivan, et al. LD Score Regression Distinguishes Confounding from Polygenicity in Genome-Wide Association Studies.
Nature Genetics, 2015.](http://www.nature.com/ng/journal/vaop/ncurrent/full/ng.3211.html)

For genetic correlation, please also cite

[Bulik-Sullivan, B., et al. An Atlas of Genetic Correlations across Human Diseases and Traits. Nature Genetics, 2015.](https://www.nature.com/articles/ng.3406) Preprint available on bioRxiv doi: http://dx.doi.org/10.1101/014498

For partitioned heritability, please also cite

[Finucane, HK, et al. Partitioning heritability by functional annotation using genome-wide association summary statistics. Nature Genetics, 2015.](https://www.nature.com/articles/ng.3404) Preprint available on bioRxiv doi: http://dx.doi.org/10.1101/014241

For stratified heritability using continuous annotation, please also cite

[Gazal, S, et al. Linkage disequilibrium–dependent architecture of human complex traits shows action of negative selection. Nature Genetics, 2017.](https://www.nature.com/articles/ng.3954) 

If you find the fact that LD Score regression approximates HE regression to be conceptually useful, please cite

Bulik-Sullivan, Brendan. Relationship between LD Score and Haseman-Elston, bioRxiv doi: http://dx.doi.org/10.1101/018283

For LD Hub, please cite

[Zheng, et al. LD Hub: a centralized database and web interface to perform LD score regression that maximizes the potential of summary level GWAS data for SNP heritability and genetic correlation analysis. Bioinformatics (2016)](https://doi.org/10.1093/bioinformatics/btw613)


## License

This project is licensed under GNU GPL v3.


## Original Authors

Brendan Bulik-Sullivan (Broad Institute of MIT and Harvard)

Hilary Finucane (MIT Department of Mathematics)

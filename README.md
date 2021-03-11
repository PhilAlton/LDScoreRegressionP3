Credit to https://github.com/bulik for the python 2 implementation (full credits below).

# LDSC (LD SCore) `v0.1`

`ldsc` is a command line tool for estimating heritability and genetic correlation from GWAS summary statistics. `ldsc` also computes LD Scores.
This guide is explicity designed for use with google colab.

## Getting Started



In order to download `ldsc`, you should clone this repository via the commands
```  
git clone https://github.com/PhilAlton/LDScoreRegressionP3.git
cd ldsc
```

In order to install the Python dependencies, you will need the [Anaconda](https://store.continuum.io/cshop/anaconda/) Python distribution and package manager. After installing Anaconda, run the following commands to create an environment with LDSC's dependencies:

```
conda env create --file environment.yml
source activate ldsc
```

Once the above has completed, you can run:

```
./ldsc.py -h
./munge_sumstats.py -h
```
to print a list of all command-line options. If these commands fail with an error, then something as gone wrong during the installation process. 

Short tutorials describing the four basic functions of `ldsc` (estimating LD Scores, h2 and partitioned h2, genetic correlation, the LD Score regression intercept) can be found in the wiki. If you would like to run the tests, please see the wiki.


## Where Can I Get LD Scores?

You can download [European](https://data.broadinstitute.org/alkesgroup/LDSCORE/eur_w_ld_chr.tar.bz2) and [East Asian LD Scores](https://data.broadinstitute.org/alkesgroup/LDSCORE/eas_ldscores.tar.bz2) from 1000 Genomes [here](https://data.broadinstitute.org/alkesgroup/LDSCORE/). These LD Scores are suitable for basic LD Score analyses (the LD Score regression intercept, heritability, genetic correlation, cross-sex genetic correlation). You can download partitioned LD Scores for partitioned heritability estimation [here](http://data.broadinstitute.org/alkesgroup/LDSCORE/).


## Support

Currently not built for wider support. See the original python 2 implemntation (https://github.com/bulik/ldsc) for a better supported version.


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

# cuteSV

[![PyPI version](https://badge.fury.io/py/cuteSV.svg)](https://badge.fury.io/py/cuteSV)
[![Anaconda-Server Badge](https://anaconda.org/bioconda/cutesv/badges/version.svg)](https://anaconda.org/bioconda/cutesv)
[![Anaconda-Server Badge](https://anaconda.org/bioconda/cutesv/badges/license.svg)](https://anaconda.org/bioconda/cutesv)
[![Anaconda-Server Badge](https://anaconda.org/bioconda/cutesv/badges/platforms.svg)](https://anaconda.org/bioconda/cutesv)
[![Anaconda-Server Badge](https://anaconda.org/bioconda/cutesv/badges/latest_release_date.svg)](https://anaconda.org/bioconda/cutesv)

---
### Getting Start
	                                               __________    __       __
	                                              |   ____   |  |  |     |  |
	                          _                   |  |    |__|  |  |     |  |
	 _______    _     _   ___| |___     ______    |  |          |  |     |  |
	|  ___  |  | |   | | |___   ___|   / ____ \   |  |_______   |  |     |  |
	| |   |_|  | |   | |     | |      / /____\ \  |_______   |  |  |     |  |
	| |        | |   | |     | |      | _______|   __     |  |  \  \     /  /
	| |    _   | |   | |     | |  _   | |     _   |  |    |  |   \  \   /  /
	| |___| |  | |___| |     | |_| |  \ \____/ |  |  |____|  |    \  \_/  /
	|_______|  |_______|     |_____|   \______/   |__________|     \_____/


---	
### Installation
	$ pip install cuteSV
	or
	$ conda install -c bioconda cutesv
	or 
	$ git clone https://github.com/tjiangHIT/cuteSV.git && cd cuteSV/ && pip install .

---	
### Introduction
Long-read sequencing technologies enable to comprehensively discover structural variations (SVs). However, it is still non-trivial for state-of-the-art approaches to detect SVs with high sensitivity or high performance or both. Herein, we propose cuteSV, a sensitive, fast and lightweight SV detection approach. cuteSV uses tailored methods to comprehensively collect various types of SV signatures, and a clustering-and-refinement method to implement a stepwise SV detection, which enables to achieve high sensitivity without loss of accuracy. Benchmark results demonstrate that cuteSV has better yields on real datasets. Further, its speed and scalability are outstanding and promising to large-scale data analysis.

The benchmark results of cuteSV on the HG002 human sample are below:

<img src="hg2_cuteSV_assessments.png" width="800px">

BTW, we used [Truvari](https://github.com/spiralgenetics/truvari) to calculate the recall, precision, and f-measure.

---
### Dependence
	
	1. python
	2. pysam
	3. Biopython
	4. cigar
	5. numpy

---
### Usage
	python cuteSV.py <sorted.bam> <output.vcf> <work_dir>
	
*Suggestions*

	> For PacBio CLR data:
		--max_cluster_bias_INS		100
		--diff_ratio_merging_INS	0.2
		--diff_ratio_filtering_INS	0.6
		--diff_ratio_filtering_DEL	0.7
	> For PacBio CCS(HIFI) data:
		--max_cluster_bias_INS		200
		--diff_ratio_merging_INS	0.65
		--diff_ratio_filtering_INS	0.65
		--diff_ratio_filtering_DEL	0.35
	
| Parameter | Description | Default |
| :------------ |:---------------|-------------:|
|--threads|Number of threads to use.| 16 |
|--batches| A batches of reads to load.        |10,000,000|
|--sample| Sample name/id |NULL|
|--genotype|Optional genotyping (True/False).|False|
|--max_split_parts|Maximum number of split segments a read may be aligned before it is ignored.|7|
|--min_mapq|Minimum mapping quality value of alignment to be taken into account.|20|
|--min_read_len|Ignores reads that only report alignments with not longer then bp.|500|
|--min_support|Minimum number of reads that support a SV to be reported.|3|
|--min_length|Minimum length of SV to be reported.|30|
|--max_cluster_bias_INS|Maximum distance to cluster read together for insertion.|100|
|--diff_ratio_merging_INS|Do not merge breakpoints with basepair identity more than the ratio of *default* for insertion.|0.2|
|--diff_ratio_filtering_INS|Filter breakpoints with basepair identity less than the ratio of *default* for insertion.|0.6|
|--max_cluster_bias_DEL|Maximum distance to cluster read together for deletion.|200|
|--diff_ratio_merging_DEL|Do not merge breakpoints with basepair identity more than the ratio of *default* for deletion.|0.3|
|--diff_ratio_filtering_DEL|Filter breakpoints with basepair identity less than the ratio of *default* for deletion.|0.7|
|--max_cluster_bias_INV|Maximum distance to cluster read together for inversion.|500|
|--max_cluster_bias_DUP|Maximum distance to cluster read together for duplication.|500|
|--max_cluster_bias_TRA|Maximum distance to cluster read together for translocation.|50|
|--diff_ratio_filtering_TRA|Filter breakpoints with basepair identity less than the ratio of *default* for translocation.|0.6|

---
### Datasets generated from cuteSV
We provided the SV callsets of the HG002 human sample produced by cuteSV form three different long-read sequencing platforms (i.e. PacBio CLR, PacBio CCS, and ONT PromethION). 

You can download them at: 
[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.3477781.svg)](https://doi.org/10.5281/zenodo.3477781)

Please cite the manuscript of cuteSV before using these callsets.

---
### Citation
Long Read based Human Genomic Structural Variation Detection with cuteSV. Tao Jiang, et al. bioRxiv 780700; doi: https://doi.org/10.1101/780700
	
---
### Contact
For advising, bug reporting and requiring help, please post on [Github Issue](https://github.com/tjiangHIT/cuteSV/issues) or contact tjiang@hit.edu.cn.

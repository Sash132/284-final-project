# Comparison of Relative Finding Methods (CSE 284 - Analysis Project)

### Group Number: 22
### Group Members: Sashwath Gollamudi

## Description
This is a project that involves comparing various methods of relative finding (IBD) and determining the benefits and drawbacks of each. Specifically, the methods that are utilized in this project are PLINK, GERMLINE, IBDseq, and BEAGLE's fastIBD.

## Repository/File Structure
All of the scripting occurs within `fp.ipynb`, which is the place where the code and visualizations reside for the scope of this project. This file contains descriptions in markdown cells of what is being done throughout the notebook. Data and results are stored across a series of directories: /samples and /samples_singular to store sample lists; /plink, /germline, /ibdseq, and /fastibd to store output files from running each of these tools; and /data to store the data of all necessary file formats that will be utilized by these tools. All of these directories are specified for Part 1 of the project. Then, in /sizes, all of these directories are recreated but this time used for the files dealing with Part 2 of the project. Note: some data files in /sizes could not be uploaded to Github due to their file sizes. Although, if one were to run the notebook again, these files will be generated for the user. Finally, there are two extra files, `persistent_p1.txt` for Part 1 and `persistent_p2.txt` for Part 2. These hold runtime and peak memory usage values collected from these executing these tools so they may be reused in visualizations without having to run each of the tools again, especially considering some of these tools have rather long runtimes for larger input sizes. 

If one were to run the notebook to test it for themselves, then they would need a series of tools installed on the system that they are running it on, on top of what is accessible on Datahub. Specifically, these tools are: 
- [PLINK 1.9](https://www.cog-genomics.org/plink/)
- [GERMLINE 1.5.3](http://gusevlab.org/projects/germline/)
- [IBDseq (r1206)](https://faculty.washington.edu/browning/ibdseq.html)
- [BEAGLE 5.4](http://faculty.washington.edu/browning/beagle/beagle.html)
- [vcf2beagle](https://faculty.washington.edu/browning/beagle_utilities/utilities.html)
- [memusg](https://github.com/jhclark/memusg)

In addition, ensure that the following Python libraries are installed through `pip`: `pandas`, `vcf`, `os`, `subprocess`, `numpy`, and `matplotlib`.

For the sake of ownership, I have not included those files and installations within this Github repository. Although, links have been provided above to download/install the necessary files to run this notebook. Once these have been installed, then all the user would need is the `fp.ipynb` file as well as access to the 1000 Genomes Phase 3 dataset (which can be found in /public/1000Genomes in Datahub); all other files and directories will be generated as a result of executing the code cells in the notebook.

## Project Scope
The scope of this project is simply to compare these four aforementioned tools against one another and see where they shine and more importantly where they falter. From this, the goal is to determine best use cases for these tools and figure out when each would be most beneficial. To do this, I made use of the 1000 Genomes Phase 3 dataset (using the path structure that was set up in Datahub [/public/1000Genomes/]). 

## Project Parts/Efforts
Across the notebook, there are two separate grand parts at comparisons between the tools. 

Part 1 deals with the different subpopulations that are made available as a part of the 1000 Genomes Phase 3 dataset. In essence, this section focuses on separating the dataset into their respective subpopulations. From there, we manipulate these files into acceptable file formats for the four tools and then run each of the tools twice on each subpopulation, once measuring the runtime of the tool and another measuring the peak memory usage of the tool. From this, we can get a large view scope of how the tools performs among similar input sizes but different data in each input.

Part 2, on the other hand, essentially deals with stress-testing these tools as a major goal rather than necessarily looking for accuracy. In essence, all samples (~2500) are taken and subsets of this large set are created in intervals of 100; this means that there is a sample list containing the first 100 samples, a sample list containing the first 200 samples, and so on until we reach a sample list of size 2500. Then, the files are manipulated into acceptable file formats for the tools, similar to Part 1. Once this is odne, each tool is run against each of these lists twice, again to measure runtime and to measure peak memory usage. From this, we can get a better look at how these tools performs dependent on the size of the input and determine which performs best in specific situations.

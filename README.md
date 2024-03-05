# Comparison of Relative Finding Methods (CSE 284 - Analysis Project)

## Description
This is a project that involves comparing various methods of relative finding (IBD) and determining the benefits and drawbacks of each. Specifically, the methods that are utilized in this project are PLINK (as a baseline), GERMLINE, IBDseq, and BEAGLE's fastIBD.

## Structure
The majority of scripting occurs within `fp.ipynb`, which is the place where the code and visualizations reside for the scope of this project. Data and results are stored across a series of directories: /samples and /samples_singular to store sample lists; /plink, /germline, /ibdseq, and /fastibd to store output files from running each of these tools; /sizes to store subsets of fixed sizes of the largest possible sample list; and finally /data and /sizes/data to store the data of all necessary file formats that will be utilized by these tools. Finally, there is an extra `persistent.txt` file that holds data collected from these tools so they may be reused in visualizations without having to run each of the tools again. If one were to run the notebook to test it for themselves, then they would need a series of tools installed on the system that they are running it on. Specifically, these tools are PLINK, GERMLINE, IBDseq, BEAGLE, vcf2beagle, and memusg. For the sake of ownership, I have not included those files and installations within this Github repository.

## Scope and Progress
### Scope
The scope of this project was simply to compare these four aforementioned tools as much as possible and see where they shine and more importantly where they falter. From this, the goal is to determine best use cases for these tools and figure out when each would be most beneficial. To do this, I made use of the 1000 Genomes Phase 3 dataset (using the path structure that was set up in Datahub [/public/1000Genomes/]). 

### Progress
Across the notebook, there are two separate parts/attempts at comparisons. 

The first part is across different subpopulations. In essence, this section focuses on separating the part of the 1000 Genomes Phase 3 dataset that is being used into their respective subpopulations and then running each of the four tools twice on each subpopulation, once measuring the runtime of the tool and another measuring the peak memory usage of the tool. 

The second attempt at comparisons comes from essentially stress-testing these tools. In essence, all samples (~2500) are taken and subsets of this large set are created in intervals of 100; this means that there is a sample list containing the first 100 samples, a sample list containing the first 200 samples, and so on until we reach a sample list of size 2500. Then each tool is run against each of these lists twice, again to measure runtime and to measure peak memory usage. From this, the goal is to analyze overall time complexity of each tool.

## Remaining Work
So far, a majority of the work has been completed in terms of data collection. Specifically, all necessary data has been collected for the first part of comparisons. What would need to be done now is to further visualize this data in a user-friendly format that highlights when these tools are at their most efficient / least efficient. 

The grand part of the work that is left resides in the second part of comparisons, the stress-testing. So far, only stress-testing for PLINK has been completed. Over the course of the remaining time, I will need to perform stress-testing against the three other tools: GERMLINE, IBDseq, and BEAGLE's fastIBD. Once this is done, they will need to be visualized in a manner that will make it clear of the generalized time complexity of each tool.

After this, I plan to write out an analysis speaking on the outputs of each of these tools and how useful they are to the common user. For example, if one tool simply gives a true/false value for if there is an association between relatives as opposed to another tool which may provide direct information regarding P(IBD=0), P(IBD=1), and P(IBD=2), then there is a necessary commentary on how these compare to one another and how they may be utilized by actual users.

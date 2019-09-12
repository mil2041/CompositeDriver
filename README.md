## CompositeDriver

### Reference

* Matthew H Bailey, Collin Tokheim, Eduard Porta Pardo, Sohini Sengupta, Denis Bertrand, Amila Weerasinghe, Antonio Colaprico, Michael C Wendl, Jaegil Kim, Brendan Reardon, Patrick Kwok Shing Ng, Kang Jin Jeong, Song Cao, Zixing Wang, Jianjiong Gao, Qingsong Gao, Fang Wang, Eric Minwei Liu, Loris Mularoni, Carlota Rubio Perez, Niranjan Nagarajan, Isidro Cortés Ciriano, Daniel Cui Zhou, Wen Wei Liang, Julian M Hess, Venkata D Yellapantula, David Tamborero, Abel Gonzalez Perez, Chayaporn Suphavilai, Jia Yu Ko, Ekta Khurana, Peter J Park, Eliezer M Van Allen, Han Liang, Michael S Lawrence, Adam Godzik, Nuria Lopez Bigas, Josh Stuart, David Wheeler, Gad Getz, Ken Chen, Alexander J Lazar, Gordon B Mills, Rachel Karchin, Li Ding, MC3 Working Group, Cancer Genome Atlas Research Network [“Comprehensive Characterization of Cancer Driver Genes and Mutations”](https://www.ncbi.nlm.nih.gov/pubmed/29625053), Cell 173, 371 385.e18 (2018). 

### Overview
CompositeDriver combined mutation recurrence and functional impact to identify coding and non-coding cancer drivers

### Version notes


* CompositeDriver (version 0.2) supports SNV coding and non-coding drivers  
* CompositeDriver (version 0.1) supports SNV coding drivers   




### Installation
User will need to install devtools in R for running CompositeDriver package

```sh
install.packages("devtools")
library("devtools")
devtools::install_github("khuranalab/CompositeDriver")
```

### Usage
User will need to 

* (1) download [drm.gene.bed](http://khuranalab.med.cornell.edu/FunSeq_data/FunSeq2_DC2/data/drm.gene.bed) file and put it in the "/path/to/dataContext" folder
* (2) assign "/path/to/Output.vcf" path for FunSeq2 annotated vcf file
* (3) assign "/path/to/output" path for saving CompositeDriver results
* (4) tumorType: name of tumor type
* (5) seedNum: random number seed number (default is 42)
* (6) functionalImpactScoreCDS: name of functional impact scoring scheme for CDS (current supports "FunSeq2" or "MCAP")
* (7) functionalImpactScoreNonCoding: name of functional impact scoring scheme for non-coding (current supports "FunSeq2" )
* (8) reSampleIter: sampling iterations (suggesting number is 1000000 iterations)
* (9) useCores: number of cores for parellel computation 

```sh

library(CompositeDriver)

#####
# global parameters setup
#####

  dataContextDir<-"/path/to/dataContext"
  annotatedInput<-"/path/to/Output.vcf"
  outputDir<-"/path/to/output"
  tumorType<-"GBM"
  seedNum<-42
  functionalImpactScoreCDS<-"FunSeq2"
  functionalImpactScoreNonCoding<-"FunSeq2"
  reSampleIter<-1000
  useCores<-6
  debugMode<-FALSE

#####
  
  preProcessVCF(annotatedInput,functionalImpactScoreCDS,functionalImpactScoreNonCoding,outputDir,tumorType,useCores)

#####

  mutationType<-"CDS"
  cdsOutputDf<-getCDSpvalue(outputDir,tumorType,mutationType,
                            reSampleIter=reSampleIter,
                            seedNum=seedNum,debugMode=debugMode)

#####


```
### Contacts
For any questions, comments and suggestions, please email

* ekk2003 [at] med.cornell.edu 
* mil2041 [at] med.cornell.edu

Copyright © 2016-2019 Ekta Khurana Lab, WCMC

### License 
This project is licensed under the CC BY-NC 4.0 
[![License: CC BY-NC 4.0](https://licensebuttons.net/l/by-nc/4.0/80x15.png)](http://creativecommons.org/licenses/by-nc/4.0/)



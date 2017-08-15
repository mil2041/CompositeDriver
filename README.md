## CompositeDriver

### An R package detecting SNV coding and non-coding drivers in cancer

Update log
```sh
* CompositeDriver (version 0.2) supports SNV coding and non-coding drivers  
* CompositeDriver (version 0.1) supports SNV coding drivers   
```


Installing CompositeDriver


You will need to install devtools for running CompositeDriver package

```sh
install.packages("devtools")
library("devtools")
devtools::install_github("khuranalab/CompositeDriver")
```

### CompositeDriver example
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


## Abstract
This is an implementation of Systematic Random forest Integrative Qualitative threshold (SRIQ) clustering.
SRIQ clusters by finding a small amount of highly correlated observations, then spiralling out from them to create bigger clusters.
SRIQ evaluates clustering solution stability on its own and won't need user input for what number of cluster solutions to be evaluated.
SRIQ has no limit to feature size performance wise, and can be run on ordinary home computers.

For more information about SRIQ, see our [publication](https://www.youtube.com/watch?v=dQw4w9WgXcQ)

## Installation

To install this repository simply create a folder and clone the repository:
```bash
mkdir SRIQ
cd SRIQ
git clone https://github.com/Fattigman/SRIQ
```
## Usage

To run the pipeline, start the jupyter notebook file and follow the instructions.

```python
jupyter notebook analysis_pipeline
```

To run SRIQ, navigate to the folder in which the VRLA.jar file exist and run following command:
```bash
java -jar VRLA.jar
```

## Features

The project provide following features 

* SRIQ-clustering
* Pre-clustering data normalization
* Silhoutte-plot analysis
* UMAP
* Differential gene expression with SAM
* Enrichment analysis with EnrichR against customizable databases
* Visualization of single or multiple genes across clusters

## Data requirements

Your data to be clustered should be a tab separated .txt file and look like this:

For SRIQ to accept the data to be clustered, the file has to be in following format:
| Gene               |   Sample1          |   Sample2          |   ...              |   SampleN          |
|:-------------------|-------------------:|-------------------:|-------------------:|-------------------:|
| Genename 1         |            val1    |         val2       |         ...        |         valN       |
| ...                |            ...     |         ...        |         ...        |         ...        |
| Genename M         |            val1    |         val2       |         ...        |         valN       |

For clustering expression data should be 
* Off-set by 0.1 OR all values < 1 set to 1
* Log2transformed
* Median-centered
* 
For SAM-analysis:
* Off-set by 0.1 OR all values < 1 set to 1
* Log2transformed

Before running SRIQ, test.properties file need to be correctly configured.
The following lines needs to be correct or SRIQ won't start.
```
studyName: Desired output name for project
studyPath: Folderpath to expression data
inFileName: expression file. exclude '.txt' from file name
outPath: Folderpath for SRIQ output
```


To run GO enrichment, the significantly expressed gene names need to be converted into symbol names.
To do that, run the `obj.ens2symbol(arg)`. Parameter can be found in [this documentation](https://docs.mygene.info/en/latest/doc/query_service.html)

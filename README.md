# MSnet

A large open benchmark dataset for computational proteomics based on public proteomics data. The project aims to generate an extensive collection of data that can be used to train AI algorithms for the following use cases: 

1. Peptide/Protein identification based on LLMs methods (de novo or FASTA database). For this use case, the collection MUST include the peptide identifications and the corresponding data.
2. Retention time prediction. For this use case, the collection MUST include, the peptide identification, and experimental retention time, MS1 information.
3. PTM localization. For PTM localization, the PTM, the position and the corresponding score are associated with the site localization.    

# Contributors

- Phoenix center: Cheng Chang, Linhai Xie, Chengxin Dai, Tianze Ling
- EBI: Yasset Perez-Riverol
- Shanghai AI lab: Zhiqiang Gao
- Chongqing: Mingze Bai

## 1. Use quantms to re-analyze the data in PRIDE (Yasset) and iProX (Cheng and Zhiqiang)

The following decisions have been made during the discussion (20223/06/20): 

- quantms (https://github.com/bigbio/quantms) will be used as the workflow to perform the peptide/protein identifications.
- Public data will be reused from ProteomeXchange. For that, the following has been decided:
  - Every dataset should be annotated with an SDRF, this should be a collective effort between all teams involved using Pull requests in this repo.
  - Datasets from PRIDE will be reanalysed by the PRIDE team, while iPROX datasets will be reanalyzed by the Phoenix Centre group. Datasets from other ProteomeXchange databases will be analyzed by any of the partners of the project. 

### 1.1 For input data

- MS instrument: High-resolution data only. Note: If data for low resolution is generated, we should keep it for version 1.2 of the project. 
- HCD/CID/ETD
- Species: We should focus first on Human. Note: most of the current algorithms and training datasets have been generated using human data, would be great to start from the beginning annotating other species, like viruses, bacteria, yeast, etc. 
- DDA at first, Then DIA.
- TMT and Label-free

### 1.2 quantms for analysis tools

- Search engine: MSGF+, Comet, and SAGE (when available).
- FDR at the project level: We should start using 1% FDR at PSM level, however for very large projects with millions of PSMs, we should try to reduce that FDR to 0.001 (depending on the project size). 

### 1.3 QC integration from multiple datasets

If the number of datasets integrated increases, also the number of false positive PSMS (even if the FDR is reduced to 0.001). The first research should be done about this topic, how to control FDR in the aggregation of the data. Possible solutions: 

- Clustering. By using clustering you can reduce the number of PSMs and just include in the data the high-quality clusters.
- Select the best high-quality hit for each spectrum representation. 
  
## 2. The output file format

From quantms would be good to have a different output that can be easily transferred between repositories (iProX - China, PRIDE - UK). 

## 3. Implement PANDAnovo (LLM) into quantms

## 4. Website for data sharing and data visualization:
- USI?
- Spectrum anatation?

## 5. Meetings
- First meeting (20223/06/20)
- to do done.

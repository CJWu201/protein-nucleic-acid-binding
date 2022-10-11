# Introduction

  We collected data on protein-nucleic acid interactions from BioLip, Uniprot and PDB databases, and finally generated the test dataset for this experiment by cleaning, clustering and redundancy. This dataset contains 223 protein-nucleic acids interaction proteins, with a total of 67805 residues, including 60 proteins interacting with DNA, containing 1341 interaction residues, and 135 proteins interacting with RNA, containing 4401 interaction residues.  
  We use this test dataset on some protein-nucleic acid interaction site prediction tool, and their results are detailed in the results folder.

# Dataset

  We collect proteins, which were solved structurally in complex from the BioLiP database in October 2015. It annotates a given residue as binding if the distance between an atom of this residue and an atom of the ligand <0.5 + sum of the Van der Waal’s radii of the two atoms . BioLip includes 5913 DNA-binding and 20 731 RNA-binding, some of which are redundant. In contrast to the other studies that typically consider one complex per protein and which may cover a fragment of the complete protein sequence, we use complete proteins that combine annotations from potentially multiple complexes. We map BioLiP sequences into UniProt with SIFTS to ensure that we work with complete protein sequences and to transfer annotations from multiple BioLiP/PDB protein chains that are linked to the same UniProt protein. Next, we remove UniProt IDs that correspond to protein fragments and combine annotations of binding residues from all PDB structures that are mapped to the same protein (UniProt ID). This way we annotate 27% more binding residues when compared with the best case scenario of how prior works annotate binding residues, i.e. when chains with the highest number of binding residues are used to cover the complete protein sequence. This enrichment is accomplished by transferring binding residues from BioLiP/PDB chains that cover the same fragment of the UniProt sequence.
    
  The final data set includes 1857 proteins (817 DNA-binding, 1040 RNA-binding). 

|dataset|proteins|residues|-DNA|-RNA|-DNA residus|-RNA residues|
| :-------: | :--------: | :--------: | :----: | :----: | :------------: | :-------------: |
|all|1857|423695|817|1040|19987|38899|

    Divide the test set.

|dataset|proteins|residues|-DNA|-RNA|-DNA residus|-RNA residues|
| :-------: | :--------: | :--------: | :----: | :----: | :------------: | :-------------: |
|test|223|67805|60|135|1341|4401|

# Result

## DNA

  Results about BindN+, DRNApred, ProNA2020, NCBRPred, DNAgenie using our test dataset.

|method|AUC|AUPR|AUCPC|AUOPC|
| -----------| -------| -------| -------| -------|
|BindN+|0.764|0.057|0.491|0.218|
|DRNApred|0.763|0.067|0.304|0.232|
|ProNA2020|0.737|0.085|0.421|0.252|
|NCBRPred|0.822|0.182|0.238|0.173|
|DNAgenie|0.744|0.046|0.560|0.235|

  Indicators based on binary forecasts

|method|F_max|MCC|PRE|REC|FPR|OPR|CPR|REC/FPR|REC/OPR|REC/CPR|
| -----------| -------| -------| ---------| -------| -------| -------| -------| ---------| ---------| ---------|
|BindN+|0.126|0.134|0.075|0.391|0.098|0.080|0.354|4.007|4.905|1.103|
|DRNApred|0.136|0.122|0.098|0.224|0.042|0.037|0.112|5.376|6.083|2.011|
|ProNA2020|0.191|0.187|0.135<br />|0.332|0.043|0.041|0.069|7.704|8.034|4.842|
|NCBRPred|0.258|0.243|0.229|0.295|0.020|0.017|0.069|14.680|17.646|4.294|
|DNAgenie|0.104|0.112|0.059|0.399|0.127|0.104|0.469|3.134|3.853|0.850|

## RNA

  Results about Pprint, BindN+, DRNApred, ProNA2020, NCBRPred using our test dataset

|method|AUC|AUPR|AUCPC|AUOPC|
| -----------| -------| -------| -------| -------|
|Pprint|0.758|0.288|0.392|0.239|
|BindN+|0.778|0.274|0.460|0.217|
|DRNApred|0.609|0.205|0.311|0.393|
|ProNA2020|0.750|0.377|0.356|0.247|
|NCBRPred|0.775|0.371|0.239|0.225|

  Indicators based on binary forecasts

|method|F_max|MCC|PRE|REC|FPR|OPR|CPR|REC/FPR|REC/OPR|REC/CPR|
| -----------| -----------------| -----------------| -----------------| -----------------| -----------------| -----------------| -----------------| ------------------| ------------------| ------------------|
|Pprint|0.324|0.277|0.322|0.327|0.048|0.046|0.138|6.842|7.115|2.366|
|BindN+|0.318|0.269|0.303|0.335|0.053|0.050|0.245|6.273|6.764|1.369|
|DRNApred|0.249|0.218|0.332|0.199|**0.028**|**0.028**|**0.010**|7.175|7.085|**19.277**|
|ProNA2020|0.425|0.383|0.404|0.447|0.046|0.045|0.078|9.778|9.919|5.748|
|NCBRPred|0.403|0.363|0.413|0.394|0.039|0.038|0.079|10.147|10.362|5.011|
|DRbindRC|**0.477**|**0.444**|**0.507**|**0.451**|0.030|0.030|0.051|**14.825**|**15.029**|8.873|

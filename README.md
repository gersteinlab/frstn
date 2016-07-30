# Frustration Project

This repository contains source code for workflow evaluating the change in Localized frustration index of a protein residue
upon mutation. The input to this workflow is VAT output file, which is ran on the user provided
list of single nucleotide variants(SNVs). More details about running VAT can be found here (http://vat.gersteinlab.org/).

---This workflow consist of three steps for evaluating changes in frustration:

**1) Parsing VAT output of all SNVs to etxract residue position and residue identity for the mutated residue on protein sequence**


Usage:


  **_parseVatOut.py -d dataResourceFile -v vatOutputFile -b bioMartFile -type snpType_**
  
  parseVatOut.py (-h | --help)
  
  dataResourceFile = gencode v19 translated fasta sequence
  
  bioMartFile = Biomart output file containing GeneId,TranscriptId and PdbId (genocde v19)
  
  snpType = nonsynonymous
  


**2) Mapping each SNV onto user-provided list of PDB strcuture ange generating mutated PDB**


Usage:


  **_mapSNP2PDB.py -p pdbIdList -b bioMartFile -I snpSummaryFile -B blastPDir -M modellerDir -P pbdSeqDir -O outLogFile_**
  
  mapSNP2PDB.py (-h | --help)
  
  pdbIdList = list of high resolution PDBs for mapping SNPs
  
  bioMartFile = Biomart output file containing GeneId,TranscriptId and PdbId (genocde v19)
  
  snpSummaryFile = generated by parseVatOut.py in the previous step
  
  blastPDir = BlastP directory
  
  modellerDir =  Modeller directory
  
  pdbSeqDir = pdbTool directory

**3) Evaluating Frustration changes of residues**


Usage:
  
  **_extractFrustrationInfo.py -I mappedSNPInfo -nd nativePDBDir -md mutPDBDir -F frstnExecDir -P pdbSeqDir -O frustrationOutFile_**
  
  
  extractFrustrationInfo.py (-h | --help)
  
  mappedSNPInfo = mapped SNV info file generated by mapSNP2PDB.py
  
  nativePDBDir = Directory where you store your native PDBs
  
  mutPDBDir = Driectory where you store your mutated/modeled PDBs
  
  frstnExecDir = Frustration executable location
  
  pdbSeqDir = pdbTool directory
  
  
  
  

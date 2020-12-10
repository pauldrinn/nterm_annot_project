## Objective
Improving the coverage of annotations for N-terminal domains of NLR proteins.

## Approach

### Through remote homologues (HMMER)
The relevant profiles were searched against our database and 1589 new domain annotations were obtained.

- [x] Pfam HMM library obtained (ftp://ftp.ebi.ac.uk/pub/databases/Pfam/current_release/Pfam-A.hmm.gz)
- [x] Relevant families retrieved from https://doi.org/10.1007/978-3-030-49924-2_6 ([relevant_family_names.txt](remote_homology/relevant_family_names.txt))
- [x] Profile HMMs of relevant families fetched:
```sh
hmmfetch -f Pfam-A.hmm relevant_family_names.txt > relevant_pHMMs.hmm
```
- [x] Homology found using hmmsearch:
```sh
hmmsearch --tblout homologies.csv relevant_pHMMs.hmm ../Sep18p.curated.Ntm_env20_le10.fa
```
- [x] Added new domain annotations to [w_remhom_Sep18p.i2.curated.arch.Ad44](w_remhom_Sep18p.i2.curated.arch.Ad44) (inclusion threshold e-value: 0.01)

### Through clustering
- [x] Selecting the best method of clustering
    - [x] Preprocessing of clustering results (cluster_preprocess.py)
    - [x] Analysis of clusters and obtaining a score (cluster_analysis.py)

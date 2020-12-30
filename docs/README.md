# Notebook

## 30.12.2020

Confused about why easy-cluster and cluster give me different results.

Figured out it's because createdb defaults to --shuffle 1 and db creation step in easy-cluster defaults to --shuffle 0 (I think? Documentation says otherwise but changing it to 0 gives me the same result as easy-cluster).

```sh
mmseqs createdb ../Sep18p.curated.Ntm_env20_le10.fa Sep18DB --shuffle 0
```

---

Trimmed the 20 residue envelope from every sequence and created 2 new FASTA files with minimum sequence length of 20 (Sep18p.curated.Ntm_minlen20.fa) and 30 (Sep18p.curated.Ntm_minlen30.fa) using seqkit.

```sh
cat Sep18p.curated.Ntm_env20_le10.fa | seqkit mutate -w 0 -d -20:-1 --quiet | seqkit seq -w 0 -m 20 > Sep18p.curated.Ntm_minlen20.fa
```

---

Clustered minlen20 and minlen30 (--cluster-mode 1).

```sh
mmseqs cluster m20DB m20outDB tmp --cluster-mode 1
mmseqs cluster m30DB m30outDB tmp --cluster-mode 1
```

Results (although somewhat pointless):
- minlen20: 
    Precision: 99.715
    Recall: 67.97
    F1 score: 80.838
- minlen30:
    Precision: 99.715
    Recall: 62.033
    F1 score: 76.484

---

Thinking about switching to a src/ data/ structure (module-oriented?)

Attempted to switch to aforementioned structure (half-assed)

---

To-do for tomorrow:
- Integrate mmseqs databases
- Build better pipeline for multiple mmeqs databases and fix evaluation module (parameters and file naming).
- Basically complete the structural reform
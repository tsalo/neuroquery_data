minimal set of data to conduct meta-analysis with the neuroquery corpus.

- `corpus_tfidf.npz` contains a sparse matrix of TFIDF features: (13881 documents x 6308 expressions). It can be loaded with `scipy.sparse.load_npz`.
- feature_names.txt gives the expression corresponding to each column of `corpus_tfidf.npz` (one per line).
- pmids.txt gives the PubMed id corresponding to each row of `corpus_tfidf.npz` (one per line)
- `coordinates.csv` contains sterotactic coordinates extracted from each
  article. These can be transformed into brain maps using for example
  https://gist.github.com/jeromedockes/142a0e51237a93ea61a68eb3d0c01ddc

## type-count files

term counts for documents in the training corpus

can be read with scipy.sparse.load_npz
each row corresponds to a pubmed ID (pmid) in pmids.txt, and each column
correspond to a term in vocabulary.txt.

when a colocation from the vocabulary occurs, such as "cingulate cortex", only
the colocation is counted, and not the individual terms (even if they are also
in the vocabulary).
For example "cingulate cortex and later cortex on its own" results in

"cingulate"        : 0
"cingulate cortex" : 1
"cortex"           : 1

note that around 20% of articles do not have keywords (or none of their keywords
are in the vocabulary), and around 0.7% of abstracts are empty or missing as well.

## scGPT Analysis (Exploratory Representation Learning)

As part of this project, I explored the use of scGPT as a complementary representation learning framework for single-cell RNA-seq data.

This work was done prior to the current transformer-based modeling direction (Project Aurora), and served as an early step toward understanding how language-model-style architectures behave on large-scale single-cell datasets.

---

### Motivation

Traditional pipelines (Seurat, Scanpy, scVI) are highly effective for:

- Integration  
- Clustering  
- Label transfer  

However, they are not designed to:

- Learn generalizable embeddings across biological contexts  
- Capture higher-order gene–gene dependencies  
- Operate in a tokenized / sequence-based framework  

scGPT provided a way to experiment with these ideas.

---

### Approach

scGPT was applied to the integrated bone marrow dataset to:

- Generate **metagene representations** from expression data  
- Perform **zero-shot clustering** without explicit supervision  
- Evaluate whether learned embeddings capture known biological structure  

Key steps included:

- Input preparation from AnnData objects (count-preserving where possible)  
- Iterative clustering using scGPT embeddings  
- Comparison against scANVI-derived annotations  
- Extraction of metagenes associated with differential states (e.g., responder vs non-responder)

---

### Observations

- scGPT embeddings captured **broad lineage structure** reasonably well  
- Performance degraded for **fine-grained cell type distinctions** compared to scANVI  
- Metagenes provided **interpretable signals**, but required careful validation  
- Iterative clustering was sensitive to initialization and parameter choices  

Overall, scGPT behaved as a useful exploratory tool, but not a replacement for the integration + annotation pipeline.

---

### Limitations

- No native handling of batch structure comparable to scVI  
- Sensitivity to input preprocessing choices  
- Limited interpretability without downstream analysis  
- Scaling challenges when applied to very large datasets (~millions of cells)

---

### Role in This Project

This work helped inform the current modeling direction:

- Reinforced the value of **transformer architectures for biological data**
- Highlighted the importance of **structured input representations**
- Motivated the development of a **custom transformer pipeline** (Project Aurora)

Rather than using scGPT directly in the final pipeline, its strengths and limitations were used to guide the design of a more tailored approach.

---

### Status

Exploratory analysis complete.  
Not part of the primary modeling pipeline, but remains a useful reference for representation learning experiments.

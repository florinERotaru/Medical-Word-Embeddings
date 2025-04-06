# **Medical Word Embeddings**
### (BSc Thesis - Florin Rotaru, [*FII@UAIC*](https://www.info.uaic.ro/), 2024)

* Word2Vec Sip-Gram with negative sampling method
(Mikolov et al 2013)
* Trained on 16 088 [PubMed articles](https://ftp.ncbi.nlm.nih.gov/pub/pmc/oa_bulk/oa_comm/txt/), 500 MB of data

* Version|WS2-NEG4|WS4-NEG7|
  |------|--------|--------|
  |window size|2|4|
  |negative samples|4|7|

* Three correlation coefficient tests on 3 correlation test sets (concept pairs with professionally ranked similarity).

| **Dataset**          | **`WS2-NEG4`** | **`WS4-NEG7`** | **`GloVe-6B-100D`** | **`word2vec-100B-300D`** |
|----------------------|----------------|----------------|---------------------|-------------------------|
| **Pederesen’s (30)** | 0.366          | **0.517**        | 0.392               | 0.31                    |
| **Pakhomov’s (77)**  | **0.203**        | 0.185          | 0.101               | 0.064                   |
| **Hliaoutakis’ (34)**| 0.261          | 0.273          | **0.347**             | 0.297                   |
| **Corpus Size**      | 72.6M          | 72.6M          | 6B                  | 100B                    |

* Information extraction
    1. SVM for [this task of document classification](https://www.kaggle.com/datasets/marcelhiltner/pubmed-human-veterinary-medicine-classification) (human/veterinary articles).


    | **Metric**      | **`WS2-NEG4`** | **`WS4-NEG7`** | **`GloVe-6B-100D`** | **`word2vec-100B-300D`** |
    |-----------------|----------------|----------------|---------------------|-------------------------|
    | **Accuracy**    | 0.9501         | 0.968          | 0.9472              | 0.986                   |
    | **F1-Score**    | 0.9500         | 0.968          | 0.9471              | 0.986                   |
    | **Precision**   | 0.9514         | 0.968          | 0.9481              | 0.987                   |
    | **Recall**      | 0.9487         | 0.967          | 0.9462              | 0.986                   |
    | **Corpus Size** | 72.6M          | 72.6M          | 6B                  | 100B                    |

    **Table 1:** Accuracy, Precision, Recall, and F1-Score on the human/veterinary medicine classification task with an **RBF** Kernel SVM


    2. SVM for human status SMOKER detection introduced by [this article](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC2274873/).

    | **Metric**      | **`WS2-NEG4`** | **`WS2.5-NEG7`** | **`GloVe-6B-100D`** | **`word2vec-100B-300D`** |
    |-----------------|----------------|------------------|---------------------|-------------------------|
    | **Accuracy**    | 0.485          | 0.504            | 0.445               | 0.584                   |
    | **F1-Score**    | 0.482          | 0.51             | 0.43                | 0.536                   |
    | **Precision**   | 0.542          | 0.566            | 0.449               | 0.559                   |
    | **Recall**      | 0.485          | 0.504            | 0.445               | 0.584                   |
    | **Corpus Size** | 72.6M          | 72.6M            | 6B                  | 100B                    |

    **Table 2:** Accuracy, Precision, Recall, and F1-Score on the smoking status detection task with a **Linear** Kernel SVM





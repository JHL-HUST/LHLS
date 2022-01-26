## Leanring-based Hybrid Local Search (LHLS) Algorithm

This repository contains code to reproduce results from the paper:

[**Learning-based Hybrid Local Search Algorithm for Hard-label Textual Attack**](https://arxiv.org/abs/2201.08193)


## Requirements

- torch == 1.7.1
- tensorflow-gpu == 1.15.0
- tensorflow-hub == 0.10.0
- numpy == 1.19.5
- nltk == 3.3
- language-tool-python == 2.5.3
- Pattern == 3.6


## Datesets

There are eight datasets used in our experiments including `AG's News`, `IMDB`, `MR`, `Yelp`, `Yahoo! Answers`, `SNLI`, `MNLI` and `MNLIm`. The sampled texts for evaluation are adopted from the [github repo](https://github.com/RishabhMaheshwary/hard-label-attack/tree/main/data) of [HLA](https://arxiv.org/abs/2012.14956). You could download and place the dataset into the directory `./data/dataset`.

## Target Model

We adopt the pretrained models provided by [HLA](https://arxiv.org/abs/2012.14956), including [BERT](https://drive.google.com/file/d/1UChkyjrSJAVBpb3DcPwDhZUE4FuL0J25/view?usp=sharing), [WordCNN](https://drive.google.com/drive/folders/149Y5R6GIGDpBIaJhgG8rRaOslM21aA0Q?usp=sharing), [WordLSTM](https://drive.google.com/drive/folders/1nnf3wrYBrSt6F3Ms10wsDTTGFodrRFEW?usp=sharing). You could put these pretrained models `BERT`, `WordCNN` and `WordLSTM` into the directory `./data/model/bert`, `./data/model/WordCNN`, `./data/model/WordLSTM`,  respectively.

## Dependencies

There are three dependencies for this project. Download and put `glove.6B.200d.txt` to the directory `/data/embedding`. And put `counter-fitted-vectors.txt` and the top synonym file `mat.txt` to the directory `./data/aux_files`.

- [GloVe vecors](https://nlp.stanford.edu/data/glove.6B.zip)
- [Counter fitted vectors](https://drive.google.com/file/d/1bayGomljWb6HeYDMTDKXrh0HackKtSlx/view)
- [Mat](https://drive.google.com/file/d/1AIz8Imvv8OmHxVwY5kx10iwKAUzD6ODx/view)


## File Description

- `attack.py`: Attack the target model for text classification with LHLS.
- `attack_nli.py`: Attack the target model for textual entailment with LHLS.
- `config.py`: Parameters of attack for all datasets.
- `./adv_method`: Implementation for our LHLS.
- `./data`: Dataset, embedding matrix and various aux files.
- `./model_loader`: Target model, including BERT, WordCNN and WordLSTM.
- `./utils`: Helper functions for building dictionaries, loading data, and processing embedding matrix etc.
- `./parameter`: All hyper-parameters of our LHLS for various target models and datasets in our main experiments.
- `./scripts`: Commands to run the attack.


## Experiments

Taking the LHLS attack on BERT using MR dataset for example, you could run the following command:

   ```shell
sh scripts/bert_mr.sh
   ```

You could change the hyper-parameters of LHLS in the `./parameter/bert_mr.yaml` if necessary.


## Citation
If you find this code and data useful, please consider citing the original work by authors:
   ```
@article{yu2022learning,
  title={Learning-based Hybrid Local Search for the Hard-label Textual Attack},
  author={Yu, Zhen and Wang, Xiaosen and Che, Wanxiang and He, Kun},
  journal={arXiv preprint arXiv:2201.08193},
  year={2022}
}
   ```


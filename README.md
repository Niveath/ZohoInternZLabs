# ZohoInternZLabs

# Mapping CVEs to MITRE ATT&CK Framework using SecureBERT

## Dataset used : 

- [This dataset has a list of CVEs and a corresponding description of the vulnerability.](https://www.kaggle.com/datasets/andrewkronser/cve-common-vulnerabilities-and-exposures)
- [This dataset has a list of enterprise MITRE ATT&CK techniques and a description of each.](https://attack.mitre.org/docs/enterprise-attack-v13.1/enterprise-attack-v13.1-techniques.xlsx)

## Approach : 

- Generate embeddings for the CVEs' description.
- Generate embeddings for the MITRE ATT&CK framework techniques' description.
- The embeddings are generated using a SecureBERT(Aghael et al., [2022](https://arxiv.org/abs/2204.02685)) model. This is RoBERTa model fine-tuned for understanding cybersecurity contexts.
- The CVEs are mapped to the corresponding MITRE ATT&CK Framework using maximum cosine similarity.
- [The model was taken from HuggingFace.](https://huggingface.co/ehsanaghaei/SecureBERT)

# Sysmon Log Classification using XGboost

## Dataset Used :

- [This dataset has 3772 Sysmon event logs from 100 processes. Each process has been labelled as either legitimate or malicious](https://github.com/dtrizna/SysmonRNN/tree/master/data)

## Approach : 

- XGBoost based classifier model is used due to highly categorical nature of data.

## Results :

- Acheived F<sub>1</sub> score of 0.91 on training data and 0.67 on testing data.

# FontCode: Embedding Information in Text Documents using Glyph Perturbation

Find the code to perform encoding and decoding of text [here](https://github.com/Niveath/ZohoInternZLabs/blob/main/FontCode.ipynb)

Find the original paper [here](https://arxiv.org/pdf/1707.09418.pdf)

# Image Enhancement

## Dataset used:

- [This dataset has a set of camera images of documents with various imperfections such as folding, curved, etc.](https://sg-vilab.github.io/event/warpdoc/)

## Approach:

Pertubation based text embedding techniques greatly depend on the quality of image when decoding. Hence, to improve the image quality, we perform the following process

- Perform image dewarping to correct the angle. The [DocTr++](https://arxiv.org/pdf/2304.08796.pdf) model was used.
- Super resolution was perform to 2x scale. [Real-ESRGAN](https://huggingface.co/ai-forever/Real-ESRGAN) model was used. 

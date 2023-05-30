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

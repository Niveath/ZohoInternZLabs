# ZohoInternZLabs

# Mapping CVEs to MITRE ATT&CK Framework using SecureBERT

## Dataset used : 

- [This dataset has a list of CVEs and a corresponding description of the vulnerability.](https://www.kaggle.com/datasets/andrewkronser/cve-common-vulnerabilities-and-exposures).
- [This dataset has a list of enterprise MITRE ATT&CK techniques and a description of each.](https://attack.mitre.org/docs/enterprise-attack-v13.1/enterprise-attack-v13.1-techniques.xlsx).

## Approach : 

- Generate embeddings for the CVEs' description.
- Generate embeddings for the MITRE ATT&CK framework techniques' description.
- The embeddings are generated using a SecureBERT(Aghael et al., [2022](https://arxiv.org/abs/2204.02685)) model. This is RoBERTa model fine-tuned for understanding cybersecurity contexts.
- The CVEs are mapped to the corresponding MITRE ATT&CK Framework using maximum cosine similarity.
- [The model was taken from HuggingFace.](https://huggingface.co/ehsanaghaei/SecureBERT).

# Sysmon Log Classification using XGboost

## Dataset Used :

- [This dataset has 3772 Sysmon event logs from 100 processes. Each process has been labelled as either legitimate or malicious](https://github.com/dtrizna/SysmonRNN/tree/master/data).

## Approach : 

- XGBoost based classifier model is used due to highly categorical nature of data.

## Results :

- Acheived F<sub>1</sub> score of 0.91 on training data and 0.67 on testing data.

# Watermarking

## FontCode: Embedding Information in Text Documents using Glyph Perturbation

This is a novel method of text steganography, where information in embedded in text by slightly perturbing the character glyphs. A CNN network is used to analyse a perturbed text image and decode the information.

Find the original paper [here](https://arxiv.org/pdf/1707.09418.pdf).

We hope to extend this method to perform watermarking. Current watermarking methods, are highly format specific. If a document is printed or screen-captured, all watermarking data is lost. Using this new approach, we hope to develop a robust cross-format, tamper-proof watermarking system.

## Image Enhancement

### Dataset used:

- [This dataset has a set of camera images of documents with various imperfections such as folding, curved, etc.](https://sg-vilab.github.io/event/warpdoc/).

- Another screenshot dataset was created by us which can be found [here](https://drive.google.com/file/d/1RdCkew6z_Y5qHbexwY80urxxNB0pUqNf/view?usp=sharing).

### Approach:

Pertubation based text embedding techniques greatly depend on the quality of image when decoding. Hence, to improve the image quality, we perform the following process:

#### Image Dewarping:

We perform image dewraping to correct the angular imperfections in the image. The pretrained [DocTr++](https://arxiv.org/pdf/2304.08796.pdf) model was used via Gradio Client. Find the demo [here](https://doctrp.docscanner.top/).

#### Super Resolution:

Super resolution was performed to 2x scale to improve OCR capabilities. [Real-ESRGAN](https://huggingface.co/ai-forever/Real-ESRGAN) model was used. Find their GitHub repository [here](https://github.com/ai-forever/Real-ESRGAN).

#### Moire Pattern Removal:

We perform moire-removal to images which have been captured from a computer screen. We explore two models, [MopNet](https://github.com/PKU-IMRE/MopNet) and [ESDNet](https://github.com/CVMI-Lab/UHDM). ESDNet has much better performance, with lower number of trainable parameters. The model was also finetuned on our original dataset which can be found. The dataset has 510 screen-captured images of computer screens which have been artifically augmented with a moire pattern. The finetuned model weights and the dataset can be found [here](https://drive.google.com/drive/u/0/folders/1y0JjSFGWNEsSnZJnEWBOVdx6emU4Bek3).

### Analyzing the results:

To quantify the improvement in image quality, we perform OCR on images, before and after the image enhancement process and calculate the edit distance between the words identified. Tesseract OCR was used to get character and word level bounding boxes.

To further analyse the robustness of the pipeline, several image augmentations such as gaussian blur and motion blur were applied. The pipeline was also tested on JPEG image format.

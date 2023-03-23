# Text Detoxification

| toxic text   |      neutral paraphrase      |
|----------|-------------|
| this is scaring the s\*\*t out of me. | This is really scaring me.  |
| calm the f\*\*k down | Please calm your nerves  |
| its a crock of s\*\*t , and you know it. | It's senseless, you know it  |

This repo summarize all the information about Text Detoxification project. Here, you can find all dataset, evaluation setups, and SOTA models for text detoxification for Enlgish and Russian languages.

---

## Datasets

1. EnParaDetox: 🤗 https://huggingface.co/datasets/s-nlp/paradetox
2. RuParaDetox: 🤗 https://huggingface.co/datasets/s-nlp/ru_paradetox

---

## Models

1. English SOTA: 🤗 https://huggingface.co/s-nlp/bart-base-detox
2. Russian SOTA: 🤗 https://huggingface.co/s-nlp/ruT5-base-detox

---

## Evaluation
Automatic evaluation always is separated into three parameters: (i) ***style transfer accuracy*** (STA) which is usually estimated by toxicity classifier; (ii) ***content similarity*** (SIM) which can be estimated either via cosine simiarity between embeddings or as a score from a classifier; (iii) ***fluency*** (FL) which can be estimated either via perplexity from LM or as a score from language acceptability classifier. The most recent evaluation setup for the languages:

### English
1. Toxicity classifier: 🤗 https://huggingface.co/s-nlp/roberta_toxicity_classifier
2. Content similarity classifier: 🤗 
3. Fluency classifier: 🤗 https://huggingface.co/cointegrated/roberta-large-cola-krishna2020

### Russian
1. Toxicity classifier: 🤗 https://huggingface.co/IlyaGusev/rubertconv_toxic_clf
2. Text embedder: 🤗 https://huggingface.co/sentence-transformers/LaBSE (russian part)
3. Fluency classifier: 🤗
---
## Demos

You can check our [telegram bot](https://t.me/rudetoxifierbot) and take out all the anger on it!

---
## Github Pages
1. [The first version of Russian Texts Detoxifier](https://github.com/s-nlp/rudetoxifier): simple baselines, Russian condBERT, ruGPT-3.
2. [Unsupervised English Texts Detoxiifcation](https://github.com/s-nlp/detox): English condBERT, ParaGedi.
3. [English ParaDetox](https://github.com/s-nlp/paradetox): English ParaDetox dataset, the first supervised English detoxification SOTA ``bart-detox``.
4. [Russian ParaDetox](https://github.com/s-nlp/russe_detox_2022): competition RUSSE-2022 details, Russian ParaDetox dataset, the first supervised Russian detoxification SOTA ``ruT5-detox``
---

## Papers
1. Logacheva, V.**\***, Dementieva, D.**\***, Ustyantsev, S., Moskovskiy, D., Dale, D., Krotova, I., ... & Panchenko, A. (2022, May). **ParaDetox: Detoxification with Parallel Data**. In *Proceedings of the 60th Annual Meeting of the Association for Computational Linguistics (Volume 1: Long Papers) (pp. 6804-6818)*. (\*equal contribution) ***TL;DR*** EnParaDetox and EnDetox SOTA. [[paper](https://aclanthology.org/2022.acl-long.469/)]
2. Dementieva, D., Logacheva, V., Nikishina, I., Fenogenova, A., Dale, D., Krotova, I., ... & Panchenko, A. **RUSSE-2022: Findings of the First Russian Detoxification Shared Task Based on Parallel Corpora**. ***TL;DR*** RuParaDetox and RuDetox SOTA. [[paper](https://www.dialog-21.ru/media/5755/dementievadplusetal105.pdf)]
3. Dementieva, D., Moskovskiy, D., Logacheva, V., Dale, D., Kozlova, O., Semenov, N., & Panchenko, A. (2021). **Methods for detoxification of texts for the russian language**. *Multimodal Technologies and Interaction, 5(9), 54*. ***TL;DR*** The first detoxification experiments on Russian, unsupervised, condBERT for TST. [[paper](https://www.mdpi.com/2414-4088/5/9/54/pdf)]
4. Dale, D., Voronov, A., Dementieva, D., Logacheva, V., Kozlova, O., Semenov, N., & Panchenko, A. (2021, November). **Text Detoxification using Large Pre-trained Neural Models**. In *Proceedings of the 2021 Conference on Empirical Methods in Natural Language Processing (pp. 7979-7996)*. ***TL;DR*** Unsupervised English detoxification based on condBERT and ParaGedi. [[paper](https://aclanthology.org/2021.emnlp-main.629/)]
5. Logacheva, V.**\***, Dementieva, D.**\***, Krotova, I., Fenogenova, A., Nikishina, I., Shavrina, T., & Panchenko, A. (2022, May). **A Study on Manual and Automatic Evaluation for Text Style Transfer: The Case of Detoxification**. In *Proceedings of the 2nd Workshop on Human Evaluation of NLP Systems (HumEval) (pp. 90-101)*. (\*equal contribution) ***TL;DR*** The problems in automatic evaluation of TST tasks. [[paper](https://aclanthology.org/2022.humeval-1.8/)]
6. Moskovskiy, D., Dementieva, D., & Panchenko, A. (2022, May). **Exploring Cross-lingual Text Detoxification with Large Multilingual Language Models**. In *Proceedings of the 60th Annual Meeting of the Association for Computational Linguistics: Student Research Workshop (pp. 346-354)*. ***TL;DR*** Transferring detoxification knowledge between English and Russian. [[paper](https://aclanthology.org/2022.acl-srw.26/)]

---

## Contact

Any question, suggestions, discussions to: Daryna Dementieva (dardem96@gmail.com)

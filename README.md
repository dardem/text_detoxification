# Text Detoxification with Parallel Data

| toxic text   |      neutral paraphrase      |
|----------|-------------|
| this is scaring the s\*\*t out of me. | This is really scaring me.  |
| calm the f\*\*k down | Please calm your nerves  |
| its a crock of s\*\*t , and you know it. | It's senseless, you know it  |

This repo summarize all the information about Text Detoxification project. Here, you can find all dataset, evaluation setups, and SOTA models for text detoxification for Enlgish and Russian languages.

📰 **Updates**

Check out **TextDetox** 🤗 https://huggingface.co/collections/textdetox/ -- continuation of ParaDetox project!

**[2025] !!!NOW OPEN!!! TextDetox CLEF2025 shared task: for even more -- 15 languages!** [website](https://pan.webis.de/clef25/pan25-web/text-detoxification.html) 🤗[Starter Kit](https://huggingface.co/collections/textdetox/)

**[2025] COLNG2025**: Daryna Dementieva, Nikolay Babakov, Amit Ronen, Abinew Ali Ayele, Naquee Rizwan, Florian Schneider, Xintong Wang, Seid Muhie Yimam, Daniil Alekhseevich Moskovskiy, Elisei Stakovskii, Eran Kaufman, Ashraf Elnagar, Animesh Mukherjee, and Alexander Panchenko. 2025. ***Multilingual and Explainable Text Detoxification with Parallel Corpora***. In Proceedings of the 31st International Conference on Computational Linguistics, pages 7998–8025, Abu Dhabi, UAE. Association for Computational Linguistics. [pdf](https://aclanthology.org/2025.coling-main.535/)

**[2024]** We have also created versions of ParaDetox in more languages. You can checkout a [RuParaDetox](https://huggingface.co/datasets/s-nlp/ru_paradetox) dataset as well as a [Multilingual TextDetox](https://huggingface.co/textdetox) project that includes 9 languages.

Corresponding papers:
* [MultiParaDetox: Extending Text Detoxification with Parallel Data to New Languages](https://aclanthology.org/2024.naacl-short.12/) (NAACL 2024)
* [Overview of the multilingual text detoxification task at pan 2024](https://ceur-ws.org/Vol-3740/paper-223.pdf) (CLEF Shared Task 2024)

## Where text detoxification can be used?

![](https://github.com/dardem/text_detoxification/blob/main/detox_usage.png)

1. Before training your language model, chatbot, you can preprocess scrapped training data to ensure that there will be no toxicity. But, you should not just through away your samples. You can detoxify them! Then, the major part of the dataset will not be lost but the content will be saved.
2. You can ensure that the user message is also non-toxic. Again, the replica will be saved. Now after detoxification, we will ensure that the conversation will not be transferred into unsafe tone.
3. You can cross-save the answers from your chat-bot as well! The conversation will not be stopped even if you chat-bot generates something toxic. Its reply will be detoxified and the user will see neutral answer.

## Main Idea

We are the first to address text detoxification task as seq2seq generation task. To achieve this, we collected the parallel corpora of pairs toxic<->non-toxic texts (See illustration). After that, we trained LM on this corpora to perform detoxification task. These models perform very good and definitely way better than previous unsupervised approaches.

![](https://github.com/dardem/text_detoxification/blob/main/schema.jpg)

---

## Datasets

We release all the main ParaDetox datates as well as the results of crowdsourcing tasks:
* The negatily marked samples from *Paraphrasing* task can be used to train classifier to detect if the sentence is detoxified in general or not;
* The results from *Content* task can be used to train paraphrase detector between toxic and non-toxic texts and then to measure texts similarity.
* The results from *Toxicity* task can be used as additional data for toxicity classification.

### English

1. EnParaDetox: 🤗 [paradetox](https://huggingface.co/datasets/s-nlp/paradetox)
2. EnParaDetox: Paraphrase Task Negative Results: 🤗 [en_non_detoxified](https://huggingface.co/datasets/s-nlp/en_non_detoxified)
3. EnParaDetox: Content Task Results: 🤗 [en_paradetox_content](https://huggingface.co/datasets/s-nlp/en_paradetox_content)
4. EnParaDetox: Toxicity Task Results: 🤗 [en_paradetox_toxicity](https://huggingface.co/datasets/s-nlp/en_paradetox_toxicity)
5. Additionally, we filtered [ParaNMT](https://aclanthology.org/P18-1042/) corpus to have detoxified pairs: 🤗 [paranmt_for_detox](https://huggingface.co/datasets/dardem/paranmt_for_detox)

### Russian

1. RuParaDetox: 🤗 [ru_paradetox](https://huggingface.co/datasets/s-nlp/ru_paradetox)
2. RuParaDetox: Paraphrase Task Negative Results: 🤗 [ru_non_detoxified](https://huggingface.co/datasets/s-nlp/ru_non_detoxified)
3. RuParaDetox: Content Task Results: 🤗 [ru_paradetox_content](https://huggingface.co/datasets/s-nlp/ru_paradetox_content)
4. RuParaDetox: Toxicity Task Results: 🤗 [ru_paradetox_toxicity](https://huggingface.co/datasets/s-nlp/ru_paradetox_toxicity)

---

## Models

1. English SOTA: 🤗 [bart-base-detox]( https://huggingface.co/s-nlp/bart-base-detox)

![](https://github.com/dardem/text_detoxification/blob/main/en_manual_results.png)

2. Russian SOTA: 🤗 [ruT5-base-detox](https://huggingface.co/s-nlp/ruT5-base-detox)

![](https://github.com/dardem/text_detoxification/blob/main/ru_manual_results.png)

---

## Evaluation
Automatic evaluation always is separated into three parameters: (i) ***style transfer accuracy*** (STA) which is usually estimated by toxicity classifier; (ii) ***content similarity*** (SIM) which can be estimated either via cosine simiarity between embeddings or as a score from a classifier; (iii) ***fluency*** (FL) which can be estimated either via perplexity from LM or as a score from language acceptability classifier. The most recent evaluation setup for the languages:

### English
1. Toxicity classifier: 🤗 [roberta_toxicity_classifier](https://huggingface.co/s-nlp/roberta_toxicity_classifier)
2. Text embedder: 🤗 [LaBSE](https://huggingface.co/sentence-transformers/LaBSE)
3. Fluency classifier: 🤗 [roberta-large-cola-krishna2020](https://huggingface.co/cointegrated/roberta-large-cola-krishna2020)

### Russian
1. Toxicity classifier: 🤗 [rubertconv_toxic_clf](https://huggingface.co/IlyaGusev/rubertconv_toxic_clf)
2. Text embedder: 🤗 [fine-tuned RuBERT](https://huggingface.co/s-nlp/rubert-base-cased-conversational-paraphrase-v1)
3. Fluency classifier: 🤗 [ruRoBERTa-large-rucola](https://huggingface.co/RussianNLP/ruRoBERTa-large-rucola)

---
## Demos

You can check our [telegram bot](https://t.me/rudetoxifierbot) and take out all the anger on it!

---
## Relevant Github Pages
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

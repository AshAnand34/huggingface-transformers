<!--Copyright 2020 The HuggingFace Team. All rights reserved.

Licensed under the Apache License, Version 2.0 (the "License"); you may not use this file except in compliance with
the License. You may obtain a copy of the License at

http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software distributed under the License is distributed on
an "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied. See the License for the
specific language governing permissions and limitations under the License.

⚠️ Note that this file is in Markdown but contain specific syntax for our doc-builder (similar to MDX) that may not be
rendered properly in your Markdown viewer.

-->

# DeBERTa-v2

<div class="flex flex-wrap space-x-1">
<img alt="PyTorch" src="https://img.shields.io/badge/PyTorch-DE3412?style=flat&logo=pytorch&logoColor=white">
<img alt="TensorFlow" src="https://img.shields.io/badge/TensorFlow-FF6F00?style=flat&logo=tensorflow&logoColor=white">
</div>

## Overview

The DeBERTa model was proposed in [DeBERTa: Decoding-enhanced BERT with Disentangled Attention](https://huggingface.co/papers/2006.03654) by Pengcheng He, Xiaodong Liu, Jianfeng Gao, Weizhu Chen It is based on Google's
BERT model released in 2018 and Facebook's RoBERTa model released in 2019.

It builds on RoBERTa with disentangled attention and enhanced mask decoder training with half of the data used in
RoBERTa.

The abstract from the paper is the following:

*Recent progress in pre-trained neural language models has significantly improved the performance of many natural
language processing (NLP) tasks. In this paper we propose a new model architecture DeBERTa (Decoding-enhanced BERT with
disentangled attention) that improves the BERT and RoBERTa models using two novel techniques. The first is the
disentangled attention mechanism, where each word is represented using two vectors that encode its content and
position, respectively, and the attention weights among words are computed using disentangled matrices on their
contents and relative positions. Second, an enhanced mask decoder is used to replace the output softmax layer to
predict the masked tokens for model pretraining. We show that these two techniques significantly improve the efficiency
of model pretraining and performance of downstream tasks. Compared to RoBERTa-Large, a DeBERTa model trained on half of
the training data performs consistently better on a wide range of NLP tasks, achieving improvements on MNLI by +0.9%
(90.2% vs. 91.1%), on SQuAD v2.0 by +2.3% (88.4% vs. 90.7%) and RACE by +3.6% (83.2% vs. 86.8%). The DeBERTa code and
pre-trained models will be made publicly available at https://github.com/microsoft/DeBERTa.*


The following information is visible directly on the [original implementation
repository](https://github.com/microsoft/DeBERTa). DeBERTa v2 is the second version of the DeBERTa model. It includes
the 1.5B model used for the SuperGLUE single-model submission and achieving 89.9, versus human baseline 89.8. You can
find more details about this submission in the authors'
[blog](https://www.microsoft.com/en-us/research/blog/microsoft-deberta-surpasses-human-performance-on-the-superglue-benchmark/)

New in v2:

- **Vocabulary** In v2 the tokenizer is changed to use a new vocabulary of size 128K built from the training data.
  Instead of a GPT2-based tokenizer, the tokenizer is now
  [sentencepiece-based](https://github.com/google/sentencepiece) tokenizer.
- **nGiE(nGram Induced Input Encoding)** The DeBERTa-v2 model uses an additional convolution layer aside with the first
  transformer layer to better learn the local dependency of input tokens.
- **Sharing position projection matrix with content projection matrix in attention layer** Based on previous
  experiments, this can save parameters without affecting the performance.
- **Apply bucket to encode relative positions** The DeBERTa-v2 model uses log bucket to encode relative positions
  similar to T5.
- **900M model & 1.5B model** Two additional model sizes are available: 900M and 1.5B, which significantly improves the
  performance of downstream tasks.

This model was contributed by [DeBERTa](https://huggingface.co/DeBERTa). This model TF 2.0 implementation was
contributed by [kamalkraj](https://huggingface.co/kamalkraj). The original code can be found [here](https://github.com/microsoft/DeBERTa).

## Resources

- [Text classification task guide](../tasks/sequence_classification)
- [Token classification task guide](../tasks/token_classification)
- [Question answering task guide](../tasks/question_answering)
- [Masked language modeling task guide](../tasks/masked_language_modeling)
- [Multiple choice task guide](../tasks/multiple_choice)

## DebertaV2Config

[[autodoc]] DebertaV2Config

## DebertaV2Tokenizer

[[autodoc]] DebertaV2Tokenizer
    - build_inputs_with_special_tokens
    - get_special_tokens_mask
    - create_token_type_ids_from_sequences
    - save_vocabulary

## DebertaV2TokenizerFast

[[autodoc]] DebertaV2TokenizerFast
    - build_inputs_with_special_tokens
    - create_token_type_ids_from_sequences

<frameworkcontent>
<pt>

## DebertaV2Model

[[autodoc]] DebertaV2Model
    - forward

## DebertaV2PreTrainedModel

[[autodoc]] DebertaV2PreTrainedModel
    - forward

## DebertaV2ForMaskedLM

[[autodoc]] DebertaV2ForMaskedLM
    - forward

## DebertaV2ForSequenceClassification

[[autodoc]] DebertaV2ForSequenceClassification
    - forward

## DebertaV2ForTokenClassification

[[autodoc]] DebertaV2ForTokenClassification
    - forward

## DebertaV2ForQuestionAnswering

[[autodoc]] DebertaV2ForQuestionAnswering
    - forward

## DebertaV2ForMultipleChoice

[[autodoc]] DebertaV2ForMultipleChoice
    - forward

</pt>
<tf>

## TFDebertaV2Model

[[autodoc]] TFDebertaV2Model
    - call

## TFDebertaV2PreTrainedModel

[[autodoc]] TFDebertaV2PreTrainedModel
    - call

## TFDebertaV2ForMaskedLM

[[autodoc]] TFDebertaV2ForMaskedLM
    - call

## TFDebertaV2ForSequenceClassification

[[autodoc]] TFDebertaV2ForSequenceClassification
    - call

## TFDebertaV2ForTokenClassification

[[autodoc]] TFDebertaV2ForTokenClassification
    - call

## TFDebertaV2ForQuestionAnswering

[[autodoc]] TFDebertaV2ForQuestionAnswering
    - call

## TFDebertaV2ForMultipleChoice

[[autodoc]] TFDebertaV2ForMultipleChoice
    - call

</tf>
</frameworkcontent>

# NLP Projects

Natural language processing (NLP) is a branch of artificial intelligence that helps computers understand, interpret and manipulate human language. During the NLP course of the Master's Degree in Artificial Intelligence and Robotics I had the chance to develope two small projects on natural language understanding, i.e. Named Entity Recognition (NER) and Semantic Role Labeling (SRL). Both the projects have been developed in a Colab environment, using Python and PyTorch.

## Named Entity Recognition
Within a sentence, every token must be tagged with some label. There are 4 lables to recognize: **ORG**anization, **PER**son, **LOC**ation, and **O**ther. For instance:

| PER  | O  | O | LOC | O | O | ORG |
| --- | --- | --- | --- | --- | --- | --- |
| John  | went | to | California | to | visit | Google |

The structure of the neural network architecture is 
  
[![word-char-model.jpg](https://i.postimg.cc/76KqzFWn/word-char-model.jpg)](https://postimg.cc/G8s0w5r4)

In particular:
- Every token is lemmatized
- The tokens are encapsulated into word embeddings, with the pretrained Word2Vec GloVe (100), plus a character embedding (50) built by a binary Long-short Term Memory (LSTM) network, which takes the character of each token normally and reversely.
- A binary LSTM is trained with the input embedding to classify each token

A more detailed description and explanation can be read in the [report](ner/report.pdf).

## Semantic Role Labeling
SRL is the task of addressing “Who did What to Whom, How, Where and When?” i.e. within a sentence, the agent, the predicate, and the patient have to be identified and classified. For instance

| - | Agent | Predicate (EAT_BITE) | - | Patient |
| --- | --- | --- | --- | --- |
| The  | cat | ate | the | fish |

The structure of the nerual network architecture is

[![extra-model.jpg](https://i.postimg.cc/MpxwHZsj/extra-model.jpg)](https://postimg.cc/gnMQBpbY)

In particular:
- Every token is lemmatized
- The tokens are encapsulated in word embeddings composed by GloVe (100) + Bidirectional Encoder Representations from Transformers (BERT) (768) + 1-hot Encoding (500)
- A binary LSTM is trained with the input embeddings
- The output is fed to two linear classifiers (Dense Layers) which outputs the role and the predicate

A more detailed description and explanation can be read in the [report](srl/report.pdf).

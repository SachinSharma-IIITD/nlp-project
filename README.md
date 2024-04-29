# Emotion-Cause Identification Project

This project focuses on the identification of emotions and their corresponding causes within conversations. The project is divided into two main tasks: Emotion Recognition in Conversation (ERC) and Emotion-Cause Pair Identification (ECPI).

## Dataset

The project utilizes the Emotion-Cause-in-Friends (ECF) dataset, which consists of a substantial amount of conversations between the characters of the show 'Friends'. The dataset includes 1,344 conversations and 13,509 utterances, with 9,272 emotion-cause pairs annotated across three distinct modalities.

## Methodology

### Task 1: Emotion Recognition in Conversation (ERC)

This task is divided into two models:

1. **Model 1 (BERT with Conversational Context Embeddings):** This model uses the context of the conversation and the speaker's name to identify emotions. The context embeddings are obtained from BERT and passed to the  BertForSequenceClassification model.

2. **Model 2 (BERT without Conversational Context Embeddings):** This model allows BERT to learn the context by predicting emotions for all utterances in a conversation and then backpropagating the combined loss.

### Task 2: Emotion-Cause Pair Identification (ECPI)

This task also uses two models:

1. **Model 1:** This model uses a fine-tuned pre-trained BERT for question answering to identify the span of the cause.

2. **Model 2:** This model uses a fine-tuned pre-trained BERT model to extract the target-cause/trigger pairs that led to the manifestation of a specific emotion. After identifying the cause pairs, it looks for the specific portion within the sentence, the 'span,' which acted as the primary trigger for expressing emotion.

## Experimental Setup

The input embeddings for all models are of size 512. The BERT models consist of Bert Embedding (Token + Positional), Bert Encoder (Self Attention + Add & Norm + FC), Pooling, and a Classifier (Dense + Softmax).

## Results

The results of the models are as follows:

- ERC Task 1: F1-Score: 0.53, Accuracy: 0.55
- Cause Span Task 2: F1-Score: 0.94, Accuracy: 0.95

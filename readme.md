## Emotion Recognition in Sarcastic Statements
## Overview
In today's AI-driven world, large language models like ChatGPT and Bard excel at interacting with users and answering queries. However, detecting human emotions, especially within sarcastic statements, remains a challenging task. Sarcasm often involves saying the opposite of what one means, relying on tone and context to convey the true, ironic sentiment. For example:

Sarcastic Statement: "Oh, wonderful! Another Monday morning!"
Intended Meaning: Despite the enthusiastic words, the speaker is expressing displeasure about the start of the workweek.

This project aims to tackle the challenge of sarcasm detection by comparing state-of-the-art models for both sarcasm and emotion detection. We also contribute to publicly available datasets and develop a model that can accurately discern emotions in sarcastic statements. Ultimately, the goal is to create a user-friendly interface to make this capability accessible to a broader audience.

## Objectives
The primary goals of this project are to:

Conduct a comparative analysis of existing models for sarcasm and emotion detection.
Develop a user-friendly interface for emotion detection within sarcastic statements.
Expand existing datasets to facilitate the evaluation of various models and the development of a model for detecting both emotions and sarcasm.
Domain
## This project falls under several key domains:

Sentiment Analysis: Focused on detecting emotions within text, making it a part of the broader sentiment analysis domain. The aim is to understand and categorize the emotional tone and opinions expressed in textual content.

Text Classification: Involves categorizing text data into predefined categories, such as classifying text as either sarcastic or non-sarcastic and identifying the associated emotions.

Machine Learning and Deep Learning: The project leverages machine learning and deep learning techniques to train models for sarcasm and emotion detection, placing it within the domain of AI research.

Linguistics: The exploration of sarcasm, tone, and language nuances intersects with linguistics, as it involves the study of language and its usage.

Application Development: Developing a user-friendly interface for emotion detection makes it easier for users to implement and use the model for predictions.

## Implementation
Dataset and its Usage
We utilize the multi-modal MUStARD sarcasm dataset, annotated with both sentiment and emotion classes, including implicit and explicit emotions. This dataset consists of raw video clips, their audio, and textual transcriptions from various TV shows and popular web series.

We begin with the MUStARD dataset, which includes 9 pre-annotated emotions, and then extend it using the MUStARD++ dataset. The extended dataset includes additional labels such as valence and arousal, which are crucial indicators of emotional intensity. The expanded dataset, nearly double the size of the original MUStARD dataset, includes features like emotion, valence, arousal, and sarcasm-type information.

Our study primarily focuses on understanding the speaker's emotion leading to sarcasm, utilizing the basic emotion annotations provided. Through extensive experiments with combinations of Video, Text, and Audio, and several state-of-the-art models, we observed that most errors arose when models predicted negative emotions while the true label was Neutral or Happy. A detailed qualitative analysis revealed that the labels for these sarcastic data points often seemed intuitively incorrect.

The multimodal dataset includes dialogues from sitcoms, each presented as a combination of the main "utterance" and the "context" in which it was spoken. The dataset consists of 1202 instances (utterance+context), with 601 sarcastic and 601 non-sarcastic instances. Each utterance is annotated with the following information:

# Table 5: Annotation of MUStARD++

Column	Description
Sarcasm	0 or 1 indicating the presence or absence of sarcasm
Sarcasm_Type	If sarcastic, indicates the type of sarcasm, else None
Implicit_Emotion	The perceived hidden emotion associated with an instance
Explicit_Emotion	The surface emotion associated with an instance
Valence	Level of pleasantness (1-9)
Arousal	Level of perceived intensity (1-9)
6.1.1 Key Features Used
Utterance: The text of the target utterance to classify.
Context: A list of utterances (in chronological order) preceding the target utterance.
Each sentence is annotated for both implicit and explicit emotions. The implicit emotion of an utterance is determined with the help of context, while the explicit emotion is determined directly from the utterance itself, without requiring external knowledge.

## Feature Extraction
Textual Features:
For feature extraction from transcripts (context and utterance), we experimented with different transformer models such as BERT, BART, RoBERTa, and T5. BART performed slightly better across all experiments (text alone, as well as in combination with audio and video) compared to the other models. Therefore, we used BART-large representations for text. BART provides a feature vector representation xt ∈ R dt for every instance x. We encoded the text using the BART Large model with dt = 1024 and used the mean of the last four transformer layer representations to obtain a unique embedding for both utterance and context.

BART:
BART is a denoising autoencoder designed for pretraining sequence-to-sequence models. It is trained by corrupting text with an arbitrary noising function and then learning to reconstruct the original text. BART utilizes a standard Transformer-based neural machine translation architecture.

## Dataset Expansion
We expanded the dataset by sourcing additional video clips from the internet, specifically looking for instances of sarcasm and emotional sentiment. These clips were tabulated and labeled based on the following columns:

Video ID
Textual Transcript (Utterance)
Speaker
Sarcasm (0 or 1)
Emotion (anger, excitement, fear, sad, surprise, frustrated, happy, neutral, disgust)

## How to Use
Clone the Repository:

git clone https://github.com/yourusername/Emotion_Recognition.git
Navigate to the Project Directory:
cd Emotion_Recognition
Install Dependencies: Ensure you have Python installed. Then install the necessary packages using:
pip install -r requirements.txt
Run the Jupyter Notebook: Open the provided Emotion_Recognition.ipynb file to explore the data analysis, model training, and evaluation steps.
User Interface: Follow the instructions in the notebook to set up and run the user-friendly interface for emotion detection.

## Contributions
Contributions are welcome! If you find a bug, or have a feature request or a suggestion, please open an issue or submit a pull request.
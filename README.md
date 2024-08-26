# GovBuzz - Ai Powered Citizen Grievance Lodging App

A hackathon project developed for the Smart India Hackathon (SIH) 2023. This app allows citizens to lodge complaints or grievances across multiple departments using text or voice input. The system utilizes AI models for spam detection and department classification.

## Table of Contents
- [Introduction](#introduction)
- [Features](#features)
- [How It Works](#how-it-works)
- [Tech Stack](#tech-stack)
- [Architecture](#architecture)
- [Model Details](#model-details)
- [Data Collection](#data-collection)
- [Preprocessing](#preprocessing)

## Introduction
The Citizen Grievance Lodging App was designed to streamline the process for citizens to report complaints or grievances to various government departments. The app is capable of receiving input via text or voice, processing the data, and then classifying the input into the appropriate department using advanced NLP techniques.

## Features
- **Text & Voice Input**: Citizens can lodge complaints through both text and voice commands.
- **Spam Detection**: Filters out irrelevant or non-complaint-related inputs.
- **Department Classification**: Automatically classifies complaints into departments such as Jal Shakti and Road Transport & Highways.

## How It Works
1. **User Input**: Citizens provide input by typing or through voice commands.
2. **Preprocessing**: The input data is cleaned, tokenized, and prepared for model processing.
3. **Spam Detection Model**: Determines if the input is valid for lodging a grievance.
4. **Department Detection Model**: Classifies the input into the appropriate department.

## Tech Stack
- **Programming Language**: Python
- **NLP Libraries**: NLTK, RegEx
- **Machine Learning Libraries**: TensorFlow, Scikit-learn
- **Deep Learning Models**: LSTM, Bidirectional LSTM
- **Data Collection Tools**: Web scraping from Twitter, Facebook, and Google Forms

## Architecture

The architecture of the Citizen Grievance Lodging App is designed to efficiently process user inputs, determine their validity, and classify them into the appropriate government department. The system comprises two core components: the **Spam/Ham Detection Model** and the **Department Classification Model**.

### 1. Spam/Ham Detection Model

The first step in processing user inputs is determining whether the input is relevant to lodging a grievance (ham) or if it is irrelevant/noise (spam). This is crucial to ensure that only valid complaints are further processed and classified.

- **Purpose**: To filter out non-relevant inputs, ensuring that the system only processes genuine grievances.
- **Implementation**: 
  - The Spam/Ham Detection Model is implemented using a **Bidirectional LSTM**. 
  - Bidirectional LSTMs are particularly suited for this task as they consider both past and future context, making them effective at understanding the structure and meaning of input text.
  - The model is trained on a labeled dataset of user inputs, with labels indicating whether the input is a valid complaint (ham) or spam.
  - The output is a binary classification: `0` for spam and `1` for ham.

**Example Workflow**:
1. A citizen submits a complaint via text or voice input.
2. The input is preprocessed (cleaning, tokenization, embedding).
3. The preprocessed input is passed through the Bidirectional LSTM model.
4. The model classifies the input as either spam or ham.
5. If classified as spam, the input is discarded; if ham, the input proceeds to the next stage.

### 2. Department Classification Model

Once the input is confirmed as a valid grievance, it needs to be routed to the correct department. The Department Classification Model handles this task by categorizing the input into one of the two departments: **Department of Jal Shakti** or **Department of Road Transport and Highways**.

- **Purpose**: To ensure that each valid grievance is directed to the appropriate government department for resolution.
- **Implementation**:
  - This model is implemented using a combination of **LSTM** and **Naive Bayes** classifiers.
  - **LSTM**: The LSTM model is utilized for its ability to handle sequential data and capture the contextual dependencies within the input text. It helps in understanding the underlying intent of the grievance.
  - **Naive Bayes**: The Naive Bayes classifier is used alongside LSTM for its efficiency and simplicity, particularly in text classification tasks. It provides a probabilistic approach to determining which department the grievance most likely pertains to.
  - The combination of these two models allows for a robust classification system that can accurately determine the correct department based on the content of the grievance.

**Example Workflow**:
1. The input is classified as ham and is passed to the Department Classification Model.
2. The LSTM model analyzes the input text to capture the sequence and context.
3. The Naive Bayes classifier evaluates the probability of the input belonging to either department.
4. The final classification result determines which department (Jal Shakti or Road Transport and Highways) the grievance should be forwarded to.


## Data Collection
- **Sources**: Twitter, Facebook, Google Forms
- **Methodology**: Data was scraped and collected to create a robust dataset of real grievances lodged by citizens.

## Preprocessing
- **Cleaning**: Removal of stop words, punctuation, and unwanted characters.
- **Tokenization**: Breaking down text into manageable tokens.
- **Embeddings**: Words are converted into embeddings for model input.
- **NLP Techniques Used**: NLTK, Regular Expressions (RegEx)







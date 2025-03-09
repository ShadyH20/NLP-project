# NLP Project Milestone 1: Data Preprocessing and Analysis

## Introduction

This milestone focuses on the preprocessing and analysis of datasets related to podcasts and YouTube channels. The primary objective is to clean the data, prepare it for machine learning tasks, and analyze it for any insights. It prepares the dataset for tasks such as Topic Modeling, Text Classification, or Multi-label Tagging.

### Datasets

The datasets involved are:

- **Spotify Podcasts Dataset**: consists of various podcast episodes, including raw scripts and metadata.
- **YouTube Channels Dataset**: includes YouTube video manuscripts from various famous channels.

The data is available in folders with scripts and corresponding metadata files. For this milestone, we selected the `YouTube Channels Dataset`.

## Steps Taken

### 1. Data Loading and Initial Inspection

The first step involved loading the dataset into a pandas DataFrame. The raw data consists of fields such as episode title, raw script, processed script, dialogue, type, length, and category. We then performed an initial inspection by reviewing a few sample rows from each channel to ensure that the data was correctly loaded and properly formatted.

### 2. Data Preprocessing

The data preprocessing phase focused on cleaning the raw text and metadata to ensure that it was ready for analysis and machine learning tasks. The preprocessing was divided into several steps:

#### a. **Stopword Removal**

Stopwords, such as common words like "the", "and", "is", etc., were removed from the text. These words do not contribute much to the meaning and can negatively impact the performance of machine learning models.

#### b. **Punctuation Removal**

Punctuation marks, including commas, periods, and special characters, were removed. This helps to simplify the text and ensures that the tokenization process does not treat punctuation as separate tokens.

#### c. **Text Normalization**

All text was converted to lowercase to maintain consistency. This ensures that words like "Data" and "data" are treated as the same token, preventing any case-sensitive mismatches during analysis.

#### d. **Tokenization**

The raw text was split into smaller units known as tokens (typically words). Tokenization allows us to treat each word or meaningful unit as a separate element, which is useful for various NLP tasks like topic modeling and classification.

#### e. **Stemming**

Stemming was applied to reduce words to their root form. For example, words like "running" and "runner" were reduced to "run". This helps to consolidate related words and reduces the number of unique tokens.

#### f. **Lemmatization**

In addition to stemming, lemmatization was performed to reduce words to their base form. Unlike stemming, lemmatization considers the context of a word to determine its base form. For example, "better" would be lemmatized to "good".

#### g. **Whitespace Removal**

Extra spaces, tabs, or newline characters were removed from the text. This ensures that the text is clean and consistent before further processing.

#### h. **Handling Non-Alphanumeric Characters**

Any non-alphanumeric characters (such as symbols and digits) were removed from the text. This ensures that the dataset consists only of meaningful words, making it easier to analyze and process for machine learning tasks.

### 3. Data Review and Insights

After preprocessing, we analyzed the cleaned dataset to extract insights. The analysis included checking the frequency of certain words across different channels and categories. This helped us identify popular topics and themes in the podcasts and YouTube videos.

### 4. Labeling and Categorization

Some of the data required labeling based on metadata, such as episode type or category. We used the available metadata to assign categories to the episodes, such as "Entertainment," "Education," etc. This labeling ensures that the dataset is ready for classification or other machine learning tasks.

## Conclusion

The primary objective of this milestone was to preprocess the dataset and make it ready for machine learning tasks. The key steps included data loading, cleaning, normalization, tokenization, stemming, lemmatization, and categorization. Through these steps, we were able to prepare the data for future modeling tasks and gain some initial insights into the dataset.

### Limitations

- **Missing Data**: Some episodes had missing metadata or incomplete scripts, which could affect analysis accuracy.
- **Language and Cultural Nuances**: Some transcripts might contain colloquialisms or language-specific phrases that need further normalization for broader NLP tasks.

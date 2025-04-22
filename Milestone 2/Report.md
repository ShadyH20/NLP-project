# Milestone 2 Report

## Methodology

### Installation & Dataset Loading

The notebook begins by installing the required libraries such as `datasets` and `torchtext`. It then loads the SQuAD dataset using the `datasets` library. The dataset is preprocessed to create tokenized versions of the context, question, and answer fields. The preprocessing also includes sorting the dataset by context length and limiting the number of samples for training and validation.

### Vocabulary & Embeddings

A vocabulary is built using the `torchtext` library, and GloVe embeddings are used to initialize the embedding matrix. Special tokens such as `<pad>`, `<sos>`, `<eos>`, and `<unk>` are added to the vocabulary. The embeddings for tokens not found in GloVe are initialized randomly.

### DataLoader

A custom `collate_fn` is implemented to pad sequences to the maximum length in each batch. The `DataLoader` is used to create batches for training and validation.

### Model Architecture

The model consists of an encoder, an attention mechanism, and a decoder:

- **Encoder**: A GRU-based encoder with pre-trained embeddings.
- **Attention**: A mechanism to compute attention weights over the encoder outputs.
- **Decoder**: A GRU-based decoder that uses the attention mechanism to generate answers.

### Training Setup & Loop

The training loop involves:

- Concatenating the context and question as input to the encoder.
- Using teacher forcing in the decoder to predict the next token in the answer sequence.
- Calculating the loss using `CrossEntropyLoss` and optimizing the model using the Adam optimizer.

Validation is performed after each epoch to evaluate the model's performance on unseen data.

## Limitations

1. **Dataset Size**: The dataset is limited to 20,000 training samples and 10,000 validation samples, which may not be representative of the full dataset.
2. **Embedding Initialization**: Tokens not found in GloVe are initialized randomly, which may affect the model's performance.
3. **Model Complexity**: The model architecture is relatively simple and may not capture complex relationships in the data.
4. **Evaluation Metrics**: The notebook only reports token-level accuracy, which may not fully reflect the model's ability to generate coherent answers.

## Suggestions for Improvement

1. **Data Augmentation**: Use data augmentation techniques to increase the diversity of the training data.
2. **Pre-trained Models**: Experiment with pre-trained models such as BERT or T5 for better performance.
3. **Hyperparameter Tuning**: Perform a systematic search for optimal hyperparameters such as learning rate, hidden dimensions, and batch size.
4. **Evaluation Metrics**: Include additional metrics such as BLEU or ROUGE to evaluate the quality of generated answers.
5. **Visualization**: Visualize the attention weights to understand the model's focus during answer generation.

## Results

The training and validation loss, along with token-level accuracy, are reported for each epoch. Below is a plot of the loss function over epochs:

![alt text](image.png)

The model shows a steady decrease in loss, indicating effective learning. However, further improvements are needed to achieve better performance.

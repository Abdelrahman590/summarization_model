# YouTube Transcript Summarization using Hugging Face Transformers

## Overview

This project demonstrates how to summarize long YouTube video transcripts using Hugging Face's `facebook/bart-large-cnn` model. Since transformer-based models have a maximum input token limit, the notebook implements a hierarchical summarization approach by splitting long transcripts into token-based chunks, summarizing each chunk individually, and then generating a final summary from the intermediate results.

---

## Features

- Extracts transcripts directly from YouTube videos.
- Automatically counts model tokens.
- Splits long transcripts into token-based chunks.
- Generates summaries for each chunk.
- Produces a final consolidated summary.
- Uses Hugging Face Transformers for abstractive summarization.
- Modular and easy to extend.

---

## Project Workflow

```text
YouTube Video URL
        │
        ▼
Extract Video ID
        │
        ▼
Download Transcript
        │
        ▼
Tokenization
        │
        ▼
Chunk Generation
        │
        ▼
Summarize Each Chunk
        │
        ▼
Combine Intermediate Summaries
        │
        ▼
Generate Final Summary
```

---

## Technologies Used

- Python
- Hugging Face Transformers
- PyTorch
- YouTube Transcript API
- SentencePiece

---

## Model

The notebook uses the following pretrained model:

| Model | Task |
|--------|------|
| `facebook/bart-large-cnn` | Abstractive Text Summarization |

---

## Installation

Install the required dependencies before running the notebook.

```bash
pip install youtube-transcript-api
pip install transformers torch sentencepiece
```

---

## Notebook Structure

The notebook consists of the following stages:

### 1. Transcript Extraction

The transcript is retrieved from a YouTube video using the YouTube Transcript API and combined into a single text document.

---

### 2. Token Counting

The transcript is tokenized using the same tokenizer as the summarization model to accurately determine the number of input tokens.

---

### 3. Token-Based Chunking

If the transcript exceeds the model's maximum context length, it is divided into smaller token-based chunks.

This ensures that each chunk can be processed without exceeding the model's input limitations.

---

### 4. Chunk Summarization

Each chunk is summarized independently using the Hugging Face summarization pipeline.

Typical generation parameters include:

- `max_length`
- `min_length`
- `do_sample=False`

---

### 5. Final Summarization

All intermediate summaries are concatenated into a single document.

The combined document is summarized once more to produce the final output.

This hierarchical approach enables summarization of transcripts that are significantly longer than the model's supported context window.

---

## Architecture

```text
                     YouTube Video
                           │
                           ▼
                Transcript Extraction
                           │
                           ▼
                   Tokenization
                           │
                           ▼
                  Token-Based Chunking
                           │
                           ▼
               Chunk-Level Summarization
                           │
                           ▼
             Merge Intermediate Summaries
                           │
                           ▼
                 Final Summarization
                           │
                           ▼
                    Final Summary
```

---

## Project Structure

```text
best-sol-intern-class.ipynb
│
├── Install dependencies
├── Import libraries
├── Extract transcript
├── Count tokens
├── Create token chunks
├── Load summarization model
├── Summarize chunks
├── Merge summaries
└── Generate final summary
```

---

## Advantages

- Supports long YouTube transcripts.
- Avoids transformer input length limitations.
- Produces coherent abstractive summaries.
- Uses a scalable hierarchical summarization pipeline.
- Can be adapted for articles, reports, PDFs, and other long documents.

---

## Future Improvements

- Support multilingual transcripts.
- Automatically detect transcript language.
- Integrate larger-context language models.
- Build a Streamlit or Gradio web interface.
- Export summaries to PDF or Microsoft Word.
- Add keyword extraction and topic classification.

---

## Author

**Abdelrahman Mahmoud Mosaad**

Artificial Intelligence Engineer

Areas of Interest:

- Large Language Models (LLMs)
- Retrieval-Augmented Generation (RAG)
- Natural Language Processing (NLP)
- Information Retrieval
- Intelligent Document Processing

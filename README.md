# RAG-ICD-Extraction-Pipeline
This repository implements a Retrieval-Augmented Generation (RAG) pipeline for ICD (International Classification of Diseases) code parsing and classification, using the Mistral-Small-24B-Instruct model and BioBERT-based sentence embeddings.

The project is designed to assist in the extraction and classification of medical concepts and conditions from clinical texts by leveraging LLM-based reasoning and biomedical embeddings.

## Features

    Sentence Embedding with nuvocare/WikiMedical_sent_biobert_multi

    Large Language Model via mistralai/Mistral-Small-24B-Instruct-2501

    Negation detection using spaCy + negspacy

    Rapid fuzzy matching for retrieval with rapidfuzz

    XML ICD Tree Parsing for dynamic lookup

    FAISS-based vector search for efficient retrieval


## Requirements

Key Dependencies

    torch

    sentence-transformers

    transformers

    vllm

    faiss-gpu

    negspacy

    spacy

    rapidfuzz

    huggingface_hub

## Hugging Face Authentication

Before using the Hugging Face models:

from huggingface_hub import login
login(token="YOUR_HF_TOKEN")

## Architecture Overview

    Parse ICD XML: Load ICD tree structure from WHO-provided XML data.

    Embed Concepts: Convert text to dense vectors using BioBERT.

    Build Vector Index: Use FAISS for scalable similarity search.

    Apply Negation Detection: Handle clinical negation with negspacy.

    Run RAG Query: Retrieve relevant ICD descriptions and query Mistral model.

    Return Final Classification.

## Project Structure

📦 RAG_ICD_Mistral
├── RAG_ICD_Mistral_Version3.ipynb  # Main notebook
├── icd_data/                       # ICD XML files
├── embeddings/                     # Saved embeddings
├── results/                        # Output results
└── README.md

## Example Use Case

Given a clinical sentence or doctors note:
text = "The patient shows no signs of myocardial infarction."

 1. Embed and search
 2. Retrieve closest ICD codes
 3. Apply RAG with Mistral to generate a reasoning-backed code suggestion

## Status

This is an experimental prototype. Intended for research and development only — not for clinical use.

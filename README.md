# NER Model: fuzzyethic/NER-ONETONOTE5

This is a Named Entity Recognition (NER) model created with [spaCy](https://spacy.io/). It is trained to identify and classify named entities in English text.

## Model Details

- **Model:** `fuzzyethic/NER-ONETONOTE5`
- **Language:** English (`en`)
- **Pipeline:** `ner`
- **spaCy Version:** `>=3.8.7,<3.9.0`
- **Hugging Face Hub:** [fuzzyethic/NER-ONETONOTE5](https://huggingface.co/fuzzyethic/NER-ONETONOTE5)

## Training

- **Dataset:** `onenote-5`
- **Evaluation Accuracy:** 81%

## Installation

```bash
pip install spacy huggingface_hub

USAGE

import spacy
from huggingface_hub import snapshot_download
import os

model_name = "fuzzyethic/NER-ONETONOTE5"

try:
    nlp = spacy.load(model_name)
    print(f"Successfully loaded '{model_name}' from cache.")
except OSError:
    print(f"Downloading '{model_name}' from Hugging Face Hub...")
    model_path = snapshot_download(repo_id=model_name)
    nlp = spacy.load(model_path)
    print("Model downloaded and loaded successfully.")

text = "Apple Company is looking at buying U.K. startup for $1 billion"

doc = nlp(text)

print("\nEntities found:")
for ent in doc.ents:
    print(f"- Text: '{ent.text}', Label: '{ent.label_}'")

```
OUTPUT

```
Downloading model fuzzyethic/NER-ONETONOTE5 from Hugging Face Hub...
Entities found:
- Apple (B-ORG)
- Company (I-ORG)
- U.K. (B-GPE)
- $ (B-MONEY)
- 1 (I-MONEY)
- billion (I-MONEY)
```

The model predicts entities in the IOB format with labels such as 

```
labels = [
    "B-CARDINAL", "B-DATE", "B-EVENT", "B-FAC", "B-GPE", "B-LANGUAGE", "B-LAW",
    "B-LOC", "B-MONEY", "B-NORP", "B-ORDINAL", "B-ORG", "B-PERCENT", "B-PERSON",
    "B-PRODUCT", "B-QUANTITY", "B-TIME", "B-WORK_OF_ART", "I-CARDINAL", "I-DATE",
    "I-EVENT", "I-FAC", "I-GPE", "I-LANGUAGE", "I-LAW", "I-LOC", "I-MONEY", "I-NORP",
    "I-ORDINAL", "I-ORG", "I-PERCENT", "I-PERSON", "I-PRODUCT", "I-QUANTITY",
    "I-TIME", "I-WORK_OF_ART"
]
```


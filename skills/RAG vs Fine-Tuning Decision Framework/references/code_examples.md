# Code Examples

## RAG Implementation

```python
from transformers import RagTokenizer, RagRetriever, RagTokenForGeneration

# Initialize the tokenizer, retriever, and model
tokenizer = RagTokenizer.from_pretrained('facebook/rag-token-base')
retriever = RagRetriever.from_pretrained('facebook/rag-token-base', index_name='custom')
model = RagTokenForGeneration.from_pretrained('facebook/rag-token-base', retriever=retriever)

# Encode the input question
input_ids = tokenizer("What is our leave policy?", return_tensors='pt').input_ids

# Generate the answer
outputs = model.generate(input_ids)

# Decode the output
answer = tokenizer.decode(outputs[0], skip_special_tokens=True)
print(answer)
```

## Fine-Tuning Implementation

```python
from transformers import Trainer, TrainingArguments, AutoModelForSequenceClassification, AutoTokenizer

# Load pre-trained model and tokenizer
model = AutoModelForSequenceClassification.from_pretrained('bert-base-uncased')
tokenizer = AutoTokenizer.from_pretrained('bert-base-uncased')

# Prepare the dataset
# Assume `train_dataset` and `eval_dataset` are already prepared

# Define training arguments
training_args = TrainingArguments(
    output_dir='./results',
    num_train_epochs=3,
    per_device_train_batch_size=16,
    per_device_eval_batch_size=16,
    warmup_steps=500,
    weight_decay=0.01,
    logging_dir='./logs',
)

# Initialize the Trainer
trainer = Trainer(
    model=model,
    args=training_args,
    train_dataset=train_dataset,
    eval_dataset=eval_dataset,
)

# Fine-tune the model
trainer.train()
```

These code examples provide a starting point for implementing RAG and fine-tuning in your generative AI systems.

# AI Support Ticket Classifier
An end-to-end NLP solution that utilizes a fine-tuned DistilBERT model to automatically categorize support tickets into 10 distinct departments.  
Built with a Flask backend and a lightweight frontend, the entire stack is hosted on Hugging Face Spaces.

[Live Demo on Hugging Face](https://huggingface.co/spaces/ch3thiya/ticket-classifier)

---

## Model & Training Overview
The core of this project is a fine-tuned distilbert-base-uncased model, chosen for its balance of speed and performance in resource-constrained environments.

- Dataset
  Trained on a stratified 35% subset (~10,000 records) of a 28k-row Kaggle dataset to optimize for CPU training time while maintaining class representation.
- Feature Engineering
  Utilized the [SEP] token to concatenate Subject and Body fields, providing the Transformer with full contextual awareness.
- Inference Guardrails
  Implemented a confidence threshold (0.45) in the Flask API.  
  If the model’s prediction score is too low, the ticket is flagged as "Uncertain" to prevent misclassification of out of distribution or gibberish text.

---

## Technical Stack

- ML Framework: PyTorch, Hugging Face Transformers  
- Backend: Flask (Python)  
- Frontend: HTML5, CSS3, Vanilla JavaScript  
- Deployment: Docker, Hugging Face Spaces

---

## Roadmap & Future Improvements
While this version serves as a functional prototype, the following updates are planned:

- Full Dataset Training 
  Scale training to 100% of the dataset (28k records) using GPU acceleration to improve accuracy and edge-case recognition.
- Model Quantization
  Convert model weights from FP32 → INT8 to reduce latency and memory footprint by up to 4x.
- LLM RAG Integration  
  Transition from a simple classifier to a Retrieval Augmented Generation (RAG) system that:
  1. Classifies the ticket  
  2. Retrieves a suggested solution from a database

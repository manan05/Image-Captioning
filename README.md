# Image-Captioning
Image Captioning - Final Project for CSE 5367 : Pattern Recognition
# 🖼️ Image Captioning with ViT-GPT2 on Flickr8K

This project explores image captioning using a pre-trained transformer-based model, [`nlpconnect/vit-gpt2-image-captioning`](https://huggingface.co/nlpconnect/vit-gpt2-image-captioning), which combines a Vision Transformer (ViT) encoder with a GPT2 decoder. The goal was to generate accurate and fluent captions for real-world images from the [Flickr8k dataset](https://github.com/jbrownlee/Datasets).

## 📌 Project Highlights

- **Zero-shot captioning** using a pre-trained model without fine-tuning
- Evaluated using BLEU (1–4) and METEOR scores
- Visualized caption quality through BLEU score distributions, word usage, and length analysis
- Sample predictions and reference captions side by side

## 🗂 Dataset: Flickr8k

- **8,000** real-world images (humans, animals, daily activities)
- **5 captions per image** written by humans
- Split:
  - Train: 6,000 images
  - Validation: 1,000 images
  - Test: 1,000 images

## 🧠 Model Used

- `nlpconnect/vit-gpt2-image-captioning` from Hugging Face
  - ViT extracts semantic visual features
  - GPT2 generates captions from encoded features
  - Beam search used during decoding (4 beams, length penalty 1.0)

## 🛠️ How It Works

1. **Setup**  
   Download and extract the Flickr8k dataset and caption files.

2. **Preprocessing**  
   Load images and prepare captions. Each image is mapped to its 5 human-written references.

3. **Caption Generation**  
   Use `generate_caption(path)` to:
   - Preprocess and encode the image
   - Generate a caption token sequence
   - Decode the sequence to text using GPT2 tokenizer

4. **Evaluation**  
   Metrics used:
   - **BLEU-1 to BLEU-4**
   - **METEOR**
   - Sentence-level BLEU-4 for image-wise analysis

5. **Visualizations**  
   - Histogram and boxplot of BLEU-4 scores
   - Caption length distribution
   - Top 20 most frequent predicted words
   - BLEU-4 vs caption length (scatter + regression)
   - Sample captions compared to references

## 📊 Results

| Metric   | Score   |
|----------|---------|
| BLEU-1   | 0.6119  |
| BLEU-2   | 0.4172  |
| BLEU-3   | 0.2693  |
| BLEU-4   | 0.1706  |
| METEOR   | 0.3670  |

- Captions are fluent and typically capture main objects/actions
- Model struggles with complex scenes or multiple entities
- Vocabulary usage is somewhat repetitive

## 🔍 Observations

- Shorter captions often yielded higher BLEU-4 scores
- Zero-shot inference works well for simple images
- Without fine-tuning, captions are accurate but lack descriptive richness

## 💡 Future Work

- Fine-tune on larger datasets (Flickr30k, MS-COCO)
- Use top-k or nucleus sampling for more diverse outputs
- Visualize attention to understand which image regions influence tokens
- Combine with CLIP for stronger multimodal understanding
- Incorporate human evaluation for fluency and relevance

## 📁 File Structure
📦Image-Captioning-ViT-GPT2
┣ 📂Flickr8k_Dataset/
┣ 📂Flickr8k_text/
┣ 📜main.ipynb (or .py)
┣ 📜README.md
┗ 📜requirements.txt (optional)


## 🧾 References

- Flickr8k Dataset: https://github.com/jbrownlee/Datasets
- Pretrained Model: https://huggingface.co/nlpconnect/vit-gpt2-image-captioning
- NLTK BLEU: https://www.nltk.org/

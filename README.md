# Tree-of-Life Family Classifier
Fine-grained rare species image classification with deep learning.

## Project at a glance
Classify photographs into **202 animal families** across **5 phyla** (Arthropoda, Chordata, Cnidaria, Mollusca, Echinodermata) using a per-phylum deep-learning pipeline built for the open **TreeOfLife-10M** dataset.

---

## Methodology
| Stage | What we did |
|-------|-------------|
| **Data curation** | • Removed 159 exact duplicates (perceptual hashing) • Auto-filtered 453 noisy images via RGB rules & **YOLOv8** (black/white backgrounds, humans, X-rays) • Optional **CLAHE** contrast boost and **U²-Net** background removal |
| **Augmentation** | Phylum-specific rotation, zoom, flips, translation, brightness/contrast to balance rare families |
| **Modelling** | Trained **one model per phylum** to cut imbalance and focus on phylum-level cues   1. **Scratch CNNs** (3–5 conv blocks)  2. **Transfer learning** – fine-tuned MobileNetV2, InceptionV3, EfficientNet-B0, ResNet-50, DenseNet-121 with Keras-Tuner HPO & early stopping |
| **Evaluation** | Accuracy + macro-F1 (imbalance-robust) and confusion matrices for error insight | 

---

## Results
| Approach | Accuracy | Macro-F1 |
|----------|----------|----------|
| Custom CNNs | 0.32 | 0.12 |
| **Transfer-learned CNNs** | **0.64** | **0.47** |

Transfer learning nearly **doubles accuracy and quadruples balanced F1**, with an InceptionV3 + CLAHE model topping the 166-class Chordata subset.  

---

## Key takeaways
* **Per-phylum transfer learning** is a simple yet powerful recipe for highly imbalanced, fine-grained wildlife datasets.  
* Rigorous **cleaning & targeted augmentation** matter as much as architecture choice.  
* **Chordata** remains the toughest challenge; richer data or stronger foreground cropping are logical next steps. 

---

> *Course project — MSc Deep Learning, NOVA IMS 2024-25*  
> **Authors:** Alexandra Pinto · Steven Carlson · Sven Goerdes · Tim Straub · Zofia Wojcik  

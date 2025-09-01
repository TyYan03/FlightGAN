# 🐦 FlightGAN - Animating Still Images Using GANs and CNNs  

## 📄 Research Paper

[![PDF Documentation](https://img.shields.io/badge/PDF-Final_Report-blue)](https://github.com/TyYan03/FlightGAN/releases/download/ResearchPaper/APS360_Final_Report.pdf)

## 📽️ Project Summary

We developed a deep learning pipeline that takes a single image of a bird and generates a short animation of it flying, using Generative Adversarial Networks (GANs) and Convolutional Neural Networks (CNNs). This project demonstrates a proof-of-concept for still image animation by predicting natural object motion from static scenes.

---

## 📌 Table of Contents

- [Motivation](#-motivation)
- [Dataset and Preprocessing](#-dataset-and-preprocessing)
- [Architecture Overview](#-architecture-overview)
- [Training Strategy](#-training-strategy)
- [Animation Pipeline](#-animation-pipeline)
- [Results](#-results)
- [Evaluation](#-evaluation)
- [Ethical Considerations](#-ethical-considerations)
- [Future Work](#-future-work)
- [Contributors](#-contributors)

---

## 💡 Motivation

Advancements in generative models have enabled automatic creation of realistic images and videos. Our goal was to explore this field by developing a pipeline that animates still images — specifically birds — using GANs trained on custom-collected data. This will act as a proof of concept for future applications like:

- Reviving memories or historical images  
- Bringing artwork to life  
- Enhancing visual storytelling

---

## 📂 Dataset and Preprocessing

- Collected **YouTube bird flight videos**
- Extracted frames and **filtered via YOLOv8** to isolate birds
- Augmented with the **CUB-200** bird dataset
- Final dataset: **18,000+ high-quality bird frames**
- Training/Test Split: 90/10

> Cleaned and cropped data ensures the model learns bird motion, not background noise.

---

## 🧠 Architecture Overview

### ✅ **Primary Model: Modified StyleGAN2-ADA**

- Used StyleGAN2 architecture as a base  
- Custom generator & discriminator with 7-layer blocks  
- Style mixing for animation generation

### 🧪 **Baseline Model: DCGAN**

- 5-layer ConvNet-based Generator and Discriminator  
- Used for initial performance benchmarking

---

## ⚙️ Training Strategy

- **Loss Function**: Standard min-max GAN loss  
- **Stabilization**: Adaptive Discriminator Augmentation (ADA)  
- **Training Time**: 160 epochs (~2 days on RTX 3060 Laptop GPU)  
- **Evaluation Metric**: Fréchet Inception Distance (FID)  
  - Initial: `149.24` → Final: `23.06`

---

## 🎞️ Animation Pipeline

1. Input single bird image  
2. Extract **style vector** from source  
3. Style-mix with target flight frames  
4. Interpolate between mixed styles  
5. Generate full flight animation (~300 frames)

> Output resembles smooth, believable bird motion.

---

## 📊 Results

### Quantitative

- **FID Score**: 23.06 (best trained model)  
- Outperformed baseline DCGAN

### Qualitative

- Photorealistic outputs on simple backgrounds  
- Style-mixed birds retained identity while changing pose  
- Model generalizes well to **new, unseen bird images**

### Final Output

![Bird Animation Demo](FlightGANResults/FinalOutput.gif)

---

## 🧪 Evaluation

- Tested on custom bird images (not in training set)  
- FID on test data: **25.88**  
- **85% realism rating** in peer evaluations 
- Animation retained bird's original shape and pose  
- Good performance on diverse environments & poses

---

## 🔒 Ethical Considerations

While our model targets bird animation, we recognize potential misuse:

- **Deepfakes**: Technology like this can be adapted for creating deceptive content involving real people, which has implications for misinformation and political manipulation.
- **Privacy**: If users input personal or unauthorized images, it may inadvertently violate privacy laws or ethical guidelines.

> We made conscious choices to avoid these concerns, including using public bird datasets and generating nature-based animations only.

---

## 🔭 Future Work

- Integrate **conditional GANs** for more control over animation attributes like angle, direction, and motion speed
- Incorporate **pose estimation** or **keypoint tracking** to improve realism
- Expand dataset to include **diverse species**, lighting conditions, and flight patterns
- Train with higher resolution data using distributed GPU clusters for improved realism and fidelity

---

## 👥 Contributors

| Name           | Email                          |
|----------------|--------------------------------|
| Tyler Yan      | ty.yan@mail.utoronto.ca        |
| Ammar Vora     | ammar.vora@mail.utoronto.ca    |
| Brett Yang     | bretteng.yang@mail.utoronto.ca |
| Shivansh Singh | shivansh.singh@mail.utoronto.ca|

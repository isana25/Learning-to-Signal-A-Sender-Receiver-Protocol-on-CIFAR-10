# 🔄 Sender–Receiver Image Ordering with Neural Networks

This project explores a simple yet powerful idea: can two neural networks **learn to communicate** using just a single bit of information?

In this setup, a **Sender** network observes two images and sends a one-bit message (0 or 1) to a **Receiver** network, which then tries to determine the original order of the images — even after they've been shuffled.

> 🧠 A communication protocol emerges from scratch between two agents trained end-to-end.

---

## 🔗 Run the Notebook on Colab

You can explore and run the full implementation directly in Google Colab:  
📎 **[Click here to open the notebook](https://colab.research.google.com/drive/1gx0YAiKesAtxL0bt6AelI2GYHbWU61mi?usp=sharing)**

> No setup needed — just open the link and run the cells! ⚡

---

## 📌 Project Highlights

- ✅ Trained a **Sender** and a **Receiver** model on random pairs of CIFAR-10 images
- 🔁 **Sender** learns to encode image order into a binary signal
- 🔄 **Receiver** uses that bit and a shuffled pair to guess the original order
- 🧪 Evaluated system performance by calculating Receiver error rate
- 📉 Visualized training loss for interpretability

---

## 🧠 Why This Matters

This task demonstrates:
- 🧠 **Emergent communication** between neural networks
- 👯 **Cooperative learning** in multi-agent settings
- 🧵 **Efficient signaling** using minimal data (just 1 bit!)

Such techniques are foundational for:
- Multi-agent systems and swarms
- AI game strategies and collaborations
- Robotics and edge AI with limited bandwidth

---

## 🧠 Model Architecture

### 🧑‍🚀 Sender
- Input: Two images (stacked vertically → 6 channels)
- Architecture:
  - 2 Convolutional layers (3×3) with ReLU
  - Adaptive Average Pooling
  - Fully connected layer → Sigmoid output (1-bit)
  
### 🧑‍💻 Receiver
- Input: Shuffled image pair + Sender’s bit
- Architecture:
  - Same CNN block as Sender
  - Concatenate image features with the 1-bit message
  - Fully connected layer → Sigmoid output (match or not)

Both models are trained **jointly** using Binary Cross-Entropy Loss, optimized with **Adam optimizer**.

---

## 🛠️ Tech Stack

- **Language:** Python
- **Framework:** PyTorch
- **Dataset:** CIFAR-10 (subset of 100 random images)
- **Visualization:** Matplotlib
- **Training Hardware:** GPU (optional, via Colab)

---

## 📊 Results

- The Sender and Receiver successfully learned to collaborate using only 1-bit messages.
- The Receiver’s error rate dropped significantly after training, proving that meaningful communication was learned.

| Metric              | Value    |
|---------------------|----------|
| Receiver Error Rate | ~X.X% ✅ |

*You can visualize the triplet comparison in the Colab notebook.*

---

## 🚀 How to Run

1. Clone this repo  
   ```bash
   git clone https://github.com/your-username/bittalk-neural-communication.git
   cd bittalk-neural-communication

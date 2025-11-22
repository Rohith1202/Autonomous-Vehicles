# 🚗 Autonomous Self-Driving Car using Udacity Simulator

## 📌 Project Overview

This project presents the development of an autonomous driving model using deep learning techniques, specifically Convolutional Neural Networks (CNNs), trained on driving behavior data collected from the **Udacity Self-Driving Car Simulator**. The objective is to predict steering angles from camera images in real time, enabling the vehicle to drive autonomously within the simulated environment.

The approach emphasizes:
- **End-to-end deep learning** for behavioral cloning.
- **Data augmentation** to increase robustness.
- **Efficient training pipeline** to minimize overfitting.
- **Real-time simulation testing** using the Udacity simulator.

---


## 🚀 Model Training Summary



### 📥 1) Data Loading & Preprocessing — Robust & Reproducible
The project follows the **Udacity-style** dataset with `driving_log.csv` and three camera streams:

- **Center / Left / Right** camera frames are loaded and paired with steering values.
- **Path Normalization:** `path_leaf()` ensures consistent filename handling across systems.
- **Steering Map:** every image is mapped to its steering measurement so the model learns direct image → action mappings.

---

### 📊 2) Data Balancing & Distribution Control — Smart & Effective
Driving data is heavily biased toward “straight” frames. We fix that with a statistically sound approach:

- Visualize steering distribution into **25 bins**.
- **Cap each bin at 400 samples** to avoid learning a “always-straight” policy.
- Shuffle and resample to keep training diverse.

**Impact:** Balanced training data improves turn detection, reduces bias, and produces safer steering behavior.

---

### 🎨 3) Data Augmentation Pipeline — Real-World Robustness
On-the-fly augmentation increases dataset variety without extra storage:

- **Horizontal Flip** — mirror images and invert steering (angle → `-angle`).
- **Brightness Variation** — HSV-based random brightness simulates day/night/shadows.
- **Camera Offset Correction** — left/right frames use steering offsets to teach recovery behavior.
- **Random Shifts (x/y)** — simulates lateral drift and camera jitter.
- **Crop & Normalize** — remove sky/hood and normalize pixels to `[-1, 1]` for stable training.
  <Figure size 1080x3600 with 20 Axes><img width="1067" height="3524" alt="image" src="https://github.com/user-attachments/assets/5baae6a4-f1bc-4705-b427-1509ed59717e" />

  <Figure size 1080x720 with 2 Axes><img width="1067" height="293" alt="image" src="https://github.com/user-attachments/assets/1d84bc59-347a-4515-81ab-dc1d64a0fbd4" />


**Why this is strong:** augmentation simulates realistic edge cases (glare, shadow, slight off-center) so the DNN generalizes to new roads.

---

### 🧠 4) Model Architecture — NVIDIA-Style CNN (DNN)
A compact, production-minded Deep Neural Network tuned for steering regression:

- **Preprocessing:** Cropping + normalization layers inside the model for portability.
- **Convolutional Backbone:** 5 Conv layers with ReLU to capture low→high level visual features (lanes, curbs, shadows).
- **Fully Connected Head:** Dense layers with dropout for robust decision-making.
- **Output:** Single linear neuron predicting the continuous steering angle.

**Design goal:** real-time-capable, small enough for deployment, powerful enough for complex road geometry.

---

### ⚙️ 5) Training Configuration — Stable & Reproducible
Training follows best-practice defaults and production controls:

| Component      | Setting |
|----------------|---------|
| Optimizer      | Adam |
| Loss           | Mean Squared Error (MSE) |
| Batch size     | 64 |
| Epochs         | 5–10 (adjust per validation curve) |
| Callbacks      | EarlyStopping, ModelCheckpoint |

**Generator-based training:** Augmentation is applied inside a generator for memory-efficiency and infinite variety.

---

### 📈 6) Training & Evaluation — Track, Visualize, Validate
- **Loss vs Epochs** charts to monitor convergence and detect overfitting.
- **Qualitative tests:** Overlay predicted steering on sample frames for visual sanity-checks.
- **Quantitative checks:** MSE on validation set and sample-driven error analysis.

---

### 🏁 7) Final Output — Production-Oriented Results
The trained model:

- Predicts steering angle from a single camera frame.
- Handles lighting variation, lane curvature, and small lateral drifts.
- Produces smooth, stable steering suitable for simulator deployment.


---

## 📁 Project Structure

```bash
├── Self_Driving_Car.ipynb       # Jupyter Notebook for training
├── model.h5                     # Trained Keras model
├── driving_log.csv              # Driving behavior log
├── IMG/                         # Folder with camera images
├── utils/                       # (Optional) For helper functions
└── README.md                    # Project documentation
```

---

## 🚀 Getting Started

### Prerequisites
- Python 3.7+
- TensorFlow / Keras
- OpenCV
- NumPy, Matplotlib, Pandas
- Udacity Self-Driving Car Simulator

```bash
pip install -r requirements.txt
```

### Running the Model
1. Launch the Udacity simulator.
2. Use the trained model (`model.h5`) with your inference script.
3. Drive autonomously using predicted steering angles.

---

## 📷 Images & Demo

![image](https://github.com/user-attachments/assets/0adc51dc-d56e-443f-a423-c394949fa588)


![image](https://github.com/user-attachments/assets/f66bccc1-5419-4921-9e41-961e7509c53c)


![image](https://github.com/user-attachments/assets/2d30b0b4-3f55-4f75-9641-a7b2b0e0bacc)

---
---

## 👨‍💻 About Me

Hi, I’m **Rohith Boppana** — a passionate and driven **final-year B.Tech student** in **Computer Science and Engineering** with a specialization in **Artificial Intelligence & Machine Learning**.

I'm deeply interested in building real-world tech solutions that combine data, intelligence, and intuitive design. My academic journey and hands-on projects reflect a strong foundation in both theory and practical application.

### 👇 My Core Interests
- 🤖 Artificial Intelligence & Machine Learning  
- 🔍 Data Science & Analytics   
- 📊 BI Dashboards & Predictive Modeling  
- 💡 Problem-Solving with Scalable Technologies

I enjoy translating business needs and data insights into impactful software solutions that solve real problems and enhance user experiences.

---

## 🔗 Let’s Connect

📫 **LinkedIn**  
Let’s connect and grow professionally:  
[linkedin.com/in/rohith-boppana-39ab57279](https://www.linkedin.com/in/rohith-boppana-39ab57279/)

🌐 **Portfolio**  
Explore my latest work, skills, and projects here:  
[rohith-boppana.vercel.app](https://rohith-boppana.vercel.app)

---


> 💡 _“Final-year student, forever learner — building the future, one project at a time.”_

Feel free to explore my repositories and reach out for **collaborations**, **internships**, or to discuss **innovative ideas**!

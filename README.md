# 🚗 Autonomous Self-Driving Car using Udacity Simulator

## 📌 Project Overview

This project presents the development of an autonomous driving model using deep learning techniques, specifically Convolutional Neural Networks (CNNs), trained on driving behavior data collected from the **Udacity Self-Driving Car Simulator**. The objective is to predict steering angles from camera images in real time, enabling the vehicle to drive autonomously within the simulated environment.

The approach emphasizes:
- **End-to-end deep learning** for behavioral cloning.
- **Data augmentation** to increase robustness.
- **Efficient training pipeline** to minimize overfitting.
- **Real-time simulation testing** using the Udacity simulator.

---

## 🛠️ Model Training Pipeline

### 1. 📥 Data Loading
- Reads driving log data from `driving_log.csv`.
- Utilizes images from **center**, **left**, and **right** cameras.
- Combines image paths and steering measurements.

### 2. 🎨 Data Augmentation
To improve model generalization, the following augmentations are applied:
- **Flipping** images horizontally and reversing the steering angle.
- **Brightness adjustment** to simulate varying lighting conditions.
- **Camera offset correction** for left/right images with adjusted steering angles.
- **Shuffling** and **balancing** data distribution.

### 3. 🧠 Model Architecture
A CNN model inspired by **NVIDIA’s end-to-end self-driving car architecture** was built using Keras:
- Input normalization and cropping layers.
- Multiple convolutional layers with ReLU activation.
- Fully connected layers with dropout regularization.
- Final output: single neuron predicting the **steering angle**.

### 4. ⚙️ Training Configuration
- Optimizer: `Adam`
- Loss Function: `Mean Squared Error (MSE)`
- Epochs: Configurable (default: 5–10 recommended)
- Batch Size: 64
- Early stopping and model checkpointing are implemented for stability.

### 5. 📊 Visualization
- Loss vs Epochs plot to observe convergence.
- Model testing results with optional prediction overlay visuals.

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

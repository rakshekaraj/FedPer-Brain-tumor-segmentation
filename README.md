# FedPer - Brain Tumor Segmentation

Federated learning framework for brain tumor segmentation to ensure patient privacy. This project utilizes the **lgg-MRI segmentation dataset** and a **ResNet model**. A Federated Learning pipeline is introduced to maintain patient privacy while achieving comparable accuracy to centralized learning.

---

## 📚 **Introduction**

Accurate brain tumor segmentation from MRI scans is essential for clinical decision-making, enabling detailed assessment and planning of treatments. However, datasets required for robust segmentation models are often distributed across institutions, making centralized data collection infeasible due to privacy concerns.

**Federated Learning** offers a solution by enabling institutions to collaboratively train models without centralizing data. However, challenges such as data heterogeneity across institutions persist. 

This project employs **FedPer** to address these challenges by personalizing models while sharing global knowledge. The project evaluates **FedPer** against traditional centralized learning to balance privacy with model performance.

---

## 📖 **Related Work**

- **Traditional Methods**: Deep learning models like UNet (Ronneberger et al., 2015) and Mask R-CNN have shown success in brain tumor segmentation but rely on centralized data.
- **Federated Learning**: Studies (e.g., Kairouz et al., 2021) highlight federated learning as a privacy-preserving alternative. However, handling non-IID data remains a challenge.
- **FedPer**: Proposed by Karimireddy et al. (2020), FedPer personalizes models by sharing global knowledge while retaining institution-specific expertise.

This project extends prior work by integrating **FedPer** with **3D brain tumor segmentation**, an area yet to be extensively explored.

---

## ⚙️ **Technical Approach**

### 1️⃣ **Data Preparation and Local Training**
- MRI scans from the **BraTS dataset** are preprocessed locally by each institution.
- Each client trains a **3D UNet model** for brain tumor segmentation with pixel-wise annotations.

### 2️⃣ **Federated Model Aggregation with FedPer**
- **Shared Encoder**: The encoder is shared across institutions to capture global knowledge.
- **Personalized Segmentation Heads**: Each institution maintains its own segmentation head to retain domain-specific knowledge.

### 3️⃣ **Global Model Updates**
- Shared encoder layers are aggregated on the server.
- Updated global models are broadcasted back to clients for local updates.

### 4️⃣ **Centralized Learning Baseline**
- A centralized model is trained using the aggregated dataset to evaluate performance against the federated approach.

### 5️⃣ **Evaluation and Optimization**
- Metrics: Models are evaluated using **Dice Coefficient** and **Intersection over Union (IoU)**.
- Optimization: Hyperparameter tuning ensures robust performance on non-IID data.

---

## 🗂️ **Dataset Description**

The **BraTS Dataset** (Menze et al., 2015):
- Contains 3D MRI scans with pixel-wise annotations for tumor regions:
  - Enhancing Tumors
  - Edema
  - Necrosis
- Includes diverse tumor types to ensure robust training.
- Preprocessed and distributed across multiple institutions for federated training.

---

## 🧪 **Results**
- **Federated Learning**:
  - Privacy-preserving with comparable performance to centralized learning.
- **Centralized Learning**:
  - Baseline for performance comparison.

**Key Metrics**:
- **Dice Coefficient**
- **IoU**

---

## 📈 **Conclusion**

This project demonstrates the potential of **FedPer** in addressing challenges of data heterogeneity in federated learning, enabling robust and privacy-preserving 3D brain tumor segmentation.

---

## 🛠️ **References**
1. Ronneberger, O., Fischer, P., & Brox, T. (2015). *UNet: Convolutional Networks for Biomedical Image Segmentation.*
2. Kairouz, P., McMahan, H. B., et al. (2021). *Advances and Open Problems in Federated Learning.*
3. Karimireddy, S. P., Kale, S., et al. (2020). *FedPer: Personalized Federated Learning.*

---

## 💡 **Acknowledgements**

Special thanks to:
- The creators of the **BraTS dataset**.
- Researchers advancing federated learning methodologies.

---

## 📩 **Contact**

For queries, feel free to reach out to:  
**Email**: rakshekaraj@gmail.com  
**GitHub**: https://github.com/rakshekaraj

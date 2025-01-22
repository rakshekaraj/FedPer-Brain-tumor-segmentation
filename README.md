# FedPer-Brain-tumor-segmentation

Federated learning framework in Brain tumor segmentation for more privacy. The model was trained on the lgg-MRI segmentation dataset and used a ResNet model. A Federated learning pipeline was introduced so that the patient’s privacy is maintained. It gave similar accuracy to that of Centralized Learning.

#Introduction
Accurate brain tumor segmentation from MRI scans is essential for clinical decision-making, enabling detailed assessment and planning of treatments. However, large-scale datasets required to train robust segmentation models are often stored across different institutions, making it difficult to build a centralized model without violating patient privacy. Traditional methods in medical image segmentation, such as UNet (Ronneberger et al., 2015), have achieved success in medical image analysis, yet these methods typically assume centralized data sources.
Federated learning offers a solution by allowing multiple institutions to collaboratively train models on their own data while keeping the data decentralized and private. Despite this, federated learning faces significant challenges due to data heterogeneity (Kairouz et al., 2021), where each institution’s dataset may differ in terms of imaging protocols, patient demographics, and other factors. To address this challenge, FedPer (Karimireddy et al., 2020) will be employed to personalize models for each institution. This project aims to evaluate federated learning with FedPer against a traditional centralized learning approach to assess the trade-offs between privacy and model performance.
Related Work
Previous studies have focused on brain tumor segmentation using deep learning techniques, particularly UNet and Mask R-CNN, for tasks like brain tumor detection and volumetric segmentation (Menze et al., 2015). However, most of these methods rely on centralized data, which is not feasible due to privacy and regulatory concerns in healthcare.
Federated learning has been increasingly applied in medical image analysis to train models without aggregating data. Kairouz et al. (2021) explored federated learning as a solution to preserve privacy across medical institutions. However, a key challenge of federated learning in medical contexts is handling non-IID data, where datasets across institutions may vary significantly (Li et al., 2020). FedPer (Karimireddy et al., 2020) was introduced to address this issue by enabling personalized models while benefiting from shared global knowledge.
This project extends previous work by incorporating FedPer in the context of 3D brain tumor segmentation, which has not been extensively explored in federated learning setups for medical image segmentation.
Technical Approach
This project will employ Federated Learning using the UNet architecture for 3D brain tumor segmentation, integrated with FedPer to address the challenges of non-heterogeneous data. The technical approach is outlined in the following steps:
 1. Data Preparation and Local Training:
● Each institution (client) will preprocess its own set of MRI scans from the BraTS dataset. The dataset includes various tumor types, such as enhancing tumors, edema, and necrosis, with pixel-wise annotations.
● The UNet model, adapted for 3D data, will be trained locally at each institution. This model is effective for medical image segmentation tasks, especially for volumetric data like MRI scans (Ronneberger et al., 2015).
2. Federated Model Aggregation with FedPer:
● FedPer will be used to personalize the model for each institution. The encoder layers of the model will be shared across institutions, while each institution will maintain personalized segmentation heads, enabling them to retain domain-specific knowledge while benefiting from shared global knowledge (Karimireddy et al., 2020).
● This strategy helps manage non-heterogeneous data by allowing each institution to retain specialized knowledge while collaborating with others, resulting in a more robust global model.
3. Global Model Updating and Broadcasting:
● After local training, the shared encoder layers will be aggregated on the server. The updated global model will then be broadcast back to each client, where they will update their personalized segmentation heads with the latest global model information.
4. Centralized Learning Approach:
● In parallel, a centralized learning model will be trained using the aggregated BraTS dataset, collected and processed centrally. This will provide a baseline for evaluating the federated learning approach and its privacy-preserving capabilities.
5. Evaluation and Optimization:
● Model performance will be evaluated using standard metrics such as Dice coefficient and Intersection over Union (IoU) for both federated and centralized learning models. Hyperparameters will be tuned to optimize the federated model’s performance while ensuring it handles the non-IID data effectively.
Dataset Description
The BraTS Dataset (Menze et al., 2015) contains 3D MRI scans of brain tumors, with detailed pixel-wise annotations for various tumor regions, including enhancing tumors,
edema, and necrosis. This dataset is widely used in medical image segmentation research and serves as an ideal candidate for federated learning.
The dataset contains a variety of brain tumor types, ensuring diversity for robust model training. Each MRI scan is accompanied by segmentation masks that provide precise tumor boundaries. The data will be preprocessed and used to train the federated learning model across multiple institutions.

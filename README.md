# Dermatology Image Classification Project

### Team Members
- [Jennifer Zheng](https://github.com/jennifer-z-1)<br>
  - Contribution(s): Project Management, Data Exploration/Preprocessing, Model Experimentation/Optimization, Evaluation/Validation, Technique Exploration (Data Augmentation, Transfer Learning, Ensemble Model, Sampling), GitHub Write Up (Project Highlights, Setup & Execution, Data Exploration, Model Development, Results & Findings, Impact Narrative, Next Steps & Future Improvements)
- [Johanna Johnsen](https://github.com/johannaj16)
  - Contribution(s): GitHub Write Up (Project Overview, Data Overview)
- [Aliona Heitz](https://github.com/alionaheitz)<br>
  - Contribution(s): GitHub Write Up (Project Overview, Data Overview)
- [Sukaina Zaidi](https://github.com/sukainazaidi)<br>
  - Contribution(s): GitHub Write Up (Project Overview, Data Overview)
- Olzhas Yessenbayev
  - Contribution(s): Teaching Assistant (TA)

--- 
### Project Highlights
- Exploration and fine tuning of 5 pre-trained models
- Experimentation of techniques for handling class imbalance and biases (data aug, transfer learning, weighted loss)
- Improvement of F1 score from 0.08 to 0.64

--- 
### Setup & Execution
1. Import Necessary Libraries
2. Load Data
3. Preprocess Data
4. Implement Model Architecture
5. Train the Model
6. Make Predictions on the Model
7. Evaluate Results

--- 
### Project Overview

As part of the Break Through Tech AI Studio Spring 2025 program, this challenge, hosted on Kaggle in collaboration with the Algorithmic Justice League (AJL), asks us to tackle a pressing issue in healthcare: the bias of dermatology AI tools against individuals with darker skin tones. Despite the rapid integration of AI in healthcare, many dermatological models have been trained on non-diverse datasets, leading to higher diagnostic error rates for people of color.

Our objective is to develop a machine learning model that can accurately classify 21 different skin conditions across a diverse range of skin tones. In doing so, we aim not just to improve overall model performance, but to build a solution that centers fairness, inclusivity, and real-world impact. Using fairness tools and non-skewed approaches, we will measure how our model performs across skin tones, ensuring that our approach does not maintain existing healthcare inequalities.

This work goes beyond the competition itself, it’s a step toward algorithmic justice. By collaborating with AJL and building on the research of institutions like UCLA and MIT Media Lab, our team is contributing to a growing movement to ensure AI serves everyone, not just the majority. We hope to create a more inclusive dermatology tool can lead to earlier and more accurate diagnoses for underserved communities, ultimately saving lives and advancing health equity.

--- 
### Data Overview
The data is a subset of the FitzPatrick17k dataset, a labeleled collection of ~17,000 images displaying a range of serious and cosmetic dermatological conditions with various skin tones scored on the FitzPatrick scale, 1 to 6. The subset is representive of the FitzPatrick17k dataset and consist of 4,500 images, representing 21 skin conditions. Images in the dataset are sourced from DermaAmin and Atlas Dermatologico, two reputable and widely used dermatology websites. 

Data Dictionary
| Column      | Data Type       | Description       |
|-----------------|-----------------|-----------------|
|md5hash |Object |An alphanumeric hash serving as a unique identifier; file name of an image without .jpg|
|fitzpatrick_scale	|int64 |Integer in the range [-1, 0) and [1, 6] indicating self-described FST|
|fitzpatrick_centaur	|int64 |Integer in the range [-1, 0) and [1, 6] indicating FST assigned by Centaur Labs, a medical data annotation firm|
|label	|Object	|String indicating medical diagnosis; the target for this competition|
|nine_partition_label	|Object |String indicating one of nine diagnostic categories|
|three_partition_label	|Object	|String indicating one of three diagnostic categories|
|qc	|Object |Quality control check by a Board-certified dermatologist.|
|ddi_scale	|int64 |A column used to reconcile this dataset with another dataset|

--- 
### Data Exploration
The data is preprocessed in accordance with the requirements of each respective pre-trained model. Common preprocessing steps include:
1. Image resizing, typically 224x224, 229x229, or 299x299 depending on model and data generator
2. Normalization to scale pixel values and facilitate faster convergence during training
3. Splitting train dataset into train (0.8) and validation (0.2) sets
4. Preprocess using function specific to each model imported using keras.applications

Skin Condition Distribution
![Skin Condition Distribution](https://github.com/user-attachments/assets/81d0ac5b-6c85-4853-adaa-a1d9d4ba78fa)
*Distribution of skin conditions is extremely imbalanced with majority conditions heavily outweighing less represented conditions.*

Fitzpatrick  Distribution
![Fitzpatrick  Distribution](https://github.com/user-attachments/assets/327855f4-9911-4e3b-899d-a3995aa2bcfa)
*Distribution of fitzpatrick scales is extremely imbalanced with lighter skin tones heavily outweighing darker skin tones.*

--- 
### Model Development
Considering the limited dataset, pre-trained models with less parameters and layers were selected to prevent overfitting, improve training stability, and better generalization. This includes:
- InceptionV3
- ResNet50
- Xception
- DenseNet201

Hyperparameters (e.g. batch size, learning rate, num of layers frozen) were also experimented with to optimize the performance of the model. Other techniques experimented with includes data augmentation, transfer learning, ensemble models, weighted loss, and sampling to increase the size and diversity of the dataset, enhance generalization, mitigate overfitting, and balance class distribution.

--- 
### Results & Key Findings
The model is expected to predict the skin condition based on the image for each md5hash and the results are evaluated using the F1 score which is the harmonic mean of the precision and recall. The formula for the base F1 score is: F1 = 2 * (precision * recall) / (precision + recall). 

The best to worst performing base models were found to be:
1. DenseNet201 (total params: ~20 million)
2. Xception (total params: ~23 million)
3. ResNet50 (total params: ~25 million)
4. InceptionV3 (total params: ~27 million)

The hyperparameter settings for best performance are:
- Batch Size: 16
- Learning Rate: 0.001
- Num of Layers Frozen: last 125

Of the other techniques experimented with, transfer learning and weighted loss contributed to improvements in the model while data augmentation, ensemble models, and over/under sampling did not significantly impact performance.

---
### Impact Narrative
This project's findings extend beyond dermatology image classification and can be implemented for all AI/ML models with limited data and/or extreme imbalance. Many of teams of engineers and researchers building and deploying AI model are not reflective of the society in which they create these technologies for. Because of that, data is often more representative of common occurances. In the case of this project, skin conditions that are more commonly seen and lighter skin tones have more data available, leading to lower accuracy for the later.

Improving model accuracy for those with rarer conditions or darker skin tone has ethical and societal impacts. As AI becomes more commonly used, the models need to be accurate and consistent to ensure patients with dark skin tones or less common conditions are not wrongly diagnosed and given incorrect or no treatment that could worsen their condition. Incorrect diagnoses can also lead patients to loss trust in medical institutions or professionals and open up room for legal, public relation, and/or financial risks. 

--- 
### Next Steps & Future Improvements
Initial experimentation has shown transfer learning and weighted loss entropy to significantly improve model performance, but further research, exploration, and implementation of data augmentation, ensemble models, and over/under sampling can be conducted further to improve model performance. This includes moderately augmenting moderately underrepresented conditions and skin tones using slight augmentation such as rotatation, zoom, flip, and fill while aggressively augmenting extremely underrepresented conditions and skin tones with more agrressive settings such as larger values for the same augmentations applied to moderate images and adding a brightness/channel shift range.

Ensemble (multiple) models can also be implemented to enhance generalization, increase robustness, and improve accuracy further by using multiple models to make predictions. Over and under sampling can help to adjust the imbalance od data but taking a balance subset of the original dataset. This can be combined with data augmentation techniques to generate a larger overall dataset and under or over sample from it to ensure the already limited dataset does not get smaller.

Lastly, other pre-trained models can be experimented as the above techniques are implemented to increase the amount of data available for training. This is because DenseNet, though performing well on the dataset as a base model, has ~20 million in total params which is suitable for limited data but may perform less well as the dataset increases.

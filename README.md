# Dermatology Image Classification Project

### Team Members
- [Jennifer Zheng](https://github.com/jennifer-z-1)<br>
  - Contribution(s): Project Management, Data Exploration/Preprocessing, Model Experimentation/Optimization, Evaluation/Validation, Technique Exploration (Data Augmentation, Transfer Learning, Ensemble Model, Sampling), GitHub Write Up (Project Highlights, Setup & Execution, Data Exploration, Model Development, Results & Findings, Impact Narrative, Next Steps & Future Improvements)
- [Johanna Johnsen](https://github.com/johannaj16)
  - Contribution(s): GitHub Write Up (Project Overview, Data Exploration)
- [Aliona Heitz](https://github.com/alionaheitz)<br>
  - Contribution(s): GitHub Write Up (Project Overview, Data Exploration)
- [Sukaina Zaidi](https://github.com/sukainazaidi)<br>
  - Contribution(s): GitHub Write Up (Project Overview, Data Exploration)
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
1. Image resizing, typically 128x128, 224x224, or 229x229 depending on model and data generator
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


--- 
### Results & Key Findings


--- 
### Impact Narrative


--- 
### Next Steps & Future Improvements

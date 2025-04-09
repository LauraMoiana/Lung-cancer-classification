# Lung-cancer-classification

University project for the course "AI in Biomedicine", Polytecnic of Milan

## Introduction
Lung cancer (LC) is the primary cause of cancerrelated mortality worldwide and the second most frequently diagnosed cancer globally. Due to the lack of early symptoms, patients often miss the optimal treatment window, making early screening crucial for the prevention and management of lung cancer. The 10-year relative survival rate can reach up to 88% if treatment is administered in time. Pulmonary nodules are clinically relevant as they may represent the initial manifestation of lung cancer.
Visual analysis of medical images is an efficient method to investigate lung tissue, identify nodules, and classify the stages of lung
cancer. Various imaging techniques are employed for lung cancer screening, including positron emission tomography (PET), computed tomography (CT), ultrasound, chest radiography (X-ray), and magnetic resonance imaging(MRI). 
However, identifying malignant cells can be challenging due to variations in scan intensity and anatomical structure, often leading to
potential misinterpretations by medical professionals. The variability and unpredictability of pulmonary nodules further complicate accurate detection and diagnosis.
Machine learning (ML) and deep learning (DL) methods have shown great potential in supporting radiologists and clinicians by enhancing
nodule detection, classification and segmentation. These AI-driven systems hold the potential to improve cancer diagnosis and prognosis, reduce misclassifications, lower error rates, and provide high-quality imaging analysis.

## Data
The dataset consists of 2,363 pairs of images in NRRD (Nearly Raw Raster Data) format, where each pair includes:
- full-slice image (2D CT scan slice showing the largest visible nodule. res=512x512)
- zoomed-in/nodule image (focused view of the nodule. res=variable (from 45x44 to 108x124)
Each pair is annotated with malignancy score label [1-5] indicating the severity of the tumor.

## Goal
For both image type (full slice, nodule) perform:
- 5-class malignancy classification
- Binary classification (1,2,3 - benign; 3-4 malignant)
Compare their performance

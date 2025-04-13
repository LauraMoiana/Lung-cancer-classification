# Lung cancer classification (CT scan)

University project for the course "AI in Biomedicine", Polytecnic of Milan.

The work is well described in the "Final report" file. Refer to it for a clearly understanding.

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

## Method
preprocessing:
1) resize nodule image to a fixed size
2) cleanLab for data cleaning
3) train-val split
4) clipping of HU pixel values
5) Clahe and denoising
6) Pixel normalization
7) Augmentation

## Experiments
### full slice
Different network have been trained, starting from the basic CNN as baseline. The best results have been optained performing TL on Resnet50 pretrained on RadImagenet.

### Nodule 
Different network have been trained, starting from the basic CNN as baseline. Radiomic features have been estracted from the nodule images (even without segmentation masks) and provide promising results. The best results have been obtained combaining both radiomic features and image analysis into a unique deeo learning network with 2 different input paths.

## Results
results are clearly described into the Final report.
The Accuracy of the best model for each image-type and classification-type are shown in the following table:
|             | binary    | 5 classes |
|-------------|-----------|-----------|
| full_slice  | 83.99 %   | 50.00 %   |
| nodule      | 89.47 %   | 61.84 %   |


## Conclusion
This study explored the performance of deep learning models in classifying two types of lung CT images: full_slice images and nodule focused images. The results showed that models trained on nodule images outperformed those trained on full_slice images, likely due the fact that nodule images focus directly on the region of interest. 
Limitations: The small and imbalanced dataset limited the robustness of the models, and the lack of segmentation made the models
struggling to localize nodules. Future works could focus on addressing these limitations by using larger, more balanced datasets and incorporating segmentation data. 

Overall, this study highlights the complexities of working with medical images in deep learning, underlying the importance of domain-specific techniques and the need for well-focused images that contains the task-relevant features without unnecessary details that may confuse the model.


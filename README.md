# SkinCancerAI

## Overview

This project focuses on the processing, segmentation, and classification of skin lesion images using advanced deep learning techniques to address the challenge of melanoma diagnosis. Melanoma is a type of skin cancer with a high cure rate if diagnosed early. The diagnosis begins with the inspection of lesions that have visual characteristics distinguishing them from benign entities like nevi (common moles).

## Project Structure

### Data
The project utilizes the ISIC 2017 dataset, which includes 2750 dermatoscopic images categorized into melanoma, seborrheic keratosis, and benign nevus. The dataset is divided into training, validation, and test sets.

### Methods

#### Pre-processing
Images are resized to 192x256 while maintaining a 3:4 aspect ratio and normalized to the [0, 1] range.

#### Segmentation
- **Model**: Convolutional Encoder-Decoder Network inspired by Yuan and Lo (2017).
- **Architecture**: The network includes convolutional, pooling, deconvolutional, and upsampling layers, totaling 291,145 parameters.
- **Training**: Batch size of 16, learning rate of 0.001, and Adam optimizer. Jaccard distance-based loss function.

#### Post-processing
- Thresholding and morphological operations are applied to refine the segmented areas.

#### Classification
- **Custom Model**: A convolutional neural network with data augmentation, batch normalization, dropout, and a final softmax activation layer.
- **Transfer Learning**: MobileNetV2 with additional layers for the specific task.
- **Balancing Techniques**: Class weighting, undersampling, and oversampling to handle class imbalance.

### Results

#### Segmentation
- Accuracy: 0.89
- Sensitivity: 0.66
- Specificity: 0.96
- Dice Coefficient: 0.73
- Jaccard Index: 0.58

#### Classification
- Custom model with class weighting showed the best balance between precision (0.44) and sensitivity (0.47).
- Transfer learning models, particularly MobileNetV2, were less effective due to biases towards the majority class.

### Conclusion
The project demonstrates the potential of deep learning in medical diagnosis, particularly for melanoma detection. Future work should explore newer architectures and more balanced datasets to enhance performance.

## Usage

### Prerequisites
- Python 3.6+
- TensorFlow
- OpenCV
- NumPy
- Matplotlib

### Installation
Clone the repository and install the required packages:
```sh
git clone https://github.com/username/SkinLesionDeepLearning.git
```
### References
- Hartman, R. I., & Lin, J. Y. (2019). Cutaneous melanoma—A review in detection, staging, and management. Hematology/Oncology Clinics of North America, 33(1), 25–38.
- Duarte AF, et al. Clinical ABCDE rule for early melanoma detection. Eur J Dermatol. 2021.
- Viknesh CK, et al. Detection and Classification of Melanoma Skin Cancer Using Image Processing Technique. Diagnostics (Basel). 2023.
- Codella, N. C. F., et al. "Skin lesion analysis toward melanoma detection: A challenge at the 2017 international symposium on biomedical imaging (isbi), hosted by the international skin imaging collaboration (isic)." IEEE, 2018.
- Yuan, Y., & Lo, Y. C. "Improving dermoscopic image segmentation with enhanced convolutional-deconvolutional networks." IEEE journal of biomedical and health informatics, 2017.
- Sandler, M., et al. "Mobilenetv2: Inverted residuals and linear bottlenecks." IEEE conference on computer vision and pattern recognition, 2018.

For more detailed information, please refer to the full report included in the repository.

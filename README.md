# Aerial-Imagery-Semantic-Segmentation

## Dataset URL
https://www.kaggle.com/datasets/humansintheloop/semantic-segmentation-of-aerial-imagery

## Problem Statement
Semantic segmentation of the aerial imagery

## About Data
The dataset consists of aerial imagery of Dubai obtained by MBRSC satellites and annotated with pixel-wise semantic segmentation in 6 classes. The total volume of the dataset is 72 images grouped into 6 larger tiles. The classes are:

- Building: #3C1098
- Land (unpaved area): #8429F6
- Road: #6EC1E4
- Vegetation: #FEDD3A
- Water: #E2A929
- Unlabeled: #9B9B9B

## Analysis
1. The analysis has been done on `Google Colab Environment`
    - Model training has been done on the notebook `UNet_Arial_Model_Train.ipynb`
    - Model inferencing has been done on the notebook `UNet_Arial_Model_Inferencing.ipynb`
    


2. Since the size of images are very large, we divided the images into 256x256 patches. For example, if the size of an image is 1024x768, then the image will be divided into 12 patches of size 256x256.


3. Converted the given hex color codes to RGB colors


4. Encoded the RGB colors of each pixel in the masks to integer labels. After that converted them into one-hot encoded labeled masks.


5. Train Test Split
    - Train size: 80%
    - Test size: 20%
    
    
6. Install the library `segmentation-models` for different loss functions and performance metrics for semantic segmentation


7. Loss: Dice Loss + Focal Loss
    
    Metric: Accuarcy & IOU Score


8. Initialize the U-Net Model. The model architecture is shown below:
![alt text](https://github.com/Suvam-Bit/Aerial-Imagery-Semantic-Segmentation/blob/main/UNet_Architecture.png?raw=true)


9. Model Training
    - Optimizer: Adam
    - Loss: Dice Loss + Focal Loss
    - Metrics: Accuarcy, IOU Score
    - Epochs: 100
    - Batch size: 8
    
    
10. Evaluation
    - Accuracy: 80.34%
    - Mean IOU Score: 0.5433
    
    
11. Inferencing
    - Model inferencing has been done in two ways. First we divide an input image in smaller patches of size 256x256. Next we predict the mask for each patch. Finally we combine the predicted masks
        - without smooth blending
        - with smooth blending
        
    - NOTE: The smooth blending has been done with the help of `smooth_tiled_predictions.py` which is collected from the GitHub Repository: https://github.com/Vooban/Smoothly-Blend-Image-Patches. The bugs in the code has been fixed by Sreenivas B. His GitHub Repository: https://github.com/bnsreenu/python_for_microscopists/blob/master/229_smooth_predictions_by_blending_patches/smooth_tiled_predictions.py

## Result:
![alt text](https://github.com/Suvam-Bit/Aerial-Imagery-Semantic-Segmentation/blob/main/sample_image_outputs/output_03.jpg?raw=true)

# AI for Damage Detection Challenge

Using object detection models to detect damages in bridges. Detecting defects on a bridge surface to aid in more effective and efficient bridge inspections.  

This challenge was organized by FruitPunch AI and was developed by 2 teams of data scientists and engineers during 10 weeks. 


### Methods

1. Binary Multi-label classification and Learning Curve Analysis
   - Useful for detecting multiple instances of defects within a single image
   - Useful to provide an estimate of how many training samples are needed to have a robust model
   
   
2. Object Detection
   - Useful to get the locations of the detected defect instances within the given image
   
   
3. Multi-class Single-label classification
   - Useful for inferring the defect label of a cropped image showing a single defect

### Dataset and Training setup details

#### Binary Multi-label classification and Learning Curve Analysis

1. Dataset: 
   - CODEBRIM, 5 binary labels per image
   - Minimal transformations applied (resize, random crop, normalization)
2. Model: 
   - Pretrained Vision Transformer, 384 px input size
   
3. Train/validation/test splits:
   - Multilabel stratified splits applied for all splits generation to handle class imbalance
   -Test set: 152 samples were held-out to evaluate all models
   - 5 models trained: 
      - Training set sizes: 100, 200, 300, 400, 900
      - 20% of each training set was held-out for validation, i.e. the model trained with 100 samples was actually trained with 80 samples and validated on 20 samples
4. Models were finetuned for 20 epochs, but best checkpoint was saved based on validation F1 score.

#### Object Detection
1. Dataset: 
   - CODEBRIM + RWS, 3 classes (ASR, Scheur, Betonrot)
3. Model: 
   - Pretrained YOLO-small checkpoint with DETR model (Image resized to min size of 800 & max size of 1333)
   - 30.7 million training parameters
 
4. Train/validation/test splits:
   - 1200 samples (62%) used for training and 466 samples (24%) used for validation
   - Test set: 260 samples (14%) were held-out to evaluate the models
5. Models were finetuned for 10 epochs






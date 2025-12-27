# Potato Disease Classification Using Deep Learning

## Overview

I built a deep learning model that can identify diseases in potato plants just by looking at pictures of their leaves. The model uses CNNs to classify leaves into three categories: healthy, early blight, or late blight. This could help farmers catch diseases early before they spread across entire crops.

## Why This Project?

Potato crops face serious threats from diseases like Early Blight and Late Blight, which can destroy entire harvests if not caught early. Currently, farmers either need to manually inspect plants (which takes forever and requires expertise) or wait until damage is visible. I wanted to create something that could:

- Give instant results from a simple leaf photo
- Work at scale without needing an expert for every plant
- Catch problems early when they're still manageable
- Be accessible enough that anyone could use it

## How It Works

### The Model

I designed a CNN with 6 convolutional layers that gradually learn to recognize disease patterns. Here's the basic structure:

- Takes 256x256 pixel color images as input
- 6 Conv2D layers starting with 32 filters and expanding to 64
- MaxPooling after each convolution to reduce dimensions
- Flattens everything into a dense layer before final classification
- Outputs probabilities for all 3 classes using softmax

The architecture balances being deep enough to learn complex patterns while staying computationally efficient.

### Data Preparation

I split the dataset 80/10/10 for training, validation, and testing. To make the model more robust, I added several preprocessing steps:

- Normalized all pixel values to 0-1 range (helps the model learn faster)
- Applied data augmentation: random flips, rotations, zooms, and contrast changes
- This prevents overfitting since the model sees slightly different versions each time
- Used TensorFlow's caching and prefetching to speed up training

### Training Process

Trained the model for 35 epochs using:
- Adam optimizer (it's adaptive and works well for most cases)
- Sparse categorical crossentropy loss
- Batch size of 32

I kept an eye on both training and validation metrics throughout to make sure the model was actually learning and not just memorizing.

### Hyperparameter Tuning

Instead of guessing, I used Keras Tuner to automatically test different configurations:
- Tried different kernel sizes (3x3 vs 5x5)
- Tested various filter counts (32, 64, 128)
- Experimented with dropout rates
- Adjusted dense layer sizes

This saved a lot of time compared to manual tuning and helped find the best setup.

## What Makes This Useful

**Smart Image Handling**: The model automatically resizes images, so it doesn't matter what size photo someone uploads. All the preprocessing is baked into the model itself.

**Confidence Scores**: Instead of just saying "this is diseased," it shows how confident it is in the prediction. This helps users know when to double-check.

**Version Controlled**: I set up automatic versioning for saved models, making it easy to track improvements and roll back if needed.

**Deployment Ready**: Everything's saved in Keras format, so it can be deployed to a web app or mobile app pretty easily.

## Disease Categories

The model recognizes three classes:

1. **Healthy** - Plant is doing fine, no intervention needed
2. **Early Blight** - Caused by a fungus (Alternaria solani), creates dark spots
3. **Late Blight** - More serious, caused by an oomycete (Phytophthora infestans)

## Results

The model trained successfully and shows good generalization between training and validation sets. The accuracy and loss curves indicate it's learning real patterns, not just memorizing the training data. Every prediction comes with a confidence percentage, which adds transparency.

## Technology Stack

**Deep Learning Framework**: TensorFlow 2.x, Keras  
**Data Processing**: NumPy, Python Image Libraries  
**Visualization**: Matplotlib  
**Hyperparameter Tuning**: Keras Tuner  
**Development Environment**: Python 3.x, Jupyter Notebooks  

## Project Structure

``` Stack

- **TensorFlow & Keras** for building and training the model
- **NumPy** for data manipulation
- **Matplotlib** for visualizing results
- **Keras Tuner** for hyperparameter optimization
- **Python 3** & Jupyter Notebooks for development

## Project Files

```
├── Potato_Disease_Data_Preprocessing.ipynb    # Data loading and prep work
├── Potato_Disease_Model_Building.ipynb        # Model creation and training
├── potato_disease_model_building.py           # Standalone Python script
├── README.md                                   # This file
└── LICENSE
```

I organized the code into separate notebooks to keep things clean - one for data prep and one for model building. There's also a standalone Python script version for easier deployment.

## What I'd Add Next

If I continue developing this:

- Build a REST API (probably with FastAPI) so it's easy to use
- Create a simple mobile app farmers could actually use in the field
- Add more disease types to make it more comprehensive
- Try transfer learning with models like ResNet or EfficientNet
- Add Grad-CAM visualizations to show which parts of the leaf the model is focusing on
- Set up a dashboard for tracking predictions over time

## What I Learned

This project gave me hands-on experience with:
- Designing CNN architectures from scratch
- Working with image data and augmentation techniques
- Hyperparameter tuning and model optimization
- Thinking about real-world deployment challenges
- Writing clean, modular code that others can understand
- The importance of validation metrics to avoid overfitting
```

### Running the Project
1. Clone the repository
2. Running the Code

You'll need Python 3.7+ and these libraries:
```bash
tensorflow >= 2.0
keras-tuner
matplotlib
numpy
```

To run it:
1. Clone this repo
2. Install dependencies (ideally in a virtual environment)
3. Open the notebooks in order - preprocessing first, then model building
4. Or just run the Python script directly if you prefer

## License

See the LICENSE file for details.

---

*A computer vision project applying deep learning to agricultural challenges*
# 🥔 Potato Disease Classification using CNN
This project uses Convolutional Neural Networks (CNN) to detect and classify diseases in potato plant leaves from images. It is structured into clear, modular sections to ensure clean, understandable code and easy experimentation.
and use Convolutional Neural Network (CNN) to classify potato leaves into 3 categories:
1. Healthy
2. Early Blight
3. Late Blight

🧱 Project Structure

## 1.Preprocessing : - 

### Located in  ===> Potato_Disease_Data_Preprocessing.ipynb ===> https://github.com/PrashantTakale369/Potato-Disease-Classification-Using-CNN-/blob/d59df8e31dbde90dbdf98e56eaa5caf8120eacd7/Potato_Disease_Data_Preprocessing.ipynb
<p> 1.Loads the dataset from local or TFDS.</p> 
<p> 2.Applies image normalization.</p>
<p> 3.Visualizes random samples.</p>
<p> 4.Organizes and prepares the data using:</p>


##  Potato Leaf Disease Classification with CNN : 

==> 1. Model Architecture : - 

- Multiple `Conv2D` + `MaxPooling2D` layers
- `Flatten` → `Dense` layers
- Final layer with `Softmax` for 3-class classification

===> 2. Hyperparameter Tuning :- 

Used Keras Tuner with RandomSearch to optimize:
<p> 1.Kernel size.</p> 
<p> 2.Number of filters.</p>
<p> 3.Dropout rate</p>
<p> 4.Dense layer units:</p>

===> 3. Model Training :- 

- Optimizer: `Adam`
- Loss Function: `SparseCategoricalCrossentropy`
- Epochs: `35`
- Metrics Tracked: `accuracy`, `val_accuracy`, `loss`, `val_loss`

Visualized using `matplotlib`:
- Training vs Validation Accuracy
- Training vs Validation Loss

# 🙌 Acknowledgements
1. TensorFlow Datasets & Keras Team
2. Dataset Source: [Kaggle / PlantVillage]
3. Google Colab GPU support

# Future Improvements
1. Add more plant species or diseases
2. Use transfer learning with pretrained models (e.g., MobileNet, ResNet)
3. Convert model to TensorFlow Lite for mobile apps
4. Deploy via Streamlit / FastAPI for live usage
  

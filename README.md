🔢 **Handwritten Digit Recognition using KNN & PCA**

A Machine Learning Project for Classifying Images of Digits (0–9)

<p align="center"> <img src="https://img.shields.io/badge/Machine%20Learning-KNN-blue?style=for-the-badge" /> <img src="https://img.shields.io/badge/Dimensionality%20Reduction-PCA-orange?style=for-the-badge" /> <img src="https://img.shields.io/badge/Dataset-MNIST-yellow?style=for-the-badge" /> <img src="https://img.shields.io/badge/Python-3.10+-green?style=for-the-badge" /> </p>

**🌟 Project Overview**
This project demonstrates how to classify handwritten digits (0–9) using Machine Learning techniques.
Instead of deep learning, this model uses:

    👁 Raw pixel intensities
    
    🤖 K-Nearest Neighbors (KNN) Classifier
    
    ✂️ PCA Dimensionality Reduction
    
    📊 2D and 3D Visualizations using Plotly

It is a great example of how classical ML methods can still achieve high accuracy on image datasets like MNIST.

**📁 Project Structure**

    Handwritten-Digit-Recognition/
    │── HandwrittenImage.csv                 
    │── MNIST_KNN_PCA.ipynb                  
    │── README.md

🧠 **Dataset Summary**

    Dataset contains 28 × 28 pixel handwritten images
    
    Each image is flattened into 784 features
    
    Column 0 → label (digit 0–9)
    
    Column 1–784 → pixel intensities
    

Example row shape:
    
    [label, pixel1, pixel2, ..., pixel784]

👁 **Visualizing a Digit**

From notebook:

    plt.imshow(df.iloc[104,1:].values.reshape(28, 28))


Which produces:

    A clear handwritten "2" image

⚙️** Machine Learning Pipeline**

    1️⃣ Data Splitting
    x = df.iloc[:, 1:]
    y = df.iloc[:, 0]
    train_test_split(..., test_size=0.2)

Training samples: 33,600
Test samples: 8,400

🤖 2️⃣ **Model Training (KNN Classifier)**

    knn = KNeighborsClassifier()
    knn.fit(x_train, y_train)

⏱ **Prediction Time:**

    ~ 11.36 seconds

**📈 Accuracy:**

    0.964889 (≈ 96.49%)

➡ Excellent accuracy without deep learning!

**✂️ 3️⃣ PCA for Dimensionality Reduction**

Before applying PCA:

    Feature size = 784

**PCA → 200 Components**

    pca = PCA(n_components=200)


**Results:**

    Accuracy improved slightly → 0.957
    
    Training becomes much faster

Plotly visualizations become possible


**🔬 4️⃣ PCA → 2 Components (Visualization)**

    pca = PCA(n_components=2)

    Created a 2D Scatter Plot:
    
    Each point is a digit
    
    Colors represent digit class
    
    Shows natural clustering in pixel space

**🧊 5️⃣ PCA → 3 Components (3D Visualization)**

Using Plotly:

fig = px.scatter_3d(...)
fig.show()


✨ Amazing 3D clusters appear for each digit.

**📊 Explained Variance Analysis**

    Using PCA eigenvalues and cumulative variance:
    
    plt.plot(np.cumsum(pca.explained_variance_ratio_))


**Insights:**

    First 100 components capture ~90% variance
    
    First 200 components capture ~95% variance
    
    All 784 components capture 100% variance

Shows how redundant pixel information is in MNIST.

**🏆 Final Model Performance**

    Method	Accuracy	Notes
    KNN (784 features)	⭐ 96.49%	High accuracy, slower
    KNN + PCA (200 components)	95.7%	Much faster, compact
    PCA 2D Visualization	—	Clusters visible
    PCA 3D Visualization	—	Clear separation

**🛠 Tech Stack**

    Technology	Purpose
    Python	Main Language
    Pandas	Data handling
    NumPy	Numerical operations
    Matplotlib	Image visualization
    Scikit-Learn	KNN & PCA
    Plotly	3D visualization


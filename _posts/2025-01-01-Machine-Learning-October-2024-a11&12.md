---
layout: post
title: UoE - Machine Learning October 2024 A - CNN Model Activity & CNN Tutorial
subtitle: Understand the applicability and challenges associated with different datasets for the use of machine learning algorithms.
categories: EL-Activities
tags: [UoE, coding, Module E-Portfolio Learning Activities]
---
---
## Convolutional Neural Networks (CNN) - Object Recognition
---

### Imports
    
    from numpy.random import seed
    seed(888)

    #from tensorflow import set_random_seed
    #set_random_seed(4112)
        import tensorflow
        tensorflow.random.set_seed(112)
        import os
        import numpy as np
        import itertools
        import tensorflow as tf
        import keras
        from keras.datasets import cifar10 # importing the dataset
        from keras.models import Sequential       #to define model/ layers
        from keras.layers import Dense, Conv2D, MaxPool2D, Flatten
        from sklearn.metrics import confusion_matrix

    # To Explore the images
        from IPython.display import display
        from keras.preprocessing.image import array_to_img
        from tensorflow.keras.utils import to_categorical
        import matplotlib.pyplot as plt
        %matplotlib inline

        import pandas as pd

### Get the Dataset
CIFAR-10  is an established computer-vision dataset used for object recognition. It is a subset of the 80 million tiny images dataset and consists of 60,000 32x32 color images containing one of 10 object classes, with 6000 images per class. It was collected by Alex Krizhevsky, Vinod Nair, and Geoffrey Hinton.
The dataset is popularly used to train image classification models

    # Getting the dataset as a Tuple
        (x_train_all, y_train_all), (x_test, y_test) = cifar10.load_data()
  
    # UPLOAD NEW IMAGE
        import numpy as np
        import tensorflow as tf
        from tensorflow.keras.datasets import cifar10
        from tensorflow.keras.utils import to_categorical
        from tensorflow.keras.models import load_model
        import matplotlib.pyplot as plt
        from PIL import Image
        import os

    # Upload your own image
        def upload_and_preprocess_image(image_path):
  
    # Load the image
        img = Image.open(image_path)
        img = img.resize((32, 32))  # Resize to 32x32 as required by CIFAR-10
        img_array = np.array(img) / 255.0  # Normalize values between 0 and 1

    # Check if the image is grayscale, and convert to RGB if necessary
        if img_array.shape[-1] != 3:
            img_array = np.stack((img_array,) * 3, axis=-1)

    # Reshape for the model
        img_array = np.expand_dims(img_array, axis=0)
        return img_array

    # Replace this with the path to your uploaded image
        your_image_path = "/content/wildlife-id-Whitetail-Deer.jpg"

    # Preprocess the image
        input_image = upload_and_preprocess_image(your_image_path)

    # Show the image for confirmation
        plt.imshow(input_image[0])
        plt.title("Uploaded Image")
        plt.axis("off")
        plt.show()

    # UPLOAD NEW IMAGE
    # Load CIFAR-10 dataset
         (x_train_all, y_train_all), (x_test, y_test) = cifar10.load_data()

    # Assign a label for the new image (e.g., 'tiger' is not in CIFAR-10, but let's assume it's similar to 'cat' -> label = 3)
         new_label = 4 # Assuming the label is 3 for 'cat'

    # Add the new image to x_train_all and the label to y_train_all
         x_train_all = np.concatenate((x_train_all, input_image), axis=0)
         y_train_all = np.concatenate((y_train_all, np.array([[new_label]])), axis=0)

    # Check new dataset shape
         print(f"x_train_all shape: {x_train_all.shape}")
         print(f"y_train_all shape: {y_train_all.shape}")

### Constants
 
         LABEL_NAMES = ['airplane', 'automobile','bird','cat', 'deer', 'dog', 'frog', 'horse', 'ship', 'truck','tiger']

### Exploring the Data
    
    # To use the ipython display to view an image
         pic = array_to_img(x_train_all[0])
         display(pic)
         plt.imshow(x_train_all[0])
    # To check the label
        y_train_all.shape
    # Note that in the image above the index 1 corresponds to "Automobile"
    # we have a 2 dimension numpy array; that is why we also include " [0] "
        y_train_all[0][0]
    # Using the lable names to get the actual names of classes
        LABEL_NAMES[y_train_all[0][0]]
        x_train_all.shape
        number_of_images, x, y, c = x_train_all.shape
        print(f'Number of images = {number_of_images} \t| width = {x} \t| height = {y} \t| channels = {c}')
        x_test.shape

### Preprocess Data

        x_train_all =x_train_all / 255.0
        x_test =  x_test / 255.0
        y_test
    # 10 >>> simply means we have 10 classes like we already know (creating the encoding for 10 classes)
        y_cat_train_all = to_categorical(y_train_all,10)
    # 10 >>> simply means we have 10 classes like we already know (creating the encoding for 10 classes)
        y_cat_test = to_categorical(y_test,10)
        y_cat_train_all

### Creating the Validation dataset
For small data we usually go with:
    * 60% for Training
    * 20% Validation
    * 20% Testing
Only the final selected model gets to see the testing data. This helps us to ensure that we have close to real data in real-world when the model is deployed. Only our best model gets to see our testing dataset. Because it will give us a realistic impression of how our model will do in the real world
However, if the dataset is enormous.:
    * 1% for is used for validation
    * 1% for is used for testing

        ALIDATION_SIZE = 10000
    # VALIDATION_SIZE = 10,000 as defined above
        x_val = x_train_all[:VALIDATION_SIZE]
        y_val_cat = y_cat_train_all[:VALIDATION_SIZE]
        x_val.shape
        y_val_cat
<b>NEXT:</b>
* We Create two NumPy arrays x_train and y_train that have the shape(40000, 3072) and (40000,1) respectively.
* They will contain the last 40000 values from x_train_all and y_train_all respectively

        x_train = x_train_all[VALIDATION_SIZE:]
        y_cat_train= y_cat_train_all[VALIDATION_SIZE:]
        x_train.shape

### Building the model
        
        model = Sequential()
    
    ## ************* FIRST SET OF LAYERS *************************
    # CONVOLUTIONAL LAYER
        model.add(Conv2D(filters=32, kernel_size=(4,4),input_shape=(32, 32, 3), activation='relu',))
    # POOLING LAYER
        model.add(MaxPool2D(pool_size=(2, 2)))
   
    ## *************** SECOND SET OF LAYERS ***********************
    # Since the shape of the data is 32 x 32 x 3 =3072 ...
    # We need to deal with this more complex structure by adding yet another convolutional layer

    # *************CONVOLUTIONAL LAYER
        model.add(Conv2D(filters=32, kernel_size=(4,4),input_shape=(32, 32, 3), activation='relu',))
    # POOLING LAYER
        model.add(MaxPool2D(pool_size=(2, 2)))
    # FLATTEN IMAGES FROM 32 x 32 x 3 =3072 BEFORE FINAL LAYER
        model.add(Flatten())

    # 256 NEURONS IN DENSE HIDDEN LAYER (YOU CAN CHANGE THIS NUMBER OF NEURONS)
        model.add(Dense(256, activation='relu'))

    # LAST LAYER IS THE CLASSIFIER, THUS 10 POSSIBLE CLASSES
        model.add(Dense(10, activation='softmax'))

        model.compile(loss='categorical_crossentropy',
                      optimizer='adam',
                      metrics=['accuracy'])
        model.summary()

### Adding Early stopping
        
        from tensorflow.keras.callbacks import EarlyStopping
        early_stop = EarlyStopping(monitor='val_loss',patience=2)
        history = model.fit(x_train,y_cat_train,epochs=25,validation_data=(x_val,y_val_cat),callbacks=[early_stop])
        metrics = pd.DataFrame(model.history.history)
        metrics
        metrics[['loss', 'val_loss']].plot()
        plt.title('Training Loss Vs Validation Loss', fontsize=16)
        plt.show()
        metrics[['accuracy', 'val_accuracy']].plot()
        plt.title('Training Accuracy Vs Validation Accuracy', fontsize=16)
        plt.show()

### Validating on Test Data

        model.evaluate(x_test,y_cat_test)
        from sklearn.metrics import classification_report, confusion_matrix
        #predictions = model.predict_classes(x_test)
        predictions = np.argmax(model.predict(x_test), axis=-1)
        print(classification_report(y_test,predictions))
        confusion_matrix(y_test,predictions)

        plt.imshow(x_train_all[50000])  # Đúng tập dữ liệu
        plt.title(f"Image at Index: {50000} in x_train_all")
        plt.axis("off")
        plt.show()

        ## plt.imshow(x_test[10])
        plt.imshow(x_train_all[50000])

        ## my_image = x_test[10]
        my_image = x_train_all[50000]
        import numpy as np

        predictions = model.predict(my_image.reshape(1, 32, 32, 3))
        predicted_class = np.argmax(predictions, axis=-1)

        print("Predicted class:", predicted_class)

        print(f"y_train_all shape: {y_train_all.shape}")
        print(f"y_test shape: {y_test.shape}")


        label_index = y_train_all[50000][0] # Hoặc y_train_all[50000] nếu là mảng 1 chiều
        print(f"Label index at 50000: {label_index}")

        label_name = LABEL_NAMES[label_index]
        print(f"Label name: {label_name}")

        LABEL_NAMES[y_test[16][0]]

---
## Artefacts
---

<a href="https://colab.research.google.com/drive/1LFkaZpj5EFmm-Sh2G4h-UGuPpo95sA4y#scrollTo=lgXq0Hik3IA3" target="_blank">Google Colab - Eportfolio Activities - Machine Learning</a><br>

![image](/assets/images/banners/ML11-1.png)
![image](/assets/images/banners/ML11-2.png)
![image](/assets/images/banners/ML11-3.png)
![image](/assets/images/banners/ML11-4.png)
![image](/assets/images/banners/ML11-5.png)
![image](/assets/images/banners/ML11-6.png)
![image](/assets/images/banners/ML11-7.png)
![image](/assets/images/banners/ML11-8.png)
![image](/assets/images/banners/ML11-9.png)
![image](/assets/images/banners/ML11-10.png)
![image](/assets/images/banners/ML11-11.png)
![image](/assets/images/banners/ML11-12.png)
![image](/assets/images/banners/ML11-13.png)
![image](/assets/images/banners/ML11-14.png)

---
## Personal Reflection
---

Working with Convolutional Neural Networks (CNN) for object recognition has been an insightful experience that solidified my understanding of deep learning concepts and their practical applications. This project, centered on the CIFAR-10 dataset, provided me with a hands-on opportunity to build, train, and evaluate a CNN model while exploring the challenges and nuances of computer vision tasks.

Key Learnings
- Understanding the Dataset The CIFAR-10 dataset, with its 60,000 images across 10 classes, offered a structured yet challenging introduction to image recognition. Handling the dataset required preprocessing, such as normalizing pixel values, splitting data into training, validation, and test sets, and ensuring appropriate label encoding for classification. This reinforced the importance of preparing data effectively to enhance model performance.

- Building and Training a CNN Constructing the CNN model was an excellent opportunity to explore how convolutional and pooling layers extract meaningful features from images. Adding multiple layers, such as:

  - Convolutional layers: For feature extraction
  - Pooling layers: For dimensionality reduction
  - Flatten and Dense layers: For classification
demonstrated how the hierarchical structure of CNNs processes image data.

- Watching the model improve during training provided an intuitive understanding of how the network learns patterns like edges, shapes, and textures, progressively combining them to recognize objects.

- Role of Hyperparameters and Callbacks Experimenting with hyperparameters like the number of filters, kernel sizes, and the number of neurons in dense layers highlighted their impact on model performance. Using EarlyStopping as a callback was particularly insightful, as it showcased how regularization techniques help prevent overfitting while reducing training time.

- Performance Metrics Evaluating the model's performance using metrics like accuracy, validation loss, and the confusion matrix reinforced the importance of interpreting results holistically. While accuracy gave a high-level view of performance, the classification report and confusion matrix provided detailed insights into how well the model performed across different classes.

- For example, observing misclassifications for visually similar classes (e.g., "cat" vs. "dog") highlighted the limitations of the model and the importance of fine-tuning to improve performance.

- Visualizing Results Visualizing training and validation loss curves emphasized the significance of monitoring training to detect overfitting or underfitting. Similarly, displaying sample predictions and their corresponding labels enhanced my understanding of the model's strengths and weaknesses.

- Challenges and Problem-Solving
Class Imbalance and Misclassifications One of the challenges was identifying misclassifications in the model's predictions, especially for classes with similar visual features. This made me consider ways to improve performance, such as augmenting the dataset with additional images or incorporating techniques like data augmentation and transfer learning.

- Model Complexity vs. Overfitting Another challenge was balancing model complexity. Adding more layers and filters initially improved performance but led to overfitting on the training data. EarlyStopping and reducing the number of epochs helped mitigate this, underscoring the importance of regularization in deep learning.

- New Image Integration Adding a custom image to the dataset and integrating it into the model's predictions presented a unique challenge. Preprocessing the image (e.g., resizing, normalizing, and handling grayscale-to-RGB conversion) was a learning opportunity, emphasizing the importance of data consistency in image recognition tasks.

Broader Insights
- Importance of Preprocessing The preprocessing steps, from normalizing pixel values to encoding labels, reminded me of the importance of cleaning and preparing data to ensure smooth training and meaningful results. This is particularly crucial in computer vision, where data inconsistencies can significantly affect performance.

- Applications of CNNs This project reinforced the versatility of CNNs in real-world applications. From healthcare diagnostics to autonomous vehicles, CNNs have transformative potential. Working on this project deepened my appreciation for their ability to process and understand image data in ways that mimic human vision.

- Continuous Learning While the model performed well, the process also revealed the limitations of simple CNN architectures. This inspired me to explore advanced techniques like transfer learning with pre-trained models (e.g., VGG16, ResNet) and experimenting with larger datasets to further enhance performance.

Impact on Professional Growth
- This project strengthened my technical skills in building and training deep learning models using Python libraries like TensorFlow and Keras. I also gained confidence in applying CNNs to solve practical problems, such as object recognition, and interpreting their results effectively. The experience further emphasized the importance of visualization and evaluation in understanding model performance, both of which are critical skills in data science.

- Additionally, integrating new images into the dataset allowed me to think creatively about extending and adapting existing models for specific use cases, a skill that will be valuable in professional machine learning projects.

Future Directions
Moving forward, I aim to:
- Experiment with Advanced Architectures: Explore transfer learning with pre-trained models like ResNet, EfficientNet, and Inception to improve accuracy and reduce training time.
- Incorporate Data Augmentation: Use techniques like rotation, flipping, and scaling to expand the dataset and improve generalization.
- Explore Explainability: Investigate explainable AI (XAI) techniques to understand why the model makes certain predictions, which is especially crucial in sensitive applications like healthcare.
- Work with Larger Datasets: Apply these techniques to more complex datasets like ImageNet or domain-specific datasets to tackle real-world challenges.

Conclusion
- This project provided a comprehensive introduction to CNNs and their applications in image recognition. It allowed me to bridge theoretical knowledge with practical implementation, strengthening my understanding of deep learning concepts. The challenges faced and insights gained have not only improved my technical skills but also inspired me to explore more advanced techniques and applications in the future.

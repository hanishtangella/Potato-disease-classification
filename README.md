# Potato-disease-classification

In this project, there are three classes, namely
1. Early Blight Leaf 
 ![0a6983a5-895e-4e68-9edb-88adf79211e9___RS_Early B 9072](https://user-images.githubusercontent.com/91310996/140764317-c8da923b-5a88-491b-aaba-81a7339efa49.JPG)

2. Healthy Leaf
![3c0d6888-c7e1-4cf8-9c25-9a0b8c62ba72___RS_HL 1780](https://user-images.githubusercontent.com/91310996/140764549-f23a3e41-cddc-4b9a-abfb-1eaba5eeaf96.JPG)

3. Late Blight leaf
![5a2996c9-ed8f-4c8d-bab3-b68a833b7811___RS_LB 4786](https://user-images.githubusercontent.com/91310996/140764930-6d7e3b5f-6c57-4917-a18d-914f3b0adcbf.JPG)

After importing the required libraries, read the data using tf.keras.preprocessing.image_dataset_from_directory with target shape of (256,256) and batch size of 32.
Splitted the complete data into three sets namely, training set(80%), validation set(10%), test set(10%).
Used most useful classes like Cache, shuffle, prefetch inorder to make the model robust.
**Building the CNN model**:
1._Creating a Layer for Resizing and Normalization_:
Before I feed my images to network, I should do resizing it to the desired size. Moreover, to improve model performance, I should normalize the image pixel value (keeping them in range 0 and 1 by dividing by 256). This should happen while training as well as inference. Hence I can add that as a layer in our Sequential Model.
You might be thinking why I need to resize (256,256) image to again (256,256). You are right I don't need to but this will be useful when I am done with the training and start using the model for predictions. At that time somone can supply an image that is not (256,256) and this layer will resize it
2. _Data Augmentation_:
In order to avoid overfitting, I used Data Augmentation.
**CNN model**
Building a robust CNN model with many layers:
1) Here I am using my 'resize_and_reshape' and 'data_augmentation' that I built before in order to attain uniformity and to avoid overfitting.
2) Building multiple Conv2d and Maxpool2d layers with 'ReLu' as activation function.
3) Also used Dropout of 10%.
4) Created Dense layer with 3 classes and using 'Softmax' as activation function.
5) Here, I used 'Adam' as optimzer, 'SparsecategoricalCrossentropy' as loss function and 'accuracy' as metric.
6) Took 15 epochs to train our data and we also gave our 'valset' as validation_data.
![image](https://user-images.githubusercontent.com/91310996/140767874-2bc33963-133e-4e3f-a39a-72a9b63dd7a9.png)
![image](https://user-images.githubusercontent.com/91310996/140767918-b3840ee8-6329-4d03-a938-ac8d7998eafc.png)
The above two graphs shows the relationship between my trainset and validation sets.
I got a validation accuracy of **96.43%**,
        Training accuracy of **95.60%**,
        Testing accuracy of **97%**.
    **_Pretty good right :)_**
 I wrote function to predict any new images that we want to classify them.

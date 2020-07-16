**A. Convolutional horses and humans**

  **1. Describe the ImageDataGenerator() command and its associated argument.  What objects and arguments do you need to specify in order to flow from the directory to the generated object?  What is the significance of specifying the target_size = as it relates to your source images of varying sizes? What considerations might you reference when programming the class mode = argument?  How much difference exists when applying the ImageDataGenerator() and .flow_from_directory() commands to the training and test datasets?**
  
*    The ImageDataGenerator() command allows us to use image data generators.  Its associated argument is called rescale, and it normalizes the images by the factor specified.  In the case of convolutionals with images of horses and humans, rescaling by dividing each byte value by 250 allows each byte's value to fall between 0 and 1.  
     
     To generate the training data, you need to use .flow_from_directory() with the training data generator created using ImageDataGenerator().  Likewise, to generate the testing data, you need to repeat this with the testing data generator created using ImageDataGenerator().  You then need to pass an argument to the .flow_from_directory() command that specifies which directory the data comes from.  For the training set, this would be your training directory; for the testing set, this would be your testing directory.  
     
     Whether generating the training data or testing data, you then need to specify the size of the images you would like to provide to the neural network.  This argument is called "target_size," and the images will all be fed through the neural network as that size, no matter what their original size happened to be.  Consequently, it is important to set an appropriate size for your image.  If you set a size that is too small for your images, you could cut off important features.  On the other hand, if you set a size that is too large for your images, you could be wasting valuable space in memory.  
     
     After that, you need to provide the batch size argument, which specifies how many training images to be loaded in a group together.  Lastly, you need to set the class mode argument.  When setting a value for this argument, it is important to consider the dimensionality of the array of class labels.  If the array is two-dimensional, it would be best to use the categorical class mode.  Otherwise, if the array is one-dimensional, it is also important to consider the number of class labels.  If there are just two options (either 0 or 1), then it would be best to use the binary class mode.  If there are more than two, it is best to use the sparse class mode.  

     All of the arguments listed above need to be specified when applying the ImageDataGenerator() and .flow_from_directory() commands, both to the training dataset *and* the testing dataset.  The argument to ImageDataGenerator() is "rescale" and the arguments to .flow_from_directory() include the directory name, "target_size," "batch_size," and "class_mode."  The only difference between the application to the training dataset versus the test dataset is that you would be using two distinct directories that refer to the the training images and testing images, respectively.  Likewise, the data generators would have different names to indicate that one is to be used for training data, while the other is to be used for testing data.

  **2. Describe the model architecture of the horses and humans CNN as you have specified it.  Did you modify the number of filters in your Conv2D layers?  How do image sizes decrease as they are passed from each of your Conv2D layers to your MaxPooling2D layer and on to the next iteration?  Finally, which activation function have you selected for your output layer?  What is the significance of this argument’s function within the context of your CNN’s prediction of whether an image is a horse or a human?  What functions have you used in the arguments of your model compiler?**

---
---

**B. Regression**

  **1. Using the auto-mpg dataset (auto-mpg.data), upload the image where you used the seaborn library to pairwise plot the four variables specified in your model.  Describe how you could use this plot to investigate the co-relationship amongst each of your variables.  Are you able to identify interactions amongst variables with this plot?  What does the diagonal access represent?  Explain what this function is describing with regarding to each of the variables.**
  
  ![seaborn Plot](Regression.PNG)

  **2. After running model.fit() on the auto-mpg.data data object, you returned the hist.tail() from the dataset where the training loss, MAE & MSE were recorded as well as those same variables for the validating dataset.  What interpretation can you offer when considering these last 5 observations from the model output?  Does the model continue to improve even during each of these last 5 steps?  Can you include a plot to illustrate your answer?  Stretch goal: include and describe the final plot that illustrates the trend of true values to predicted values as overlayed upon the histogram of prediction error.**

---
---

**C. Overfit and Underfit**

  **1. What was the significance of comparing the 4 different sized models (tiny, small, medium, large)?  Can you include a plot to illustrate your answer?**
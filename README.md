# UG_Open_Lab
Designed a Convolutional Neural Network (CNN) model to predict gestures of the American Sign Language MNIST dataset.

## Dataset Description
The dataset contains 28x28 images of 24 out of 26 letters of the English alphabet (J and Z are not present in the dataset as they are not static gestures). These images have greyscale values between 0 to 255 and are stored in separate csv files, with the size of each file being approximately half of the standard MNIST dataset.

To create new data, an image pipeline was used based on ImageMagick and included cropping to hands-only, gray-scaling, resizing, and then creating at least 50+ variations to enlarge the quantity. The modification and expansion strategy was filters ('Mitchell', 'Robidoux', 'Catrom', 'Spline', 'Hermite'), along with 5% random pixelation, +/- 15% brightness/contrast, and finally 3 degrees rotation. Because of the tiny size of the images, these modifications effectively alter the resolution and class separation in interesting and controllable ways.
* Title: Sign Language MNIST
* URL: https://www.kaggle.com/datasets/datamunge/sign-language-mnist

### Training Dataset
<table>
<thead>
  <tr>
    <th align="center" colspan="2">Generic Description</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td align="center">Number of samples</td>
    <td align="center">27,455</td>
  </tr>
  <tr>
    <td align="center">Number of columns</td>
    <td align="center">785</td>
  </tr>
  <tr>
    <td align="center">Input features</td>
    <td align="center">784 (Values for 28 x 28 pixels)</td>
  </tr>
  <tr>
    <td align="center">Target variable</td>
    <td align="center">1 (Image label - 0 to 24)</td>
  </tr>
</tbody>
</table>

Before being used to train the model, the above dataset has been augmented and normalized to introduce variations in the dataset and to improve the model's performance respectively.

### Test Dataset
<table>
<thead>
  <tr>
    <th align="center" colspan="2">Generic Description</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td align="center">Number of samples</td>
    <td align="center">7,172</td>
  </tr>
  <tr>
    <td align="center">Number of columns</td>
    <td align="center">785</td>
  </tr>
  <tr>
    <td align="center">Input features</td>
    <td align="center">784 (Values for 28 x 28 pixels)</td>
  </tr>
  <tr>
    <td align="center">Target variable</td>
    <td align="center">1 (Image label - 0 to 24)</td>
  </tr>
</tbody>
</table>

## CNN
The Conv2D, MaxPool2D, Flatten and Dense layers of the Sequential module of the Keras library in Python were used to implement the CNN model.
* Activation functions:
  *  LeakyReLU with alpha = 0.01 has been used for the convolution and hidden computation layers
  *  Softmax has been used for the output layer, since the network performs classification
* Training:
  * Batch size = 512
  * Number of epochs = 50
  * The samples have been shuffled before each epoch to improve the performance of the model

## Results
The model was tested using the test dataset and it was found that the model could accurately predict gestures upto a considerable extent, with the testing accuracy being higher than the training accuracy.

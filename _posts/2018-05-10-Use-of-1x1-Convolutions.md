# 1x1 Convolutions
## The need to use 1x1 kernels/filters 

The common notion about 1x1 filters/kernels is that they are of no use since they dont reduce the dimensions of image size. But when we consider channels of images i.e the features (RGB Colors, Depth of the image, Tranparency etc), 1x1 convolutions have a different story to say.

Consider the following scenario where we apply filters for an input image of size 200x200 with 3 channels. 

##### Description of the scenario :
For the sake of understanding, I am depicting the convolution process using three fragments seperated by two bars. Everything left to the first bar is the input to the layer of the NN and everything to the right is the output of the layer of the NN. This output is fed as the input  to the next layer.
The first fragment notates :
##### (size of the image) x number of channels. 
The second fragment notates :
##### number of kernels x (size of the kernels) x number of channels
The third fragment fed as the  input of next layer notates :
##### (size of the convoluted image) x number of channels
###### 200x200 x 3   | 32  x 3x3 x 3   | 198x198 x 32
###### 198x198 x 32  | 64  x 3x3 x 32  | 196x196 x 64
###### 196x196 x 64  | 128 x 3x3 x 64  | 194x194 x 128
###### 194x194 x 128 | 256 x 3x3 x 128 | 192x192 x 256
###### 192x192 x 256 | 512 x 3x3 x 256 | 190x190 x 512

if we closely observe the number of channels in each input, we can infer that they increase after the convolution. This is a problem for computation as we have limited memory and millions of images to train. So to avoid out of memory error, we need to reduce the dimensions.Here we can choose either to reduce the size of the feature map or the channels. But reducing the size of the feature map doesn't make sense as we have worked hard to learn the features. Hence reducing the channels is the logical way forward. To affect the number of channels, we need to change the number of kernels in the middle fragment without affecting the size of the feature map. So we choose a 1x1 matrix to retain the size of the feature map and change the number of kernels to reduce the number of channels. Here is the mentioned step of reducing the number of channels (reduction from 512 to 10): 
###### 190x190 x 512 | 10 x 3x3 x 512 | 190x190 x 10
This process of feature merging helps to retain the relevant features.
<img src="./Images/convo.png">

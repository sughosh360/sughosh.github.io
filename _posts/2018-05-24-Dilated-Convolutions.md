# Dilated Convolutions
### What does it do?
It increases the receptive field by using a dilated filter size, retaining the resolution and lowering the computational cost. It increases the receptive field by skipping input values.

### Filter size after dilation :
Spaces are inserted between the kernel/filter elements. Since the operation is axis invariant, let us take one axis and assume d-1 spaces are inserted between filter elements along that axis so that d=1 gives us casual convolution. The dilated size of the filter is then given by : 

##### k' = k + (k-1)*(d-1)

where d-1 spaces are inserted in the k-1 possible places between elements.

Among few of the use cases, the dilated convolutions are used in the following :
1) [Wavenet]( https://arxiv.org/pdf/1603.07285.pdf)
2) [Image Segmentation](https://arxiv.org/abs/1412.7062)

# Transposed Convolutions/Deconvolution 
Deconvolution is not the inverse of convolution rather it is convolution done on output to get input(reversing flow with the same operation). This process is used to get the input feature map and not the input image (data). Accordingly, it is used to map the given data to a higher dimensional space. It can be used in the decoder part of autoencoder to get the input feature map. 

One simple way to visualize this process of convolution is to closely follow the arithmetic behind it :
Consider the process of convoluting a 5x5 input image with a 3x3 kernel in strides of 1. This gives us an output feature map with dimensions 3x3. 

If we imagine the reverse of this process, then we convolute 3x3 matrix with a 3x3 kernel in strides of 1. To get back the dimensions of the original image, we need to pad the input in this operation. We need to pad a 2x2 size over the 3x3 input to get a 7x7 input map. Now convoluting the 7x7 input map with the 3x3 kernel in strides of 1 gives us 5x5 output feature map which was the input in the previous convolution process.

# ReLU
ReLU is an activation function. The expansion of ReLU is Rectified Linear Unit. The word linear is deceiving, throwing us off that the activation function is linear.
Linear activations are useless because we can affect the change done by the linear layers using one layer consisting the product of all linear transformations thus rendering the layers redundant.
Back to ReLU being a non-linear activation function. Across the whole domain, ReLU is a non-Linear activation function. But considered piecewise, ReLU is Linear over the domain (-inf,0] or \[0,inf) where inf is infinity.
The definition of ReLU :
##### y = max(0,x)

Non-Linear activations are important because we can get any shape we want using non-linear functions which is not possible with a linear function. Intuitively, a line cannot produce a curve. But a curve can produce a line rather a curve is a generalization of a line.
ReLU is simple and elegant hence easy to use.
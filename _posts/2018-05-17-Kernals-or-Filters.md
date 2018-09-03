# Kernels/Filters
Since long enough, scientists are known to use sophisticated and elusive language to communicate simple ideas to sound cool or to appear learned. The same way, matrix, a simple algebraic term has been called a kernel/filter in the computer vision vernacular. A kernel/filter is a matrix used in the operation of convolution. Explanation of convolution operation can be found here [Wikipedia](https://en.wikipedia.org/wiki/Kernel_(image_processing)).

Consider the following convolution operations on images:
![0.1wjfm0duac6j](images/0.1wjfm0duac6j)
![0.0yico7bq78fg](images/0.0yico7bq78fg)
![0.l5jtjh1hojr](images/0.l5jtjh1hojr)
![0.uxqn73525j9](images/0.uxqn73525j9)

#### Explanation of convolution operations with kernels :
The matrices that are convoluted with the images labeled as original are called the kernels/filters. As we can observe multiplication of matrices with specific values allows us to affect the original image. 
All that the operation is doing is comparing a pixel value with its neighboring values. Each pixel value is surrounded by 8 other pixel values except for those at the edges. For the pixel values at the edges, we use a technique called padding on the image to make a valid convolution operation on the image.
To understand the working of the operation, take a simple 3x3 matrix and convolute it with the kernel which outputs an identical image. After convolution, you get back the same 3x3 matrix that was started with initially. 

#### Padding 
We add additional columns of zeroes to the image matrix to make the convolution operation to work.
![0.yeu3vai3nhl](images/0.yeu3vai3nhl)

#### Why dimensions of kernels are in most cases odd
Most places we see the dimensions of the kernels to be odd. The reason is to center the kernel on top of a pixel value and compare all the neighboring pixel values.

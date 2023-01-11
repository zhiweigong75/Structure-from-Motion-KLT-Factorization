# Structure-from-Motion-KLT-Factorization
This repository provides our implementation of Structure from Motion using Factorization Approach for orthographic camera cases.

## Feature Point Tracker
The feature point tracker we use is Kanade–Lucas–Tomasi (KLT) feature tracker [1]. Good features are located by examining the minimum eigenvalue of each 2 by 2 gradient matrix, and features are tracked using a Newton-Raphson method of minimizing the difference between the two windows. Multiresolution tracking allows for relatively large displacements between images.

## Factorization Method
The factorization approach [2] is implemented for estimation of object shape and camera motion from image stream.

## Implementation
We choose the first frame in the video and delete some Shi-Tomasi corner points in it, following that, utilizing Lucas-Kanade optical flow, we iteratively track these points.

Through the tracking of P points over F frames of images, the 2FxP measurement matrix W is constructed. In order to use the rank theorem, the rotation and translation are measured with respect to the object's centroid. The rotation matrix is described by: both rotation (R) and translation (T) of the dimensions 2Fx3 and 3xP, respectively. In order to estimate the rotation and translation matrices, we use the factorization approach after obtaining the SVD decomposition. To solve for matrix Q, we use the cholesky decomposition. Finally, we align the first camera reference system with the world reference system.

## Data: Castle Image Sequence & Medusa Head Image Sequence
<p align="center">
  <img width="460" height="300" src="https://github.com/zhiweigong75/Structure-from-Motion-KLT-Factorization/blob/main/Images/castle.jpg">
  <img width="460" height="300" src="https://github.com/zhiweigong75/Structure-from-Motion-KLT-Factorization/blob/main/Images/Medusa.jpg">
</p> 

## Structure from Motion
<p align="center">
  <img width="460" height="300" src="https://github.com/zhiweigong75/Structure-from-Motion-KLT-Factorization/blob/main/Images/SfM_castle.jpg">
  <img width="460" height="300" src="https://github.com/zhiweigong75/Structure-from-Motion-KLT-Factorization/blob/main/Images/SfM_Medusa.jpg">
</p> 

## References
[1] Jianbo, Shi, and Carlo Tomasi. "Good features to track." In IEEE Computer Society Conference on Computer Vision and Pattern Recognition, pp. 593-600. 1994.
[2] C. Tomasi and T. Kanade, "Shape and motion from image streams under orthography-- a factorization method," International Journal of Computer Vision, 9(2):137--154, 1992.


# 3D-reconstruction
NTUST Computer Vision and Applications

1. Writing programs for reading BMP images, then generating XYZ files for illustrating 3D voxel models.
2. There are four data sets, says "Bird", "Last", "Teapot", and "Monkey". Each set has 11 silhouette images. In a image, white pixels indicate "foreground", and black pixels mean "background" All images are taken with the same intrinsic parameter, and their extrinsic parameters are corresponding to the number in the TXT file . For example, 01.bmp, 02.bmp, 03.bmp et. al. have the extrinsic parameters shown in camera parameter.txt
3. The initial workspace in world coordinate is around ( 50, 50, 0) to (50, 50, 100). The voxel is a cube with 1 x 1 x 1 in dimensions. So, there are 1.0 million candidate voxels should be processed. Please project all voxels onto each silhouette image ,and check their existence.

### The snapshot of camera configuration and all ground truths
![](https://github.com/naiyu0609/3D-reconstruction/blob/main/png/1.PNG)

### Reference result as following
![](https://github.com/naiyu0609/3D-reconstruction/blob/main/png/2.PNG)

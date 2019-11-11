# MLCloudDetection
This project was for the ESA 2019 Summer of Code

Cloud detection with machine learning using the RGBN bands

This algorithm started off as just applying band thresholding and other filters and then progressed into using algorithms, such as K-Means Clustering and Quickshift to cluster the image, to try and detect and mask clouds. A big issue that I’ve come across is trying to detect haze in an image. V1 also contains cloud shadow masking that is based upon the generated cloud mask. A problem with this is if there’s a cloud shadow in the image but there’s no cloud, it won’t get detected. Otherwise, it's pretty decent at detecting cloud shadows.

V1 does contain a bit of machine learning, as it is just an initial attempt at solving this issue and so that I can learn the basics, but more advanced machine learning (CNN’s) is definitely going to be explored in V2. The included model and training data is pretty limited (only 80 or so samples) so the SVM's performance at classifying clusters is not the greatest. However, with more training data and more inputs, such as the GLCM outputs, I believe it would be able to perform better.

Another area to look into would be going back to using the K-Means Clustering instead of the Gaussian Mixture Model. I chose to use the GMM because it generally clustered pixels more accurately, however it is much, much slower than the K-Means algorithm in ```scikit-learn``` because (among other things like ```covariance_type``` and ```num_clusters```) it doesn't have a ```n_jobs``` argument, which parallelizes the algorithm.   

The main constraint with all of this is only being able to use the RGB and N bands as the images only contain those.

## Getting Started
### DISCLAIMER: These instructions are for Windows 10
1. Make sure you install or have a Python version supported by Snappy
2. Install all the libraries in the requirements.txt file
3. Install ESA SNAP and Snappy
4. Follow all the instructions for installing Snappy in the links below
5. Proceed to [Running the sample](#running-the-sample)

### Installing Snappy
https://senbox.atlassian.net/wiki/spaces/SNAP/pages/50855941/Configure+Python+to+use+the+SNAP-Python+snappy+interface

https://github.com/senbox-org/snap-engine/tree/master/snap-python/src/main/resources

### Running the sample
1. Run all the cells in [cloudv1.ipynb](cloudv1.ipynb)

### Usage
1. Rename [sample_consts.py](sample_consts.py) to ```consts.py```
2. Fill in the fields
3. Uncomment line 182 in [cloudv1.ipynb](cloudv1.ipynb) if you want to get your data from an S3 bucket
4. Run all the cells in [cloudv1.ipynb](cloudv1.ipynb)

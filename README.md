# 760-project

## Downloading the landmark dataset

To download the landmark dataset go to `data_download/` . Follow these steps:

1. Create a folder where the dataset will go.
2. Download the train.csv and train.npy files from the dropbox I shared. Alternatively download the train.csv and save it in the folder where you are going to create the dataset. Then run `Example_csv2npy.py`. Make sure to set the `path_urls` variable in that script to the correct path.
3. Modify the `path_urls` variable in `Example_DownloadDataset.py`.
4. Run `Example_DownloadDataset.py`. In this file depending if you want to download the files for the train or test set you will have to comment and uncomment some sections of the code. Just read the comment in the file.

**NOTE:** Even if the download crashes at any point you if you re-run  `Example_DownloadDataset.py` it will restart where it left off.

## Setup 

The code in this repository relies is written in python 3. In python 3 the python image library (PIL) is called pillow. 

```
	conda create -n py3env python=3.5
	source activate py3env
	conda install numpy
 	conda install pillow
 	conda install tensorflow=1.3.0
 	pip install daiquiri
```

The package daiquiri is needed for logging in the capsnetEM model. Pillow is needed to load the 
landmark dataset. 

**NOTE:** If you want to setup tensorflow with gpu support instead of doing `conda install tensorflow=1.3.0` run `conda install tensorflow-gpu=1.3.0`.

### CapsNetEM Setup

After downloading all the dependencies above, create the following two directories inside `mnist_capsnetEM/`

```
	mkdir mnist_capsnetEM/logdir/
	mkdir mnist_capsnetEM/test_logdir/
```

Finally make sure that the line `line 83` in `capsnetEM_mnist_train.py` is set to use cpu or gpu whatever you need.

Then to train simply run `capsnetEM_mnist_train.py`.

## Dataset Notes

### Google Image Retrieval and Recognition Dataset Notes

* *Task:* take a query image and retrieve a set of images that depict a landmark contained in the query image.
* More than a million images.
* 15k landmarks (i.e. categories/classes).
* test set: 40GB index set: 359 GB
* There are no labels. We have to use some pretrained model, do some feature engineering, or use the data from the landmark recognition challenge to pretrain your own model.

#### Dataset Description

* The query images are listed in 'test.csv'
* The index from which we will retrieve the images is in 'index.csv'.

### Google Landmark Recognition Dataset Notes

* More than a million images
* 15k classes
* From the 15k classes about 50-100 of them contain 1/3 of the data

#### Dataset Description

* The training set has all landmarks labeled with a landmark ID.
* The training set each image will depict a single landmark.
* The test set each image may have none, 1 or more landmarks.
* The test set has no labels.



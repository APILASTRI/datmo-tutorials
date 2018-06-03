### Face Recognition

a. Introduction
This is a tutorial on face recognition to show case classifiers built using datmo, in order to track our work and make machine learning workflow reproducible and usable. We have built classifier for facial recognition, with very few images here. The accuracy from this tutorial can be improved with more training images. You can also increase the number of classes or faces. 

During this experimentation, we perform model engineering and will be using datmo to create versions of work by creating snapshot.

b. Installation
To use datmo, you can install it using pip install datmo after having the prerequisites as in this README

To run the experimentation.ipynb file, you can run it with datmo task run command, it uses docker for environment management.

```bash
home:~/datmo-tutorials/face-recognition$ datmo task run -p 8888:8888 "jupyter notebook"
```
c. Solution
After the installation, we run the experimentation.ipynb notebook and perform following steps,

* Visualizing the images
* Face detection
* Extracting facial encoding to train a classifier
* Using random forest classifier 
* Using KNN classifier

d. Creating versions or snapshots
During the process of model engineering, we will be using datmo to create versions of work by creating datmo snapshots. As you see below, we created two snapshots at the end of the notebook tutorial. More information about the flow can be found in the notebook file.

```bash
home:~/datmo-tutorials/face-recognition$ datmo snapshot create -m "knn classifier"
Creating a new snapshot
Created snapshot with id: 7a3530f742
```

After running this, you should be able view the created snapshot using the command, `snapshot ls`

```bash
home:~/datmo-tutorials/face-recognition$ datmo snapshot ls
+-------------+-----------+--------------------+---------------+--------------+-------+
|   id        | created at|      config        |      stats    |    message   | label |
+-------------+-----------+--------------------+---------------+--------------+-------+
| 7a3530f742  | 2018-06-03| {'n_neightbors': 7}| {'accuracy':  |     knn      |  None |
|             | 07:22:07  |                    |   0.8125}     |  classifier  |       |
+-------------+-----------+--------------------+---------------+--------------+-------+
| 9095c50d30  | 2018-06-03|   {'n_jobs': 6}    | {'accuracy':  | random forest|  None |
|             | 07:22:07  |                    |  0.9375}      |  classifier  |       |
+-------------+-----------+--------------------+---------------+--------------+-------+
```
Now after the creation of snapshots, we can perform checkout to a different version with the following command,

```
home:~/datmo-tutorials/datmo-face-recognition$ # Run this command: datmo snapshot checkout --id <snapshot-id>
home:~/datmo-tutorials/datmo-face-recognition$ datmo snapshot checkout --id 9095c50d30
```
Built using [dlib](http://blog.dlib.net/2017/02/high-quality-face-recognition-with-deep.html) and [face_recognition](https://github.com/ageitgey/face_recognition)

# Homework 2 - Creating Backdoor Detector Design

- By Ankush Pratap Singh

```bash
├── data 
    └── cl
        └── valid.h5 // this is clean validation data used to design the defense
        └── test.h5  // this is clean test data used to evaluate the BadNet
    └── bd
        └── bd_valid.h5 // this is sunglasses poisoned validation data
        └── bd_test.h5  // this is sunglasses poisoned test data
├── models
    └── bd_net.h5
    └── bd_weights.h5
    └── B_prime_2.h5
    └── B_prime_4.h5
    └── B_prime_10.h5
├── Homework_2_ax2047.ipynb
└── eval.py // this is the evaluation script
```

## I. Dependencies
   1. Python 3.6.9
   2. Keras 2.3.1
   3. Numpy 1.16.3
   4. Matplotlib 2.2.2
   5. H5py 2.9.0
   6. TensorFlow-gpu 1.15.2
   7. Pandas
   8. Seaborn 
   
## II. Data
   1. Download the validation and test datasets from [here](https://drive.google.com/drive/folders/1Rs68uH8Xqa4j6UxG53wzD0uyI8347dSq?usp=sharing) and store them under `data/` directory. If you want to directly use, I have already downloaded and uploaded in required data under `data/` directory.
   2. The dataset contains images from YouTube Aligned Face Dataset. We retrieve 1283 individuals and split into validation and test datasets.
   3. bd_valid.h5 and bd_test.h5 contains validation and test images with sunglasses trigger respectively, that activates the backdoor for bd_net.h5. 

## III. Running and Creating Backdoored Model  
   1. To create B_prime models, run each cell of the file Homework_2_ax2047.ipynb. 
   2. Make sure to uncomment the part which is corresponding to the required threshold value (drop in   clean_accuracy_valid) and comment out the parts which are for other threshold values.
   3. Only once you have all the three model file corresponding to different threshold values, then only proceed to the comparison section. **It will throw an error if you do not create all the three different B_prime models.**
   3. Exisiting created B_prime models can also be used which are present in `models/` directory named as B_prime_2.h5, B_prime_4.h5 and B_prime_10.h5.

## III. Evaluating the Backdoored Model
   1. The DNN architecture used to train the face recognition model is the state-of-the-art DeepID network. 
   2. To evaluate the backdoored model, execute `eval.py` by running:  
      `python3 eval.py <clean validation data directory> <poisoned validation data directory> <model directory>`.
      
      E.g., `python3 eval.py data/cl/valid.h5 data/bd/bd_valid.h5 models/B_prime_10.h5`. This will output:
      Clean Classification accuracy: 84.43751623798389
      Attack Success Rate: 77.015675067117

## IV. Important Notes
Please use only clean validation data (valid.h5) to design the pruning defense. And use test data (test.h5 and bd_test.h5) to evaluate the models. 

For any further enquires, drop a mail on ankushpratap@nyu.edu

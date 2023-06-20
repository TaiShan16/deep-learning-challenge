# deep-learning-challenge

## Overview
In this project, a tool is developed with the aim of assisting the nonprofit organization, Alphabet Soup, in efficiently selecting funding applicants who demonstrate the highest probability of achieving success in their endeavors. Leveraging the principles of machine learning and neural networks, the provided dataset's features are employed to construct a binary classifier capable of predicting the potential success of applicants if granted funding by Alphabet Soup.

The dataset, which is available in CSV format, encompasses a comprehensive record of over 34,000 organizations that have received financial support from Alphabet Soup throughout the years. Below is the dataset's columns encompass various metadata attributes pertaining to each organization, serving as valuable indicators for analysis and decision-making.

EIN and NAME—Identification columns
APPLICATION_TYPE—Alphabet Soup application type
AFFILIATION—Affiliated sector of industry
CLASSIFICATION—Government organization classification
USE_CASE—Use case for funding
ORGANIZATION—Organization type
STATUS—Active status
INCOME_AMT—Income classification
SPECIAL_CONSIDERATIONS—Special considerations for application
ASK_AMT—Funding amount requested
IS_SUCCESSFUL—Was the money used effectively

## Results: 

### Data Preprocessing
- The target variable in this model is 'IS_SUCCESSFUL'
- The variables feature in this model are:
    APPLICATION_TYPE
    AFFILIATION
    CLASSIFICATION
    USE_CASE
    ORGANIZATION
    STATUS
    INCOME_AMT
    SPECIAL_CONSIDERATIONS
    ASK_AMT

- EIN and NAME are variables that were removed from the input data because they are neither targets nor features.
  
### Compiling, Training, and Evaluating the Model
In the initial model, the following parameters are employed for the neural network model:
- Two hidden layers consisting of 80 and 30 neurons, respectively, utilizing Rectified Linear Unit (ReLU) as the activation function.
- A single output layer is incorporated, employing a binary classifier alongside the Sigmoid activation function. The 'adam' optimizer
  is utilized for optimization purposes; and accuracy metrics are extracted to evaluate the model's performance.
- These parameters were chosen due to their minimal computational time.
  
![image](https://github.com/TaiShan16/deep-learning-challenge/assets/122623573/ff031868-ef72-49ed-b768-21eec1f9dc7a)

  
In the 2nd model, the following parameters are employed:
- Three hidden layers, consisting of 80, 40, and 20 neurons, respectively, utilizing Rectified Linear Unit (ReLU) as the activation function.
- A single output layer is incorporated, employing a binary classifier alongside the Sigmoid activation function. The 'adam' optimizer
  is utilized for optimization purposes; and accuracy metrics are extracted to evaluate the model's performance.
- The decision to increase the number of hidden layers to three was made in response to the initial model's prediction accuracy falling below 75%.
  
![image](https://github.com/TaiShan16/deep-learning-challenge/assets/122623573/e1eac688-2828-456c-a5f8-1dc0c2c07ed6)


The initial model yielded an accuracy of 72.87%, whereas the second model achieved an accuracy of 72.90%. Despite incorporating three hidden layers 
in the second model, there was only a marginal improvement in accuracy.

Accuracy result from the initial model:

![image](https://github.com/TaiShan16/deep-learning-challenge/assets/122623573/bfa9b4ce-ed41-435e-848d-2492460418b8)


Accuracy result from the second model:

![image](https://github.com/TaiShan16/deep-learning-challenge/assets/122623573/1c209a5d-23a3-4f93-84b4-3a11caec6817)



To enhance the model's performance, an automated model optimizer was employed with the objective of attaining the utmost accuracy. This was achieved by developing a method that utilizes the keras-tuner library to create a keras Sequential model, incorporating various hyperparameter options for optimization.

![image](https://github.com/TaiShan16/deep-learning-challenge/assets/122623573/de10fc91-922f-4a27-b5bc-bdeb2fd91441)



A function was implemented to facilitate hyperparameter tuning of deep learning models, encompassing the incorporation of three distinct activation functions, namely ReLU, Tanh, and Sigmoid, within the hidden layers. The function systematically iterates through various attributes on the initial layer, subsequently exploring a range of 1 to 20 neurons on subsequent layers. Additionally, the function explores different configurations of hidden layers and their respective neurons, thereby enabling comprehensive experimentation and evaluation of model performance.

![image](https://github.com/TaiShan16/deep-learning-challenge/assets/122623573/9861fac2-2d65-4f27-9b93-8779115efcde)


Then, kt Hyperband function is utilized to run the optimizer.

![image](https://github.com/TaiShan16/deep-learning-challenge/assets/122623573/0ddb849e-96c3-4a04-af80-20f6472db9e4)


A search function was employed to identify the optimal combination of hyperparameters, resulting in the determination that the model achieved an accuracy of 73.38% 

![image](https://github.com/TaiShan16/deep-learning-challenge/assets/122623573/71f58fc7-1210-4803-85bb-e7154eddc2cb)


The most optimal model, as determined by the keras tuner method, was obtained using a sigmoid activation function with an input node count of 7. 
Additionally, the model consisted of 7 hidden layers and underwent 30 training epochs.

![image](https://github.com/TaiShan16/deep-learning-challenge/assets/122623573/0173bd17-933e-4ad9-94dc-23f419122b43)


## Summary
The neural network model, which underwent optimization using the keras tuner method, achieved a prediction accuracy of 73%. This was accomplished by utilizing a sigmoid activation function. Notably, the performance improvement compared to the non-optimized model was only marginal. Considering the lack of substantial improvement in the prediction accuracy of the model when compared to the initial model, it is advisable to explore alternative hyperparameter combinations. This can be accomplished by conducting experiments encompassing a broader range of hyperparameter values, including the manipulation of layer count, neurons per layer, activation functions, learning rates, and batch sizes. This comprehensive exploration holds the potential to reveal a more optimal configuration that can yield enhanced accuracy.

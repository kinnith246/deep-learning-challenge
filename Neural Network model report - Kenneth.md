# Module 21 Report

## Overview of the Analysis

The purpose of this analysis is to build and optimize a neural network model using TensorFlow and Keras to predict the success of charity funding applications for the Alphabet Soup organization. The main goal is to develop a deep learning model that can achieve a predictive accuracy greater than 75%.

## Results

# Data Preprocessing:
- What variable(s) are the target(s) for your model?
    * The target variable for the model is IS_SUCCESSFUL, which indicates whether a funding application was successful (1) or not (0).

- What variable(s) are the features for your model?
    The feature variables used in the model are:
    * Categorical variables like CLASSIFICATION, APPLICATION_TYPE, AFFILIATION, USE_CASE, ORGANIZATION, INCOME_AMT, SPECIAL_CONSIDERATIONS were one-hot encoded using pd.get_dummies().
    * Continuous variables like ASK_AMT (the amount of funding requested) were included directly.

- What variable(s) should be removed from the input data because they are neither targets nor features?
    * Non-informative variables like EIN (Employer Identification Number) and NAME of the organization were removed, as these are identifiers and do not contribute to the prediction of success.

## Compiling, Training, and Evaluating the Model:

Base Model:
- Architecture:
    * First Hidden Layer: 80 neurons, ReLU activation.
    * Second Hidden Layer: 30 neurons, ReLU activation.
    * Output Layer: 1 neuron, Sigmoid activation (for binary classification).
    * Total Parameters: 5,981.

- Training:
    * Epochs: 150
    * Batch Size: 32

- Results:
    * Training Accuracy: ~73.35% after 150 epochs.
    * Validation Accuracy: 72.68%, with a loss of 0.5736.

The initial model had a fairly decent accuracy but failed to achieve the target accuracy of 75%. This suggested the need for optimization to enhance the model's performance.

Optimized Model:
- Architecture:
    * First Hidden Layer: 256 neurons, Leaky ReLU activation.
    * Second Hidden Layer: 128 neurons, Tanh activation.
    * Third Hidden Layer: 64 neurons, ReLU activation.
    * Output Layer: 1 neuron, Sigmoid activation (for binary classification).
    * Total Parameters: 52,481.

- Training:
    * Epochs: 150
    * Batch Size: 32

- Results:
    * Training Accuracy: ~72.84% after 150 epochs.
    * Validation Accuracy: 72.84%, with a lower loss of 0.5667 compared to the base model.

Although the accuracy of the optimized model only slightly improved to 72.84% from the base model’s 72.68%, the model’s loss improved, indicating better generalization. Additional tuning and adjustments would likely be needed to reach the target 75% accuracy.

## What steps did you take in your attempts to increase model performance?
Increased the number of neurons in the first hidden layer to 256 from 80 and in the second hidden layer to 128 from 30. This helped capture more complexity in the data.

Added a third hidden layer with 64 neurons to allow the model to learn more intricate patterns.

Used different activation functions:

The Leaky ReLU function was used in the first hidden layer to avoid the "dying ReLU" problem where neurons become inactive.
The Tanh function was introduced in the second hidden layer to allow smoother gradients and a different non-linear transformation.
Maintained the Sigmoid activation in the output layer as the task is a binary classification problem.

## Summary

The final optimized neural network model achieved an accuracy of 72.84%, which is a slight improvement over the base model's accuracy of 72.68%. However, despite the optimization attempts, the model did not reach the target accuracy of 75%.

Recommendation to further improve the model:
- Increase or decrease the learning rate for finer control over the optimization process.
- Experiment with more advanced architectures, such as adding more hidden layers or using alternative techniques like batch normalization.
- Consider other models: A different machine learning model such as Random Forest or XGBoost may perform better than a deep learning approach for this specific task.

The deep learning model shows promise, but further tuning or a different model approach could help reach or surpass the target accuracy of 75%.

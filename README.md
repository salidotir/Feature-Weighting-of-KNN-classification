# Feature Weighting in KNN Classification

## Overview

This bachelor's project explores feature weighting within K-Nearest Neighbors (KNN) classification to enhance K-accuracy, utilizing gradient descent and leave-one-out techniques. Supervised by Dr. Mohammad Taheri, this project aims to refine the accuracy metrics of the KNN model through innovative weight adjustments of data features.

## Abstract

Feature weighting is a novel approach aimed at improving the accuracy of nearest neighbor classifications. Traditionally, techniques such as prototype weighting have focused on optimizing weights assigned to each class in a dataset to maximize the agreement among data points within the k-nearest neighbors. This project introduces an alternative strategy—feature weighting—to determine the optimal weights for individual features to enhance k-accuracy, defined as the presence of at least one label matching the query sample within its k-nearest neighbors.

## Methodology
  Full method and report are uploaded in this repository as well.
  
  **\*Note\*** Since this was a project for Shiraz University, the report is written in persian. So you can find the formula implemented in the following.

### Mathematical Formulations

1. **Features Representation in Dataset**
   - Definition: Each data point in dataset \(T\) has \(D\) features.
     
     $`\forall x \in T \rightarrow x \text{ has } D \text{ features}`$
     
2. **Distance Metric Definition**
   - Formula for calculating weighted Euclidean distance between two data points \(x_1\) and \(x_2\).
     
     $`d_E(x_1, x_2) = \sum_{j=0}^{D} (x_{1j} - x_{2j})^2 w_j`$

3. **Objective Function for Gradient Ascent**
   - Objective function used in gradient ascent to maximize the classification accuracy.
     
     $`J_w = \frac{1}{N} \sum_{x \in T} \text{acc}(T-x)(x)`$


4. **Accuracy Function Using Step Function**
   - Accuracy calculation using a step function based on radius and distance.

     $`\text{acc}(x) = \text{step}\left(\frac{R_w(x)}{d_E(x, x=)}\right)`$

5. **Radius Calculation for Nearest Neighbor**
   - Determines the radius \(R_w(x)\) for the nearest neighbor search.

     $`R_w(x) = d_E(x, N_k(x))`$

6. **Definition of the Step Function**
   - Binary step function used in the accuracy calculation.

     $`\text{step}(z) = 
     \begin{cases} 
     1 & \text{if } z \geq 1 \\
     0 & \text{if } z < 1
     \end{cases}`$

7. **Sigmoid Function for Differentiability**
   - Sigmoid function replacing the step function to allow gradient calculations.

     $`\phi_\beta(z) = \frac{1}{1 + e^{\beta(1-z)}}`$

8. **Derivative of Sigmoid Function**
   - Derivative of the sigmoid function essential for computing the gradient.

     $`\phi'_\beta(r_x) = \beta e^{\beta(1-r_x)} \left(\frac{1}{(1 + e^{\beta(1-r_x)})^2}\right) = \beta \phi_\beta(r_x) (1 - \phi_\beta(r_x))`$

9. **Gradient of the Objective Function**
   - Gradient of the objective function with respect to the weights.

     $`\frac{\partial J_w}{\partial w_i} = \sum_{x \in T} -\phi'_\beta(r_x) R_w(x) \frac{\sum_{j=0}^{D} (x_j - x'=) d_E(x, x'=)^2}{d_E(x, x'=)}`$

10. **Weight Update Rule in Gradient Ascent**
    - Rule for updating the feature weights in each iteration of gradient ascent.

      $`w_{i, \text{new}} = w_{i, \text{old}} + \alpha \frac{\partial J_w}{\partial w_i}`$


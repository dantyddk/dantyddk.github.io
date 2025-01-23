---
layout: post
title: UoE - Machine Learning October 2024 A - Perceptron Activities
subtitle: Understand the applicability and challenges associated with different datasets for the use of machine learning algorithms.
categories: EL-Activities
tags: [UoE, coding, Module E-Portfolio Learning Activities]
---
---
## Perceptron Activities
---

### simple_perceptron

    import numpy as np
    
    # Lets define the Inputs and weights
    # With NumPy, we work with arrays. Hence we will need to define our inputs as arrays
        inputs = np.array([90, 80])
    
    # Check the type of the inputs
        type(inputs)
   
    # check the value at index position 0
        inputs[0]
    
    # Lets define the weights
    
    # creating the weights as Numpy array
        weights = np.array([0.7, 0.1])

    # Check the value at index 0
        weights[0]

    # Create the Sum Function
    ## The dot function is called the dot product from linear algebra. If you are dealing with a huge dataset, The processing difference between the for loop used in the last notebook and this dot product will significantly be different.
        def sum_func(inputs, weights):
          return inputs.dot(weights)

    # for weights = [0.9, 0.2]
        s_prob1 = sum_func(inputs, weights)
        s_prob1
--
    
    # Create Step function
        def step_function(sum_func):
        if (sum_func >= 1):
            print(f'The Sum Function is greater than or equal to 1')
        return 1
        else:
            print(f'The Sum Function is NOT greater')
        return 0
    
    # Result
        step_function(s_prob1 )
--
        
        weights = [-0.9, 0.2]
        s_prob2 = sum_func(inputs, weights)
        round(s_prob2, 2)  #round to 2 decimal places
--

    # Result
        step_function(s_prob2 )

### perceptron_AND_operator

    import numpy as np
    # Inputs
    ## Creating input values as a matrix not as a vector
        inputs = np.array([[0,0], [0,1], [1,0], [1,1]])
   
    ## Checking the shape of the inputs
        inputs.shape
    # Outputs
        outputs = np.array([0, 0, 0, 1])
    ## Checking the shape of the outputs
        outputs.shape

    # Weights
    ## One weight for x1 and one for x2
        weights = np.array([0.0, 0.0])
    
    ## Learning Rate
        learning_rate = 0.1
    
    # Step function
    ## This is our Activation function
        def step_function(sum):
          if (sum >= 1):
        return 1
        else:
        return 0

    # Process Output
    ## We define a function that allows us to calculate/ process the output. The function accepts an instance of our data, then calculate the sum function using Numpy. Finally, we check the output by passing it through the "Step Function."</b>
        def cal_output(instance):
          sum_func = instance.dot(weights)
          return step_function(sum_func)
    ## We pass it as alist in a numpy array ...
        cal_output(np.array([[1,1]]))
--

    # Check the number of outputs
        len(outputs)
    
    # Checking the index of the input at postion 3 ..
    # this is the last inpute value
        inputs[3]
        inputs
    
        def train():
        total_error_value = 1
        while (total_error_value != 0):
            total_error_value = 0
            ## Looping into each row of the dataset (remember indexing in python starts at zero hence 0-3 which are 4 values)
                for i in range(len(outputs)):
            ##Calculating predictions
                prediction = cal_output(inputs[i])
            ## Calculating the absolute value of the error
                error = abs(outputs[i] - prediction)
            ## Updating the error
                total_error_value  += error

            if error > 0:
                for j in range(len(weights)):
                    #updating the weights for x1 and x2
                    weights[j] = weights[j] + (learning_rate * inputs[i][j] * error)
                    print('Weight updated to: ' + str(weights[j]))
        print('Total error Value: ' + str(total_error_value))
        train()
--

    # Classification
    ## Now we have the final weights that will be used to classify new instances of the data after training.
        weights
--

    cal_output(np.array([0,0]))
    cal_output(np.array([0,1]))
    cal_output(np.array([1,0]))
    cal_output(np.array([1,1]))

### multi-layer Perceptron

    import numpy as np
    
    # Define the Sigmoid Function
        def sigmoid(sum_func):
          return 1 / (1 + np.exp(-sum_func))
        sigmoid(0)
    
    np.exp(2)
--
    
    np.exp(1)    
    sigmoid(40)
    sigmoid(-20.5)
--
    
    # Input Layer to Hidden Layer
    ## Define "Inputs, outputs and weights" as Numpy arrays
        inputs = np.array([[0,0],
                   [1,0],
                   [1,1]])
        inputs
        inputs.shape
        
        outputs = np.array([[0],
                    [1],
                    [1],
                    [0]])

        outputs.shape
   
    # Weights
    ## These weights are for the connection between the inputs and the hidden layer
    ### First row holds the weights for x1, 2nd row contains the weights for x2
        weights_0 = np.array([[-0.424, -0.740, -0.961],
                             [0.358, -0.577, -0.469]])
        weights_0.shape

    ## These weights are for the connection between the  hidden layer and the output
        weights_1 = np.array([[-0.017],
                             [-0.893],
                             [0.148]])
        weights_1.shape

    ## Epochs & Learning Rate
        epochs = 100
        learning_rate = 0.3
    ### for epoch in epochs:
        input_layer = inputs
        input_layer

    ## Computing the Sigmoid function for the Hidden layer
      hidden_layer = sigmoid(sum_synapse_0)
      hidden_layer
--

    # Dealing with the 2nd side
        weights_1

    ## "sum_synapse_1" This holds the sum function total of weights for the output layer
    ## For the Output: Each row holds the sum_func for each input data

        sum_synapse_1 = np.dot(hidden_layer, weights_1)
        sum_synapse_1
        output_layer = sigmoid(sum_synapse_1)
        output_layer

        outputs
        output_layer
        error_output_layer = outputs - output_layer
        error_output_layer
        average_error = np.mean(abs(error_output_layer))
        average_error

    ## Sigmoid Derivative
        def sigmoid_derivative(sigmoid):
              return sigmoid * (1 - sigmoid)
--

    # Delta output Calculation
    ## output_layer holds the results of our application of the sigmoid, computed above
        output_layer
    ## derivative_output is our Derivative of the activation function (sigmoid) which we have on the slide
    ## each row is for each instance of our input dataset
        derivative_output = sigmoid_derivative(output_layer)
        derivative_output
        error_output_layer
    
    # Delta output
    ## each row is for each instance of our input dataset
        delta_output = error_output_layer * derivative_output
        delta_output
    
    # Delta calculations for the Hidden Layer
        delta_output
        weights_1
        weights_1.shape
        weights_1T = weights_1.T
        weights_1T
        weights_1T.shape

    ## Each one of the weights will have to be multiplied by each delta_output for each data instance
        delta_output_x_weight = delta_output.dot(weights_1T)
        delta_output_x_weight
        hidden_layer

    # Each row in the output of delta_hidden_layer is for the data input values
        delta_hidden_layer = delta_output_x_weight * sigmoid_derivative(hidden_layer)
        delta_hidden_layer

    ## We will deal with the (input * delta) first
    # * The first column in "hidden_layer" holds  the activation value for the first neuron
        hidden_layer
        delta_output

    # * We need to multiply the "inputs" by "delta" however, for the matrix multiplication we need to transpose the values in the hidden_layer, so we have all of them on one row for each neuron
        hidden_layerT = hidden_layer.T
        hidden_layerT
        input_x_delta1 = hidden_layerT.dot(delta_output)
        input_x_delta1

    ## Let us now update the "weights_1"
        weights_1 = weights_1 + (input_x_delta1 * learning_rate)
        weights_1
--

    # Dealing with the Hidden Layer to Input Layer
    ## First column is X1, and 2nd column is X2 (our input values )
        input_layer
        delta_hidden_layer
    ## we need to transpose the values just as we did before
        input_layerT = input_layer.T
        input_layerT
        input_x_delta0 = input_layerT.dot(delta_hidden_layer)
        input_x_delta0
        weights_0 = weights_0 + (input_x_delta0 * learning_rate)
        weights_0

    ### So all the lines of code above, has allowed us to complete our first epoch. we will need to put all the code together so we can run multiple epochs
    # Complete Artificial Neural Network
    #Importing Numpy
        import numpy as np

    # This is the sigmoid Function
        def sigmoid(sum):
          return 1 / (1 + np.exp(-sum))

    #This is the sigmoid derivative as used before
        def sigmoid_derivative(sigmoid):
          return sigmoid * (1 - sigmoid)

    # Our input values
        inputs = np.array([[0,0],
                           [0,1],
                           [1,0],
                           [1,1]])
    # Our output values
        outputs = np.array([[0],
                            [1],
                            [1],
                            [0]])

--

    ### Initializing our weights with random values
      # * <b>Note:</b> Multiplying the random number by 2 and subtracting by 1, allows us to have a mix of both positive and negative random numbers for the weights
        weights_0 = 2 * np.random.random((2, 3)) - 1
        weights_1 = 2 * np.random.random((3, 1)) - 1

        epochs = 400000
        learning_rate = 0.6
        error = []

        for epoch in range(epochs):
          input_layer = inputs
          sum_synapse0 = np.dot(input_layer, weights_0)
          hidden_layer = sigmoid(sum_synapse0)

          sum_synapse1 = np.dot(hidden_layer, weights_1)
          output_layer = sigmoid(sum_synapse1)

          error_output_layer = outputs - output_layer
          average = np.mean(abs(error_output_layer))
   
    # print after every specified range of the value
          if epoch % 100000 == 0:
          print('Epoch: ' + str(epoch + 1) + ' Error: ' + str(average))
        error.append(average)
    
          derivative_output = sigmoid_derivative(output_layer)
          delta_output = error_output_layer * derivative_output

          weights1T = weights1.T #### WRONG CODE
          delta_output_weight = delta_output.dot(weights1T)
          delta_hidden_layer = delta_output_weight * sigmoid_derivative(hidden_layer)

          hidden_layerT = hidden_layer.T
          input_x_delta1 = hidden_layerT.dot(delta_output)
          weights_1 = weights_1 + (input_x_delta1 * learning_rate)

          input_layerT = input_layer.T
          input_x_delta0 = input_layerT.dot(delta_hidden_layer)
          weights_0 = weights_0 + (input_x_delta0 * learning_rate)

    #### At this point after runing for 1million epochs you can see the value is very low.
    # 1 million epochs with a learning rate of 0.3
        1 - 0.009670967930930745
    # after 400,000 epochs, with a learning rate of 0.6
        1- 0.008192022809586367
--

    # Let's visualize this result
        import matplotlib.pyplot as plt

        plt.xlabel('Number of Epochs')
        plt.ylabel('Error')
        plt.title('Plot showing results from Neural Network')
        plt.plot(error)
        plt.show()
        plt.xlabel('Number of Epochs')
        plt.ylabel('Error')
        plt.title('Plot showing results from Neural Network')
        plt.plot(error)
        plt.show()
    #### Compearing the outputs and the predictions
        outputs
        output_layer
    #### * We see that our neural network was able to get values close to the actual values from the results.
    #### * This shows that our neural network can handle the complexity of the XOR operator dataset.
    # * Let us see the updated weights. These are the weights we will require if we want to make future predictions
        weights_0
        weights_1
    # This function accepts an instance of a dataset

        def calculate_output(instance):
            #input to hidden layer
            hidden_layer = sigmoid(np.dot(instance, weights_0))
            #hidden to output layer
            output_layer = sigmoid(np.dot(hidden_layer, weights_1))
            return output_layer[0]
            round(calculate_output(np.array([0, 0])))
            round(calculate_output(np.array([0, 1])))
            round(calculate_output(np.array([1, 0])))
            round(calculate_output(np.array([1, 1])))

---
## Artefacts
---

<a href="https://colab.research.google.com/drive/1LFkaZpj5EFmm-Sh2G4h-UGuPpo95sA4y#scrollTo=lgXq0Hik3IA3" target="_blank">Google Colab - Eportfolio Activities - Machine Learning</a><br>

![image](/assets/images/banners/ML8-1.png)
![image](/assets/images/banners/ML8-2.png)
![image](/assets/images/banners/ML8-3.png)
![image](/assets/images/banners/ML8-4.png)
![image](/assets/images/banners/ML8-5.png)
![image](/assets/images/banners/ML8-6.png)
![image](/assets/images/banners/ML8-7.png)
![image](/assets/images/banners/ML8-8.png)
![image](/assets/images/banners/ML8-9.png)
![image](/assets/images/banners/ML8-10.png)
![image](/assets/images/banners/ML8-11.png)
![image](/assets/images/banners/ML8-12.png)
![image](/assets/images/banners/ML8-13.png)

---
## Personal Reflection
---

The perceptron activities provided an enriching experience that helped me dive deeper into the fundamentals of artificial neural networks. Working with simple perceptrons, AND operators, and multi-layer perceptrons allowed me to bridge the gap between theoretical concepts and their practical implementation. This journey reinforced my understanding of machine learning foundations while challenging me to apply logic and problem-solving skills.

Simple Perceptron
- The simple perceptron exercise was an excellent introduction to the building blocks of neural networks. Defining inputs, weights, and the sum function provided an intuitive understanding of how perceptrons compute outputs. The use of the step function as an activation mechanism was particularly insightful, as it demonstrated how simple rules can be applied to make binary decisions.

- The most interesting part was experimenting with different weights and observing how they influenced the perceptron’s output. It was fascinating to see how small changes in the weights shifted the decision boundary, reinforcing the importance of weight optimization in neural networks. Additionally, understanding the dot product’s role in efficiently calculating the sum function highlighted the mathematical elegance behind neural networks.

Perceptron as an AND Operator
- This activity showcased the perceptron’s ability to model logical operations, such as the AND operator. Designing the perceptron to classify inputs based on a specific logic gate helped me grasp how linear functions can solve simple problems. Implementing the training loop to adjust weights through an error-driven learning process was both challenging and rewarding.

- The iterative nature of the perceptron training algorithm, where weights were updated based on errors, reinforced my understanding of gradient-based learning. Observing the weights converge after multiple iterations emphasized how perceptrons learn to minimize error. It also deepened my appreciation for the role of learning rates, as I saw firsthand how different values affected the speed and accuracy of training.

- One limitation I noticed was that a single-layer perceptron could only model linearly separable problems, such as the AND gate. This realization prepared me for the next step: multi-layer perceptrons.

Multi-Layer Perceptron (MLP)
- The multi-layer perceptron exercise introduced the power of deep learning. It was exciting to see how MLPs, with their additional hidden layers, could handle more complex problems like the XOR operator, which cannot be solved by a single-layer perceptron. The use of the sigmoid function as an activation mechanism provided a smooth, continuous alternative to the step function, enabling the network to learn non-linear relationships.

- One of the most valuable aspects of this activity was understanding the forward and backward propagation processes. Calculating deltas for the output and hidden layers, and updating weights accordingly, demonstrated the mechanics of error propagation and weight optimization. This hands-on implementation helped demystify the concept of backpropagation, which often seems abstract in theory.

- The iterative improvement of the model over 400,000 epochs showed how MLPs gradually minimize error through repeated updates. Visualizing the error reduction over epochs reinforced the importance of proper training and patience in machine learning. Moreover, experimenting with different learning rates highlighted the delicate balance between convergence speed and stability.

Challenges and Insights
- Understanding Backpropagation: Backpropagation was initially challenging to grasp due to its iterative nature and multiple layers of calculations. However, breaking it down step-by-step—computing the error, applying the sigmoid derivative, and updating weights—clarified the process.

- Managing Complexity: Transitioning from simple perceptrons to MLPs added layers of complexity. Working with matrix multiplications for hidden layers and outputs required careful attention to detail, as even small mistakes in dimensions or calculations could lead to errors.

- Overfitting and Generalization: Observing the network’s performance on the XOR dataset made me realize the importance of training on diverse datasets to avoid overfitting. While the XOR task was successfully modeled, it highlighted the limitations of applying a trained model to unseen data without proper validation.

Key Learnings
- Role of Activation Functions: The transition from step functions to sigmoid functions demonstrated the importance of non-linearity in solving complex problems. Sigmoid’s continuous nature enables better error gradient calculations, paving the way for more flexible learning.

- Importance of Learning Rates: Experimenting with different learning rates emphasized their critical role in training efficiency. Too high a rate caused instability, while too low a rate slowed convergence.

- Iterative Improvement: Visualizing the reduction in error over epochs highlighted the iterative nature of neural network training and the patience required to achieve meaningful results.

- Scalability: The activities revealed how neural networks scale to handle increasingly complex tasks by adding more layers and neurons, showcasing their adaptability in diverse applications.

Impact on Professional Growth
- These activities enhanced my confidence in understanding and implementing neural networks from scratch. They strengthened my Python programming skills, particularly in matrix operations, loops, and mathematical computations. More importantly, I now have a solid foundation in perceptron-based learning, which will be invaluable as I explore advanced neural network architectures like convolutional and recurrent neural networks.

- The hands-on implementation of neural networks has also improved my problem-solving skills. Debugging errors during training and ensuring correct dimensionality in matrix operations were challenging but rewarding tasks that deepened my analytical thinking.

Moving Forward
- Building on this foundation, I plan to explore deeper neural networks with larger datasets and more complex architectures. I aim to experiment with modern activation functions, such as ReLU, and optimization techniques like Adam, to improve training efficiency. Additionally, I am excited to apply neural networks to real-world tasks, such as image classification or natural language processing, to see their practical impact.

In conclusion, the perceptron activities were a transformative learning experience. They bridged theoretical knowledge with practical implementation, enabling me to understand the building blocks of neural networks and their applications. These lessons will undoubtedly shape my future journey in machine learning and artificial intelligence.


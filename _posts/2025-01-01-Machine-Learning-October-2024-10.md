---
layout: post
title: UoE - Machine Learning October 2024 A - Gradient Cost Function
subtitle: Understand the applicability and challenges associated with different datasets for the use of machine learning algorithms.
categories: EL-Activities
tags: [UoE, coding, Module E-Portfolio Learning Activities]
---
---
## Gradient Cost Function
---

### Calculating cost with gradient descent and learning rate
- Change the iteration and learning rate vaules and see the impact on cost.
- Low iteration values with high learning rate (i.e. big steps) may lead to miss the global minimum
- Goal is to reach minimum cost with minimum iteration

        # Importing necessary libraries
            import pandas as pd
              import numpy as np

            def gradient_descent(x,y):
                m_curr = b_curr = 0
                iterations = 100       #change value
                n = len(x)
                learning_rate = 0.09   #change value

            for i in range(iterations):
                y_predicted = m_curr * x + b_curr
                cost = (1/n) * sum([val**2 for val in (y-y_predicted)])
                md = -(2/n)*sum(x*(y-y_predicted))
                bd = -(2/n)*sum(y-y_predicted)
                m_curr = m_curr - learning_rate * md
                b_curr = b_curr - learning_rate * bd
                print ("m {}, b {}, cost {} iteration {}".format(m_curr,b_curr,cost, i))

            x = np.array([1,2,3,4,5])
            y = np.array([5,7,9,11,13])

            gradient_descent(x,y)
--

    import numpy as np
    import matplotlib.pyplot as plt

    def gradient_descent(x, y):
      m_curr = b_curr = 0
      iterations = 100  # Change value
      n = len(x)
      learning_rate = 0.09  # Change value

    lt.figure(figsize=(10, 6))  # Set up the plot size
      for i in range(iterations):
       y_predicted = m_curr * x + b_curr
       cost = (1/n) * sum([val**2 for val in (y - y_predicted)])
       md = -(2/n) * sum(x * (y - y_predicted))
       bd = -(2/n) * sum(y - y_predicted)
       m_curr = m_curr - learning_rate * md
       b_curr = b_curr - learning_rate * bd

    # Print values for debugging
       print("m {}, b {}, cost {} iteration {}".format(m_curr, b_curr, cost, i))

    # Plot the line for every few iterations
       if i % 10 == 0:  # Plot every 10 iterations
          plt.scatter(x, y, color="red")  # Actual data points
          plt.plot(x, y_predicted, label=f"Iteration {i}")  # Line predicted by the model

    # Final plot adjustments
        plt.title("Gradient Descent Visualization")
        plt.xlabel("x")
        plt.ylabel("y")
        plt.legend()
        plt.show()

        x = np.array([1, 2, 3, 4, 5])
        y = np.array([5, 7, 9, 11, 13])
        gradient_descent(x, y)
--

        import numpy as np
        import matplotlib.pyplot as plt

        def gradient_descent(x, y):
            m_curr = b_curr = 0
            iterations = 100  # Change value
            n = len(x)
            learning_rate = 0.09  # Change value

    # Tracking cost and values of b for visualization
        cost_history = []
        b_history = []

    for i in range(iterations):
        y_predicted = m_curr * x + b_curr
        cost = (1/n) * sum([val**2 for val in (y - y_predicted)])
        md = -(2/n) * sum(x * (y - y_predicted))
        bd = -(2/n) * sum(y - y_predicted)

        # Update values
        m_curr = m_curr - learning_rate * md
        b_curr = b_curr - learning_rate * bd

        # Save values for visualization
        cost_history.append(cost)
        b_history.append(b_curr)

        print("m {}, b {}, cost {} iteration {}".format(m_curr, b_curr, cost, i))

    # Visualization
        visualize_gradient_descent(cost_history, b_history)

        def visualize_gradient_descent(cost_history, b_history):
            fig, axes = plt.subplots(1, 2, figsize=(12, 6))

    # Left Plot: Gradient Descent Steps with Cost vs b
        axes[0].plot(b_history, cost_history, 'r-o', label='Gradient Descent Path')
        for i in range(1, len(b_history)):
            axes[0].arrow(b_history[i-1], cost_history[i-1],
                      b_history[i] - b_history[i-1], cost_history[i] - cost_history[i-1],
                      head_width=0.05, head_length=0.05, color='brown')
            axes[0].set_xlabel('b')
            axes[0].set_ylabel('MSE (Cost)')
            axes[0].set_title('Gradient Descent Steps (Learning Rate Too High)')
            axes[0].legend()

    # Right Plot: Smooth Descent with Smaller Steps
        axes[1].plot(b_history, cost_history, 'r-o', label='Gradient Descent Path')
        axes[1].plot(b_history, cost_history, color='brown')  # Smooth Path
        for i in range(1, len(b_history)):
            axes[1].arrow(b_history[i-1], cost_history[i-1],
                      b_history[i] - b_history[i-1], cost_history[i] - cost_history[i-1],
                      head_width=0.05, head_length=0.05, color='brown')
            axes[1].set_xlabel('b')
            axes[1].set_ylabel('MSE (Cost)')
            axes[1].set_title('Gradient Descent Steps (Learning Rate Balanced)')
            axes[1].legend()

            plt.tight_layout()
            plt.show()

    # Input Data
        x = np.array([1, 2, 3, 4, 5])
        y = np.array([5, 7, 9, 11, 13])
        gradient_descent(x, y)

---
## Artefacts
---

<a href="https://colab.research.google.com/drive/1LFkaZpj5EFmm-Sh2G4h-UGuPpo95sA4y#scrollTo=lgXq0Hik3IA3" target="_blank">Google Colab - Eportfolio Activities - Machine Learning</a><br>

![image](/assets/images/banners/ML10-1.png)
![image](/assets/images/banners/ML10-2.png)
![image](/assets/images/banners/ML10-3.png)
![image](/assets/images/banners/ML10-4.png)
![image](/assets/images/banners/ML10-5.png)
![image](/assets/images/banners/ML10-6.png)

---
## Personal Reflection
---
Engaging with the gradient descent algorithm and visualizing its process was an enlightening experience that deepened my understanding of one of the fundamental concepts in machine learning. This exercise provided valuable insights into how optimization techniques work, the importance of hyperparameters like learning rates, and how visualization aids in interpreting algorithmic behavior.

Key Learnings from Gradient Descent
- The Iterative Nature of Gradient Descent
The step-by-step adjustment of parameters (m and b) to minimize the cost function demonstrated the iterative process behind gradient descent. Observing how each iteration reduced the cost (Mean Squared Error) provided a concrete understanding of how optimization algorithms move toward convergence. Watching the values stabilize toward the global minimum reinforced the idea that gradient descent is about gradual improvement rather than a direct solution.

Role of Learning Rate
- Experimenting with different learning rates was particularly insightful. With a low learning rate, the descent was slow, requiring more iterations to reach the minimum. On the other hand, a high learning rate caused the algorithm to overshoot, leading to unstable or divergent behavior. This hands-on exploration emphasized the importance of selecting an appropriate learning rate, balancing efficiency and accuracy.

Cost Function Visualization
- Visualizing the cost function over iterations was a breakthrough moment. It was fascinating to see how the cost decreased over time, forming a smooth downward curve when the learning rate was balanced. Tracking the changes in b alongside the cost provided a deeper understanding of how each parameter update contributes to the optimization process.

Gradient Descent with Visualization
- Plotting the gradient descent path with cost vs. parameter values offered a dynamic perspective on the algorithm’s progression. The arrow plots were particularly effective in showing the stepwise adjustments and the eventual stabilization as the algorithm approached the minimum. It underscored the practical use of visualization in diagnosing issues with the learning rate or convergence.

Challenges and Problem-Solving
- One of the initial challenges was understanding the impact of hyperparameters like iterations and learning rates. It took several attempts to find the right balance, especially when observing divergent behavior with high learning rates. This taught me to approach hyperparameter tuning systematically and to use visualization tools to diagnose and resolve issues.

- Another challenge was interpreting the relationship between m and b during the updates. Initially, it was difficult to connect how the gradients influenced parameter adjustments, but breaking the cost calculation into smaller steps clarified the mathematical intuition behind it.

Insights and Applications
- Importance of Visualization
This exercise reinforced how critical visualization is in machine learning workflows. Whether it’s monitoring the cost over iterations or visualizing gradient paths, these tools help diagnose problems, evaluate performance, and communicate results effectively.

Practical Relevance
- Gradient descent forms the backbone of many machine learning algorithms. Understanding its mechanics and challenges prepares me for real-world applications where optimization is key. For instance, tuning learning rates and iterations is a transferable skill for training neural networks or fine-tuning models in professional settings.

Iterative Learning Process
- The iterative nature of gradient descent mirrors the learning process itself. Each step builds on the previous one, refining the solution over time. This concept resonated with me personally, as it reminded me to approach challenges with patience and persistence.

Personal Growth and Takeaways
- This exercise significantly improved my technical skills in Python, particularly with libraries like NumPy and Matplotlib. Writing functions to implement gradient descent from scratch deepened my understanding of the underlying mathematics and how algorithms translate into code.

- On a broader level, this experience enhanced my analytical mindset. It taught me to break down complex problems into smaller, manageable steps and to focus on the iterative improvements that lead to better results. These lessons are applicable not just in machine learning but in any problem-solving scenario.

Moving Forward
- Moving forward, I plan to explore more advanced optimization techniques like stochastic gradient descent (SGD), momentum-based updates, and Adam optimization. Additionally, I aim to apply gradient descent to more complex datasets and use cases, such as multivariate regression or neural network training.

- Another area of interest is experimenting with adaptive learning rates and regularization techniques to address overfitting and convergence issues. These explorations will help me build a stronger foundation for tackling real-world machine learning challenges.

In conclusion, implementing and visualizing gradient descent was an invaluable learning experience. It not only deepened my understanding of a foundational algorithm in machine learning but also reinforced critical thinking and problem-solving skills. This exercise has laid a strong foundation for future explorations in optimization and machine learning.

---
layout: post
title: UoE - Machine Learning October 2024 A - Jaccard Coefficient Calculations
subtitle: Understand the applicability and challenges associated with different datasets for the use of machine learning algorithms.
categories: EL-Activities
tags: [UoE, coding, Module E-Portfolio Learning Activities]
---
---
## Jaccard Coefficient Calculations
---

![image](/assets/images/banners/ML6-1.png)

### Define data for individuals

    jack = {'Test-1': 'P', 'Test-2': 'N', 'Test-3': 'N', 'Test-4': 'A'}
    mary = {'Test-1': 'P', 'Test-2': 'A', 'Test-3': 'P', 'Test-4': 'N'}
    jim = {'Test-1': 'N', 'Test-2': 'N', 'Test-3': 'N', 'Test-4': 'A'}

### Function to calculate Jaccard coefficient

    def calculate_jaccard(person1, person2):
      intersection = 0
        union = 0
        for key in person1.keys():
            if person1[key] != 'A' or person2[key] != 'A':  # Include in the union if at least one result is valid
                union += 1
                if person1[key] == person2[key] and person1[key] != 'A':  # Count matches as intersection
                    intersection += 1
        return intersection / union if union > 0 else 0

### Recalculate Jaccard coefficients for each pair

    jack_mary_jaccard = calculate_jaccard(jack, mary)
    jack_jim_jaccard = calculate_jaccard(jack, jim)
    jim_mary_jaccard = calculate_jaccard(jim, mary)

    jack_mary_jaccard, jack_jim_jaccard, jim_mary_jaccard

---
## Artefacts
---

<a href="https://colab.research.google.com/drive/1LFkaZpj5EFmm-Sh2G4h-UGuPpo95sA4y#scrollTo=lgXq0Hik3IA3" target="_blank">Google Colab - Eportfolio Activities - Machine Learning</a><br>

![image](/assets/images/banners/ML6-2.png)

---
## Personal Reflection
---

Exploring the Jaccard coefficient for similarity analysis provided valuable insights into how to quantify relationships between data points based on shared attributes. This exercise helped me appreciate the practical use of similarity metrics in diverse applications, ranging from recommendation systems to clustering algorithms.

Understanding the Concept of Jaccard Coefficient
- The Jaccard coefficient, as a measure of similarity, calculates the ratio of shared attributes (intersection) to the total attributes considered (union). This simple yet effective metric became clearer as I implemented it in Python. By comparing pairs of individuals (Jack, Mary, and Jim), I could see firsthand how this coefficient highlights the level of agreement between their test outcomes, excluding ambiguous results (A).

Insights Gained from Implementation
- Implementing the calculate_jaccard function allowed me to delve deeper into the practical challenges of similarity measurement. The step to exclude ambiguous results from the intersection while still considering them in the union required careful logic, reinforcing the importance of handling data irregularities. It also demonstrated how small variations in logic can significantly impact the outcome of similarity metrics.

- For example:
  - Jack and Mary had a higher similarity because their test outcomes aligned more closely.
  - Jim and Jack, on the other hand, exhibited lower similarity due to significant differences in their responses.
  - The similarity between Jim and Mary was also minimal, highlighting the dissimilarity in their test results.
  - These outcomes revealed how sensitive the Jaccard coefficient is to the nature of the data, emphasizing the importance of understanding the context of the dataset.

Challenges and Problem-Solving
- One of the key challenges was ensuring the logic of the function correctly accounted for ambiguous results (A). Initially, I found it tricky to determine whether ambiguous results should be entirely excluded from the union or only ignored for the intersection. This step helped me refine my problem-solving approach and underscored the importance of data preprocessing in analysis.

- Another challenge was interpreting the numerical results of the Jaccard coefficient in a meaningful way. Understanding that the coefficient ranges from 0 (completely dissimilar) to 1 (identical) required me to think critically about how small differences in the dataset affect the similarity score.

Broader Reflections on Similarity Metrics
- This exercise highlighted the versatility and importance of similarity metrics like the Jaccard coefficient in real-world applications. Whether it’s measuring the overlap in user preferences for recommendation systems or analyzing relationships in survey responses, the ability to quantify similarity is a fundamental skill in data science.

- It also reinforced the importance of tailoring similarity metrics to the problem at hand. For instance, while the Jaccard coefficient worked well in this case, other datasets might benefit more from metrics like cosine similarity or Euclidean distance, depending on their characteristics.

Professional Growth
- This activity improved my ability to implement mathematical concepts programmatically and interpret their results in practical scenarios. Writing the Jaccard coefficient function enhanced my Python coding skills, particularly in handling dictionaries and designing custom logic for specific use cases.

- Moreover, this exercise deepened my understanding of how similarity metrics can inform decision-making in fields like clustering, classification, and even natural language processing. These skills will undoubtedly be valuable in my professional development as I tackle more complex data science problems.

Moving Forward
- Moving forward, I aim to explore other similarity metrics and their applications, particularly in larger and more complex datasets. Additionally, I plan to investigate techniques for combining similarity metrics with machine learning algorithms to improve clustering and recommendation systems.

In conclusion, calculating and interpreting the Jaccard coefficient for similarity analysis was a rewarding experience that enhanced my technical and analytical skills. This hands-on exercise not only deepened my understanding of similarity metrics but also provided a solid foundation for applying these concepts to real-world data challenges.

---
layout: post
title: UoE - Research Methods and Professional Practice April 2025 - Research Proposal Presentation
subtitle: The 2 core types of reasoning are Deductive and Inductive reasoning.
categories: EL-Activities
tags: [UoE, Refection, Module E-Portfolio Learning Activities]
---
# Detecting Political Misinformation on Twitter Using NLP-Based Models: A Critical Analysis of Methodologies, Ethics, and Efficacy
---
## Presentation

![image](/assets/images/banners/RM10-1a.png)
![image](/assets/images/banners/RM10-2a.png)

In the digital age, social media platforms like Twitter have become central channels for communication, marketing, public relations, and information dissemination. Businesses, government agencies, and the general public rely heavily on these platforms for timely information, opinion shaping, and decision-making. However, the proliferation of political misinformation on platforms such as Twitter presents severe risks and challenges. Political misinformation can lead to public confusion, erosion of trust in institutions, polarization, and even adverse business consequences, including reputational damage and financial loss.

From a business perspective, misinformation undermines brand integrity, disrupts market dynamics, and impacts stakeholder confidence. For instance, misinformation campaigns have previously damaged corporate reputations, led to consumer boycotts, and influenced market behavior negatively. Additionally, misinformation challenges regulatory compliance, especially in sensitive sectors such as finance, healthcare, and technology, where accuracy and trust are paramount.

The decision to focus this research on detecting political misinformation using NLP-based models is driven by these critical issues. It addresses a pressing need for businesses and institutions to proactively manage misinformation risks and safeguard credibility. Furthermore, examining and enhancing NLP methodologies for misinformation detection aligns with broader industry trends toward ethical artificial intelligence, corporate responsibility, and transparency in digital interactions.

This research thus aims not only at improving technological capabilities in misinformation detection but also contributes significantly to strategic business practices, regulatory compliance, ethical standards, and overall public trust in digital communication platforms.

![image](/assets/images/banners/RM10-3a.png)

The proliferation of misinformation on Twitter represents a critical societal problem. Existing detection systems often prioritize technical accuracy over ethical considerations, such as bias mitigation and transparency. 

My research will address this gap by critically evaluating and comparing NLP methodologies. It will contribute academically by elucidating conflicts within existing research and practically by providing guidelines and tools for ethically sound misinformation detection

![image](/assets/images/banners/RM10-4a.png)

The central question guiding this research is:
- "How can NLP-based models be effectively and ethically employed to detect political misinformation on Twitter, and in what ways do current methodologies differ regarding accuracy, transparency, and bias mitigation?"

To answer this question, the research objectives include:
-	Conducting a comprehensive literature review of existing NLP-based misinformation detection methodologies.
-	Implementing and critically evaluating multiple NLP models, focusing on accuracy, fairness, and interpretability.
-	Identifying theoretical tensions and conflicts within the existing literature.
-	Proposing ethical guidelines and best practices for future implementations of NLP-based misinformation detection..

![image](/assets/images/banners/RM10-5a.png)

When we look at the existing literature, we find a number of very different, and sometimes even conflicting, perspectives on how best to detect political misinformation:

-	For example, **Zhou and colleagues in 2020** show us that deep learning approaches like BERT deliver exceptionally high accuracy. But they also warn that these models often operate as “black-boxes,” lacking both transparency in how they arrive at their decisions and the ability to generalize reliably to new domains.

-	By contrast, **Shu and co-authors in 2019** propose hybrid methods that combine textual content with metadata, things like retweet patterns or user profiles, to boost detection performance. They achieve strong results, but they admit that these more complex systems can be difficult to deploy in real time.

-	Then we have **Klein and Wueller’s analysis from 2017**, which doesn’t focus on technical performance at all, but instead raises deep ethical red flags. They remind us that automatically labeling political statements as “false” can edge into censorship territory and carries profound implications for free speech.

-	**Vlachos and Riedel, writing in 2014**, highlight a different concern: the very process of building fact-checking datasets can introduce circular biases. If your training data come from the same limited set of fact-checkers or news sources, your model may learn and reinforce their blind spots.

-	And more recently, **Zellers and colleagues in 2019** added yet another twist: the same generative models, like the GPT series, that we can use to detect fake news are also powerful enough to create highly persuasive misinformation themselves, creating an arms race between content generation and detection.

My project will bring all of these viewpoints into conversation. Rather than simply choosing one “best” method, I will compare their underlying philosophical assumptions about truth, examine their ethical trade-offs, and test their practical strengths and weaknesses on the same Twitter data. This combination of technical evaluation and theoretical critique is at the heart of my research.

![image](/assets/images/banners/RM10-6a.png)
![image](/assets/images/banners/RM10-7a.png)

In order to answer our research question, I’m using a mixed-methods design that blends both quantitative modeling and qualitative interpretation. 
-	First, I’ll gather publicly available Twitter datasets such as CoAID and PHEME, then clean the text using standard NLP steps (tokenization, lemmatization, and stop-word removal) and transform this into features via TF-IDF, Word2Vec, and BERT embeddings.

  -	A baseline logistic regression, a random forest to give us more interpretable feature insights.
  -	A fine-tuned BERT transformer for deeper semantic understanding.
  -	I’ll evaluate each model quantitatively using accuracy, precision, recall, and F1-score, alongside confusion matrices and ROC-AUC curves to compare their overall performance.

-	Beyond pure performance, I’ll assess bias and fairness by running statistical disparity tests across different demographic and political groups. To open up the ‘black-box’ models, I’ll apply SHAP and LIME explanations so we can see which words or features drove each prediction. 

-	Finally, I’ll dive into the cases where the models fail, analyzing misclassifications in detail so we can understand the underlying patterns or blind spots. This combination of numerical rigor and case-by-case analysis will give us a holistic view of how these NLP methods work in practice.

![image](/assets/images/banners/RM10-8a.png)

Addressing ethics and managing risk is a core component of this project. 
-	First, in terms of data privacy, we will fully comply with GDPR and other relevant data protection regulations, and we’ll ensure that all user identifiers are anonymized before analysis.
-	When it comes to truth labeling, we recognize that determining political truth is inherently subjective. To address this, we’ll adopt a probabilistic labeling framework that captures uncertainty rather than forcing a binary true-or-false decision.
-	For bias mitigation, we’ll incorporate fairness-aware training techniques into our models and continuously monitor for disparities in performance across different demographic and political groups.
-	Finally, we’re committed to transparency and accountability: every step of the modeling process will be documented in detail, and we’ll produce ethical audit reports that outline each model’s capabilities, limitations, and any residual risks. This ensures stakeholders can trust not only our results but our entire research journey.

![image](/assets/images/banners/RM10-9a.png)

-	The final output of this research will be an intuitive, interactive tool, either a web-based dashboard or a Jupyter notebook interface, which is designed for real-time exploration. Users will be able to paste or upload tweets and immediately see whether each one is classified as misinformation. 
-	We’ll show side-by-side results from our three models (logistic regression, random forest, and a BERT transformer) so users can compare performance at a glance.
-	To demystify the models, we’ll integrate SHAP and LIME visualizations, letting users hover or click to see exactly which words or features influenced a given prediction. 
-	Beyond that, the dashboard will include clear, user-friendly charts that summarize fairness metrics and any biases detected across demographic or political groups. 
-	And because stakeholders often need to report results, we’ll provide exportable summaries that cover both model performance and ethical accountability, ensuring everyone can review and share the findings with confidence

![image](/assets/images/banners/RM10-10a.png)

We’ll conduct this project over twelve weeks, organized around clear milestones. 
-	During weeks 1 - 2, I’ll wrap up the literature review, acquire the Twitter datasets, and validate their quality. 
-	In weeks 3 - 4, I’ll focus on data preprocessing (cleaning and embedding the text) and set up the baseline logistic regression model.
-	Moving into weeks 5 - 6, I’ll implement the more advanced models, including the random forest and the BERT transformer, and begin their initial training. 
-	Week 7 is dedicated to a comprehensive evaluation, where I’ll assess performance metrics, run fairness audits, and generate interpretability analyses.
-	In week 8, I’ll shift to artefact development, designing and building the first prototype of our interactive dashboard or notebook. 
-	Weeks 9 - 10 will be spent on detailed critical comparisons, aligning our findings with the literature, and on deeper ethical evaluations.
-	Finally, during weeks 11 - 12, I’ll write the final report, prepare the presentation materials, and integrate any feedback from stakeholders or peers.
This structured timeline ensures steady progress and leaves room for iteration based on interim results.

![image](/assets/images/banners/RM10-11a.png)

While this research presents substantial benefits, it also has several limitations that should be considered:

-	**Dataset Constraints**: We rely on publicly available datasets like CoAID and PHEME, which may themselves carry biases or be limited in scope. That means our findings might not generalize perfectly to other contexts or newer data.

-	**Model Generalizability**: while transformer-based models such as BERT deliver impressive accuracy, they can be highly context- or language-specific. To apply them in different regions or on other platforms, we would likely need to retrain or fine-tune these models substantially.

-	**Subjectivity in Labeling**: labeling political content as ‘misinformation’ is inherently subjective. Different fact-checkers or audiences might disagree, and those subjective judgments can introduce biases that affect both our model’s performance and how we interpret the results.

-	**Real-time Deployment Challenges**: deploying these NLP models in real-time on a fast-paced platform like Twitter presents serious computational and logistical challenges. Ensuring low-latency, high-throughput predictions in production would require additional engineering work beyond what we cover in this research.

-	**Ethical and Privacy Concerns**: despite strict data privacy and ethical safeguards, we must remain vigilant about ongoing privacy and consent issues—particularly when dealing with politically sensitive content. Ethical standards evolve, and continuous oversight will be needed to keep our methods and artefacts responsibly aligned with best practices.

Acknowledging these limitations helps us interpret our results with caution and points the way for future research to improve robustness, fairness, and applicability.

This research seeks to critically bridge technical capabilities with ethical responsibilities in political misinformation detection on Twitter. By rigorously evaluating NLP methodologies, addressing ethical complexities, and creating practical tools, it aims to significantly advance both theoretical understanding and practical solutions

![image](/assets/images/banners/RM10-13a.png)

As we conclude this activity, I’d like to reflect on the key learnings acquired throughout this process:

-	Enhanced Critical Thinking: Engaging deeply with conflicting literature and methodologies significantly sharpened my ability to critically analyze and synthesize complex arguments, identifying not only strengths but also potential biases and limitations.

-	Research Methodology Skills: Developing a mixed-method research design improved my understanding of how quantitative and qualitative analyses complement each other, providing richer insights than either method alone.

-	Ethical Awareness: Exploring ethical considerations around misinformation detection heightened my sensitivity to issues such as data privacy, labeling biases, and algorithmic fairness, emphasizing the importance of responsible AI use.

-	Technical Proficiency: The hands-on process of selecting NLP models and evaluation methods expanded my technical expertise, especially in areas like model interpretability and bias analysis, strengthening my capability to manage practical data-driven tasks.

-	Time and Project Management: Crafting a detailed project timeline enhanced my ability to manage tasks effectively, highlighting the importance of structured planning and milestone setting in successful research execution.

These takeaways represent substantial growth areas for me, preparing me better for future academic research, professional projects, and continuous personal development.

![image](/assets/images/banners/RM10-12a.png)

---
## Artefacts
---
Tutor Feedback

![image](/assets/images/banners/RM10-14.png)
![image](/assets/images/banners/RM10-15.png)

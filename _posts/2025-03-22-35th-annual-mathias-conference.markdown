---
layout: post
title:  Presenting My Research at the 35th Annual Mathias Conference
description: Translating data science into impact, this presentation explored bias in mortgage lending during the COVID-19 pandemic through machine learning. From tackling class imbalance to evaluating model fairness, the project highlighted how technical rigor and social relevance intersect. Engaging with a vibrant academic community, the experience sharpened my communication skills and reinforced the power of data-driven storytelling.
date:   2025-03-22 20:01:35 +0300
image:  '/post_images/cover_images/mathias_student_reference_generated.png'
tags:   [research, mortgage lending, machine learning, story]
---

Earlier this month, I had the opportunity to present my research at the 35th Annual Robyn Rafferty Mathias Research Conference at American University. As one of nearly 200 undergraduate and graduate students in the College of Arts and Sciences, it was an exciting experience to showcase my work and engage with faculty, peers, and guests about a topic I’ve been deeply invested in throughout my Data Science program.

<div class="gallery-box">
  <div class="gallery">
    <img src="/hilton_website/post_images/mathias_conference/mathias_solo_shot.jpeg" loading="lazy">
  </div>
  <em>Gallery / <a href="https://unsplash.com/" target="_blank">Unsplash</a></em>
</div>

*What’s this topic, you may ask?*

My poster, titled “Assessing Bias in Mortgage Lending and Payment Trends During the COVID-19 Pandemic in the United States Using Machine Learning,” examined how socio-economic and demographic factors influenced mortgage delinquency risk between 2020 and 2022.
The COVID-19 pandemic reshaped the U.S. housing market in profound ways, especially for first-time homebuyers and communities that were already financially vulnerable. So, I wanted to explore not only how borrower characteristics affected delinquency outcomes but also whether there was any evidence of systemic bias in lending practices during this period.

*How could I do this?*

I worked with publicly available data from the Federal Home Loan Bank (FHL Bank), which includes detailed information on borrower demographics, credit profiles, and loan characteristics. I developed a binary classification task to categorize borrowers as either high-risk or low-risk based on their Total Debt Expense. 

However, the dataset was highly imbalanced—there were significantly fewer high-risk borrowers—so I applied a range of techniques to address this issue, including SMOTE and Tomek Links for oversampling and cleaning, as well as class weighting strategies to ensure that my models could learn from both classes effectively.

I built four machine learning models—Logistic Regression, Decision Trees, Random Forest, and LightGBM—and evaluated their performance on this classification task.

Additionally, I tested the models with and without Principal Component Analysis (PCA) to examine how dimensionality reduction might affect predictive performance and fairness.

One of the key findings from my research was that Random Forest and LightGBM outperformed the other models, both achieving ROC-AUC scores around 0.83. 

The most important predictors across models were Housing Expense Ratio, Credit Score, and Loan-to-Value Ratio, highlighting the central role that financial attributes play in mortgage risk assessment. 

Interestingly, demographic variables had lower feature importance, which might suggest limited predictive power—but this does not necessarily rule out the presence of systemic bias. In fact, one of the more surprising outcomes was that PCA, while useful for reducing dimensionality, actually reduced the model’s ability to detect high-risk borrowers among minority groups. This raises important questions about fairness in data preprocessing and model design.

What I found most rewarding about this project wasn’t just the technical implementation, but the broader implications it touched on. The models suggest that financial indicators are the most predictive of delinquency, yet the potential for algorithmic bias remains, especially when minority representation in the data is limited or masked through dimensionality reduction. 

As I continue to develop my skills in data science, I’m eager to explore fairness-aware machine learning algorithms and evaluate the trade-offs that come with handling imbalanced data, especially in high-stakes contexts like housing and finance.

Presenting this research gave me a chance to reflect on how far I’ve come in my graduate studies and how much I’ve learned by applying classroom concepts to real-world issues. It was also a reminder of the importance of interdisciplinary conversations—many of the best questions I received came from people outside my immediate field, which helped me think more critically about the social dimensions of technical work.

![Poster Presentation]({{site.baseurl}}/portfolio_images/mg_supervised_ml_images/Assessing Bias in Mortgage lending_completed_image.png#wide)

Thank you to everyone who stopped by my poster and engaged in thoughtful discussion. I’m excited to keep exploring the intersection of machine learning, fairness, and economic policy—and I’m always happy to connect with others working on similar challenges. If you’ve worked with fairness-aware algorithms or have experience dealing with class imbalance in real-world datasets, I’d love to hear your story.

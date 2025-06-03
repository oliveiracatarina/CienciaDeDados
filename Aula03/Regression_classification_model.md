# **Aula 03: Regression and Classification Models**

These two pillars form the bedrock of supervised learning, enabling us to make predictions and extract valuable insights from data. We will also explore a wide array of real-world applications (use cases) where these models shine, discuss fundamental concepts of learning algorithms, and dive into the mechanics of the Decision Tree Algorithm.

### **1\. Regression and Classification Models**

At the heart of supervised machine learning are two primary types of predictive modeling:

* Regression: Regression models are used to predict a continuous numerical value. The output is a number, such as temperature, price, age, or sales figures. The goal is to establish a relationship between independent variables (features) and a dependent variable (target).

  * Example: Predicting the price of a house based on its size, number of bedrooms, and location.  
* Classification: Classification models are used to predict a categorical label or class. The output is a discrete value, indicating which category an input belongs to.

  * Binary Classification: Predicts one of two classes (e.g., "yes" or "no", "true" or "false", "spam" or "not spam").  
  * Multi-class Classification: Predicts one of more than two classes (e.g., "cat", "dog", or "bird"; classifying types of diseases).  
  * Example: Identifying whether an email is spam or not spam; categorizing customer feedback as positive, negative, or neutral.

The choice between regression and classification depends entirely on the nature of your target variable. If it's a quantity you measure, it's regression. If it's a category you assign, it's classification.

### **2\. Real-world Use Cases**

Regression and Classification models are pervasive across various industries, driving data-driven decision-making. Let's explore some key applications:

* Churn Prediction (Classification):

  * Description: Predicting which customers are likely to stop using a service or product (churn).  
  * Data: Customer demographics, usage patterns, service history, complaints.  
  * Outcome: Binary classification (churn/no churn) or multi-class (different types of churn).  
  * Impact: Enables businesses to proactively engage at-risk customers with retention strategies (e.g., special offers, personalized support), reducing customer attrition and increasing customer lifetime value.  
* Customer Segmentation (Often Unsupervised, but also Supervised Classification):

  * Description: Dividing a customer base into distinct groups based on shared characteristics, behaviors, or needs. While often done with unsupervised methods like clustering, it can also involve supervised classification if segments are predefined.  
  * Data: Purchase history, Browse behavior, demographics, preferences.  
  * Outcome: Categorical labels representing different customer segments (e.g., "high-value shoppers", "bargain hunters", "new customers").  
  * Impact: Allows for targeted marketing campaigns, personalized product recommendations, and tailored customer service, leading to increased engagement and1 sales.  
* Risk Assessment (Classification/Regression):

  * Description: Evaluating the likelihood of a negative event occurring or quantifying the potential impact.  
  * Data: Financial history, credit scores, health records, demographic information.  
  * Outcome:  
    * Classification: Predicting the likelihood of loan default (high/medium/low risk), disease presence (diseased/healthy).  
    * Regression: Quantifying the potential financial loss from a specific risk event.  
  * Impact: Crucial in finance (credit scoring, insurance underwriting), healthcare (patient risk stratification), and security, enabling informed decision-making to mitigate potential losses.  
* Demand Prediction (Regression):

  * Description: Forecasting the future demand for a product or service.  
  * Data: Historical sales data, promotional activities, economic indicators, seasonality, weather.  
  * Outcome: Continuous numerical value (e.g., number of units expected to be sold, expected call volume).  
  * Impact: Optimizes inventory management, production planning, staffing levels, and supply chain logistics, minimizing waste and ensuring product availability.  
* Recommendation Engines / Market Basket Analysis (Classification/Association Rules):

  * Description:  
    * Recommendation Engines: Suggesting items to users based on their preferences or past behavior. Can involve predicting ratings (regression) or whether a user will like an item (classification).  
    * Market Basket Analysis: Discovering associations between items purchased together (e.g., "customers who buy bread also buy milk").  
  * Data: User ratings, purchase history, Browse data, item characteristics.  
  * Outcome:  
    * Recommendation Engines: List of recommended items, predicted ratings for items.  
    * Market Basket Analysis: Association rules (e.g., "if A then B").  
  * Impact: Enhances user experience, increases cross-selling and up-selling opportunities, and boosts sales for e-commerce platforms and streaming services.  
* Fraud Detection (Classification):

  * Description: Identifying fraudulent transactions or activities.  
  * Data: Transaction details (amount, location, time), user behavior, account history.  
  * Outcome: Binary classification (fraudulent/legitimate).  
  * Impact: Prevents financial losses for banks, e-commerce companies, and insurance providers by flagging suspicious activities in real-time or near real-time.  
* Sentiment Analysis (Classification):

  * Description: Determining the emotional tone or opinion expressed in text data.  
  * Data: Customer reviews, social media posts, news articles, survey responses.  
  * Outcome: Categorical labels (e.g., positive, negative, neutral; or specific emotions like joy, anger).  
  * Impact: Helps businesses understand customer perception of products/services, monitor brand reputation, and gain insights from public opinion, informing marketing and product development.  
* Anomaly Detection (Classification/Unsupervised):

  * Description: Identifying rare occurrences or outliers that deviate significantly from the norm. Can be supervised if anomalies are labeled, or unsupervised otherwise.  
  * Data: Network traffic logs, sensor readings, credit card transactions, machine performance data.  
  * Outcome: Binary classification (normal/anomaly) or anomaly score.  
  * Impact: Crucial for cybersecurity (detecting intrusions), financial crime (unusual transactions), manufacturing (fault detection), and healthcare (identifying unusual patient readings), preventing damage or failure.

### **3\. Basic Concepts of Learning Algorithms**

Before diving into specific algorithms, let's establish some fundamental concepts:

#### **What is a Learning Algorithm?**

A learning algorithm is a set of rules and statistical procedures that a computer program uses to learn from data without being explicitly programmed for every specific task. Instead of providing precise instructions for every possible scenario, we provide the algorithm with data and a goal, and it learns to perform the task by finding patterns and relationships within that data. The "learning" part refers to the algorithm's ability to adjust its internal parameters or structure based on the data it processes, improving its performance over time.

#### **Algorithm Training / Learning**

The process by which a learning algorithm acquires knowledge from data is called training or learning. This process varies depending on the type of learning paradigm:

* Supervised Learning:

  * Concept: The algorithm learns from a labeled dataset, meaning each data point has both input features and a corresponding "correct" output (label). The algorithm's goal is to learn a mapping function from the inputs to the outputs.  
  * How it works: The algorithm is fed input data and its associated correct output. It makes predictions, compares them to the true outputs, and adjusts its internal parameters to minimize the error.  
  * Analogy: Learning with a teacher who provides corrected answers.  
  * Examples: Regression (predicting continuous values like house prices) and Classification (predicting discrete labels like spam/not-spam).  
  * Role of Data: High-quality, accurately labeled data is crucial.  
* Unsupervised Learning:

  * Concept: The algorithm learns from an unlabeled dataset, meaning there are no predefined output labels. The algorithm's goal is to discover hidden patterns, structures, or relationships within the data itself.  
  * How it works: It groups similar data points together, identifies underlying dimensions, or finds rules governing the data without any external guidance.  
  * Analogy: Learning by observation and finding patterns on your own.  
  * Examples:  
    * Clustering: Grouping similar data points together (e.g., customer segmentation).  
    * Dimensionality Reduction: Reducing the number of features while retaining important information (e.g.,2 PCA).  
    * Association Rule Mining: Finding relationships between items (e.g., Market Basket Analysis).  
  * Role of Data: Can work with raw, unlabeled data, often used for exploratory data analysis or preprocessing for supervised tasks.  
* Semi-Supervised Learning:

  * Concept: A hybrid approach that uses a small amount of labeled data combined with a large amount of unlabeled data for training.  
  * How it works: The algorithm leverages the patterns learned from the labeled data to make sense of the unlabeled data, or uses the unlabeled data to refine the understanding gained from the labeled subset. It's particularly useful when labeling data is expensive or time-consuming.  
  * Analogy: A student who gets some direct instructions but mostly learns by observing and inferring.  
  * Examples: Image recognition (only a few images are fully labeled), web page classification.  
* Reinforcement Learning (Aprendizado por Reforço):

  * Concept: An agent learns to make decisions by performing actions in an environment to maximize a cumulative reward. There's no labeled dataset; instead, the agent receives feedback (rewards or penalties) based on its actions.  
  * How it works: The agent learns through trial and error. It explores different actions, observes the consequences (state changes and rewards), and develops a policy (strategy) that dictates the best action to take in a given state.  
  * Analogy: Training a pet with treats for desired behaviors.  
  * Examples: Game playing (AlphaGo), robotics, autonomous driving, resource management.  
  * Key Components: Agent, Environment, States, Actions, Rewards, Policy.  
* Self-Supervised Learning:

  * Concept: A new paradigm within unsupervised learning where the learning algorithm generates its own labels from the input data. It creates a "pretext task" where the input data contains the supervision signal.  
  * How it works: Instead of relying on human-provided labels, the model learns by solving an auxiliary task where the labels are automatically derived from the data itself. Once trained on the pretext task, the learned representations can then be used for a downstream supervised task.  
  * Analogy: A puzzle where you create the "rules" of the puzzle from the puzzle pieces themselves.  
  * Examples: Predicting missing words in a sentence (BERT), predicting the next frame in a video, image colorization (predicting colors from grayscale).  
  * Impact: Highly effective for pre-training large models when labeled data is scarce, then fine-tuning them on specific supervised tasks. This is a rapidly evolving field, especially in natural language processing (NLP) and computer vision.

### **4\. Decision Tree Algorithm**

The Decision Tree Algorithm is a popular and intuitive supervised learning method that can be used for both classification and regression tasks. It models decisions by creating a tree-like structure, where each internal node represents a "test" on an attribute, each branch represents the outcome of the test, and3 each leaf node represents a class label (in classification) or a numerical value (in regression).

#### **How it Works:**

1. Root Node: The tree starts with a single root node, representing the entire dataset.  
2. Splitting: The algorithm recursively splits the data into subsets based on the values of input features. At each node, it selects the "best" feature and a corresponding threshold to split the data. The "best" split is determined by a criterion that aims to maximize the homogeneity (purity) of the target variable within the resulting child nodes.  
   * For Classification:  
     * Gini Impurity: Measures the probability of misclassifying a randomly chosen element in the dataset if it were randomly labeled according to the distribution of labels in the node. A lower Gini impurity indicates higher purity.  
     * Information Gain (Entropy): Entropy measures the disorder or uncertainty in a set of labels. Information Gain is the reduction in entropy achieved after a split. The algorithm seeks to maximize information gain.  
   * For Regression:  
     * Mean Squared Error (MSE): Measures the average squared difference between actual and predicted values. The goal is to minimize the MSE within each child node.  
     * Mean Absolute Error (MAE): Measures the average absolute difference.  
3. Recursive Process: This splitting process continues recursively for each new node until:  
   * All data points in a node belong to the same class (for classification) or have a similar value (for regression).  
   * A predefined stopping criterion is met (e.g., maximum tree depth, minimum number of samples per leaf, minimum impurity decrease).  
4. Leaf Nodes: Once the splitting stops, the final nodes are called leaf nodes.  
   * For Classification: Each leaf node represents a class label (the majority class in that node) or a probability distribution over the classes.  
   * For Regression: Each leaf node represents a predicted numerical value (e.g., the average of the target values in that node).

#### **Advantages of Decision Trees:**

* Simple to Understand and Interpret: The tree structure is highly intuitive and can be visualized, making it easy to explain how decisions are made.  
* Handle Both Numerical and Categorical Data: They can directly handle different types of feature data.  
* Require Little Data Preparation: They don't typically require feature scaling or normalization.  
* Non-linear Relationships: Can capture complex non-linear relationships between features and the target variable.

#### **Disadvantages of Decision Trees:**

* Prone to Overfitting: Without proper pruning or hyperparameter tuning, decision trees can easily become too complex, learning the noise in the training data and performing poorly on unseen data.  
* Instability (High Variance): Small changes in the training data can lead to significantly different tree structures, making them unstable.  
* Bias towards Dominant Classes: In imbalanced datasets, they can be biased towards the majority class.  
* Local Optima: The greedy approach of selecting the best split at each step might not lead to a globally optimal tree.

#### **Overcoming Disadvantages:**

Many of the disadvantages, particularly overfitting and instability, are addressed by ensemble methods that combine multiple decision trees, such as Random Forest (which we will discuss in future lectures) and Gradient Boosting. These methods leverage the strengths of individual trees while mitigating their weaknesses, leading to more robust and accurate models.


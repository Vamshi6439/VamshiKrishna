# Customer Sentiment Analysis and Satisfaction Prediction from Support Tickets
Project Overview

The primary objective of this project is to predict customer satisfaction using the historical data contained within the Customer Support Ticket Dataset. This will be achieved by applying machine learning algorithms to analyze the various factors and features present in the ticket information that have an influence on how satisfied a customer is with the support they receive. The ultimate goal is to build a predictive model capable of estimating customer satisfaction levels based on the characteristics of their support interaction.

About Dataset
The Customer Support Ticket Dataset contains records of customer inquiries related to tech products, covering issues like hardware, software bugs, network problems, account access, and data loss. It includes details about the customer (name, email - anonymized domain, age, gender), the product purchased, the purchase date, and specifics of the support ticket (type, subject, description, status, resolution, priority, channel). Crucially, for closed tickets, it also provides the first response time, time to resolution, and the customer satisfaction rating (on a scale of 1 to 5). This dataset is suitable for analyzing support trends, applying Natural Language Processing to ticket text, predicting customer satisfaction and resolution times, segmenting customers, and building recommendation systems for support resources.

Features Description:

Ticket ID: A unique identifier for each individual support ticket.

Customer Name: The name of the customer who submitted the ticket.

Customer Email: The customer's email address (domain anonymized for privacy).

Customer Age: The age of the customer.

Customer Gender: The gender of the customer.

Product Purchased: The specific tech product the customer bought.

Date of Purchase: The date when the customer purchased the product.

Ticket Type: The broad category of the support request (e.g., technical issue).

Ticket Subject: A brief summary or topic of the customer's ticket.

Ticket Description: A more detailed explanation of the customer's problem or question.

Ticket Status: The current state of the ticket (e.g., open, closed).

Resolution: The solution or action taken to close the ticket.

Ticket Priority: The assigned level of urgency for the ticket.

Ticket Channel: How the customer contacted support (e.g., email, chat).

First Response Time: The duration until the initial response was sent to the customer.

Time to Resolution: The total time taken to resolve the ticket.

Customer Satisfaction Rating: The customer's feedback on their satisfaction with the resolution (1-5 scale).

Use Cases of such dataset:

Customer Support Analysis: This allows for data-driven improvements to support operations by understanding what issues are most frequent, how efficiently they are handled, and where processes can be optimized.

Natural Language Processing (NLP): Leveraging the text data (subject and description) can lead to automation and deeper understanding of customer needs and sentiments at scale.

Customer Satisfaction Prediction: Proactively identifying customers likely to be dissatisfied enables timely interventions and can improve overall customer loyalty.

Ticket Resolution Time Prediction: Accurate predictions can help manage customer expectations, allocate resources effectively, and potentially identify tickets that might require escalation.

Customer Segmentation: Understanding different customer groups based on their support interactions allows for tailored support strategies and potentially personalized product or service offerings.

Recommender Systems: Providing relevant solutions or product suggestions within the support process can improve efficiency and customer self-service capabilities.

Data Preprocessing:

This crucial step involves cleaning and preparing the raw data for modeling.

The sample code demonstrates:

Loading the dataset using pandas.

Displaying basic information about the data (data types, non-null values).

Handling missing values by dropping rows containing any NaN values.

Encoding categorical (object) columns into numerical representations using LabelEncoder.

Exploratory Data Analysis (EDA):

While not explicitly shown in the provided code snippet, EDA is a vital step that typically precedes feature engineering and model building. It involves visualizing data distributions, identifying patterns, and understanding relationships between variables using libraries like matplotlib and seaborn. This helps in gaining insights into the data and informing subsequent steps.

Feature Engineering:

This involves selecting, transforming, and creating new features from the existing data that might improve the performance of the machine learning model. The sample code shows a basic step of defining the feature set (X) by dropping 'CustomerID' and the target variable ('Overall Satisfaction'), and defining the target variable (y). More advanced feature engineering could involve creating interaction terms, polynomial features, or extracting information from date/time columns.

Model Building:

This step involves selecting a suitable machine learning algorithm and training it on the prepared data. The sample code uses a RandomForestClassifier, a popular ensemble method known for its good performance on various classification tasks. The data is split into training and testing sets to evaluate the model's ability to generalize to unseen data.

Model Evaluation:

After training, the model's performance is evaluated on the test set using appropriate metrics. The sample code demonstrates the use of:

accuracy_score:

The proportion of correctly classified instances. classification_report: Provides precision, recall, F1-score, and support for each class. confusion_matrix:

A table that summarizes the model's predictions against the actual values, showing true positives, true negatives, false positives, and false negatives.

Visualization:

This step involves presenting the results and insights in a visual format for better understanding and communication. The sample code shows an example of visualizing feature importance from the trained Random Forest model, highlighting the top 10 features that contributed most to the predictions.

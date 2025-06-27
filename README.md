# from google.colab import files
uploaded = files.upload()
import pandas as pd
import io

if uploaded:
    filename = list(uploaded.keys())[0]  # Get the first uploaded filename
    print(f"Uploaded filename: {filename}")
    try:
        df = pd.read_csv(io.BytesIO(uploaded[filename]))
        print("\nDataset loaded successfully!")
        print(df.head())  # Display the first few rows
        print(df.info())  # Display dataset information
    except Exception as e:
        print(f"\nError loading the dataset: {e}")
else:
    print("\nNo file was uploaded.")
    # Assuming your preprocessed DataFrame is named 'df_cleaned'
print(df_cleaned.columns)
# Analyze customer support ticket trends
# Identify common issues
common_issues = df['Ticket Subject'].value_counts().head(10)
print("Top 10 Common Issues:")
print(common_issues)

# Plotting ticket trends over time
df['Date of Purchase'] = pd.to_datetime(df['Date of Purchase'])
df['YearMonth'] = df['Date of Purchase'].dt.to_period('M')
ticket_trends = df.groupby('YearMonth').size()
plt.figure(figsize=(10, 6))
ticket_trends.plot(kind='line', marker='o')
plt.title('Customer Support Ticket Trends Over Time')
plt.xlabel('Year-Month')
plt.ylabel('Number of Tickets')
plt.grid(True)
plt.xticks(rotation=45)
plt.tight_layout()
plt.show()
# Assuming your loaded DataFrame is named 'df'

# Define the target variable (Customer Satisfaction Rating)
y = df['Customer Satisfaction Rating']

# Define the features (X) - select the columns you want to use for prediction
# You'll need to choose these based on your understanding of the data and EDA.
# Here's an example using some potentially relevant columns:
features = ['Customer Age', 'Product Purchased', 'Ticket Type', 'Ticket Priority', 'Ticket Channel', 'Ticket Subject', 'Ticket Description']
X = df[features]

# If you've already done some preprocessing and your DataFrame is 'df_cleaned', use that instead:
# y = df_cleaned['Customer Satisfaction Rating']
# features = [...]
# X = df_cleaned[features]

print("Features (X) shape:", X.shape)
print("Target (y) shape:", y.shape)
# Assuming your loaded DataFrame is named 'df'

# Segment based on ticket types
ticket_type_segmentation = df.groupby('Ticket Type').size()
print("\nSegmentation based on Ticket Types:")
print(ticket_type_segmentation)

# Segment based on satisfaction levels
satisfaction_segmentation = df.groupby('Customer Satisfaction Rating').size()
print("\nSegmentation based on Customer Satisfaction Levels:")
print(satisfaction_segmentation)
import seaborn as sns
import matplotlib.pyplot as plt

# Assuming your loaded DataFrame is named 'df'

# Set up the plotting aesthetics
sns.set(style="whitegrid")

# Customer Satisfaction Distribution
plt.figure(figsize=(10, 6))
sns.histplot(df['Customer Satisfaction Rating'].dropna(), bins=5, kde=True, color='skyblue')
plt.title('Customer Satisfaction Distribution')
plt.xlabel('Satisfaction Rating')
plt.ylabel('Frequency')
plt.show()
import matplotlib.pyplot as plt
import seaborn as sns

# Assuming your loaded DataFrame is named 'df'

# Ticket Status Distribution
ticket_status_distribution = df['Ticket Status'].value_counts()
plt.figure(figsize=(8, 8))
plt.pie(ticket_status_distribution,
        labels=ticket_status_distribution.index,
        autopct='%1.1f%%',
        colors=sns.color_palette('pastel'),
        startangle=140)
plt.title('Ticket Status Distribution')
plt.axis('equal')
plt.show()
import matplotlib.pyplot as plt
import seaborn as sns

# Assuming your loaded DataFrame is named 'df'

# Customer Age Distribution
plt.figure(figsize=(10, 6))
sns.histplot(df['Customer Age'].dropna(), bins=20, kde=True, color='salmon')
plt.title('Customer Age Distribution')
plt.xlabel('Age')
plt.ylabel('Frequency')
plt.show()
import matplotlib.pyplot as plt
import seaborn as sns

# Assuming your loaded DataFrame is named 'df'

# Customer Gender Distribution
customer_gender_distribution = df['Customer Gender'].value_counts()
plt.figure(figsize=(8, 8))
plt.pie(customer_gender_distribution,
        labels=customer_gender_distribution.index,
        autopct='%1.1f%%',
        colors=sns.color_palette('Set2'),
        startangle=90)
plt.title('Customer Gender Distribution')
plt.axis('equal')
plt.show()
import matplotlib.pyplot as plt
import seaborn as sns

# Assuming your loaded DataFrame is named 'df'

# Ticket Channel Distribution
ticket_channel_distribution = df['Ticket Channel'].value_counts()
plt.figure(figsize=(10, 6))
sns.barplot(x=ticket_channel_distribution.index,
            y=ticket_channel_distribution,
            palette='rocket')
plt.title('Ticket Channel Distribution')
plt.xlabel('Ticket Channel')
plt.ylabel('Count')
plt.xticks(rotation=45, ha='right') # Added ha='right' for better label alignment
plt.tight_layout() # Added to prevent labels from overlapping
plt.show()
import matplotlib.pyplot as plt
import seaborn as sns

# Assuming your loaded DataFrame is named 'df'

# Chart 1: Average Customer Satisfaction by Gender (Bar Plot)
average_satisfaction = df.groupby('Customer Gender')['Customer Satisfaction Rating'].mean().reset_index()
plt.figure(figsize=(8, 6))
sns.barplot(x='Customer Gender', y='Customer Satisfaction Rating', data=average_satisfaction, palette='muted', order=['Male', 'Female', 'Other'])
plt.title('Average Customer Satisfaction by Gender')
plt.xlabel('Gender')
plt.ylabel('Average Satisfaction Rating')
plt.ylim(1, 5) # Adjust y-axis limit if needed
plt.show()
import matplotlib.pyplot as plt
import seaborn as sns

# Assuming your loaded DataFrame is named 'df'

# Product Purchased Distribution
plt.figure(figsize=(10, 6))
product_purchased_distribution = df['Product Purchased'].value_counts().head(10)
sns.barplot(y=product_purchased_distribution.index,
            x=product_purchased_distribution,
            palette='magma')
plt.title('Top 10 Products Purchased')
plt.xlabel('Count')
plt.ylabel('Product')
plt.tight_layout() # Added to prevent labels from overlapping
plt.show()
import matplotlib.pyplot as plt

# Assuming your loaded DataFrame is named 'df'

# Chart 2: Top Items Purchased by Gender (Horizontal Bar Chart)
plt.figure(figsize=(15, 6))

# Top Items Purchased by Males
plt.subplot(1, 3, 1)
top_items_male = df[df['Customer Gender'] == 'Male']['Product Purchased'].value_counts().head(5)
top_items_male.plot(kind='barh', color='skyblue')
plt.title('Top Items Purchased by Males')
plt.xlabel('Count')
plt.ylabel('Product')

# Top Items Purchased by Females
plt.subplot(1, 3, 2)
top_items_female = df[df['Customer Gender'] == 'Female']['Product Purchased'].value_counts().head(5)
top_items_female.plot(kind='barh', color='salmon')
plt.title('Top Items Purchased by Females')
plt.xlabel('Count')
plt.ylabel('Product')

# Top Items Purchased by Other Gender
plt.subplot(1, 3, 3)
top_items_other = df[df['Customer Gender'] == 'Other']['Product Purchased'].value_counts().head(5)
top_items_other.plot(kind='barh', color='lightgreen')
plt.title('Top Items Purchased by Other Genders')
plt.xlabel('Count')
plt.ylabel('Product')

plt.tight_layout()
plt.show()
import matplotlib.pyplot as plt

# Assuming your loaded DataFrame is named 'df'

# Count ticket types
ticket_type_distribution = df['Ticket Type'].value_counts()

# Plot
plt.figure(figsize=(8, 6))
ticket_type_distribution.plot(kind='pie', autopct='%1.1f%%',
                             colors=['skyblue', 'salmon', 'lightgreen'])
plt.title('Ticket Type Distribution')
plt.ylabel('')  # Remove the default 'Ticket Type' label on the y-axis
plt.show()
import matplotlib.pyplot as plt

# Assuming your loaded DataFrame is named 'df'

# Count ticket priorities
priority_distribution = df['Ticket Priority'].value_counts()

# Plot
plt.figure(figsize=(8, 6))
priority_distribution.plot(kind='pie', autopct='%1.1f%%',
                            colors=['lightblue', 'lightgreen', 'lightsalmon', 'skyblue'])
plt.title('Priority Level Distribution')
plt.ylabel('')  # Remove the default label on the y-axis
plt.show()
import pandas as pd
import matplotlib.pyplot as plt

# Assuming your loaded DataFrame is named 'df'

# Define age groups
bins = [0, 20, 30, 40, 50, 60, 70, 80, 90, 100]
labels = ['0-20', '21-30', '31-40', '41-50', '51-60', '61-70',
          '71-80', '81-90', '91-100']

# Categorize customers into age groups
df['Age Group'] = pd.cut(df['Customer Age'], bins=bins,
                        labels=labels, right=False)

# Calculate number of tickets raised by each age group
tickets_by_age_group = df.groupby('Age Group').size()

# Plot
plt.figure(figsize=(10, 6))
tickets_by_age_group.plot(kind='bar', color='skyblue')
plt.title('Tickets Raised by Age Group')
plt.xlabel('Age Group')
plt.ylabel('Number of Tickets Raised')
plt.xticks(rotation=45)
plt.grid(axis='y')
plt.show()
import numpy as np
import seaborn as sns
import matplotlib.pyplot as plt

# Assuming your loaded DataFrame is named 'df'

# Replace inf values with NaN (important for numerical stability)
df.replace([np.inf, -np.inf], np.nan, inplace=True)

# Create a facet grid for each ticket type
g = sns.FacetGrid(df, col='Ticket Type', col_wrap=3,
                  height=5, aspect=1.5)
g.map(sns.histplot, 'Customer Age', bins=20, kde=True)

# Set titles and labels
g.set_titles('{col_name}')
g.set_axis_labels('Age', 'Number of Tickets')

# Adjust layout
plt.subplots_adjust(top=0.9)
g.fig.suptitle('Distribution of Ticket Types by Age')

# Show plot
plt.show()

